---
title: X.509-Zertifikats-Validierungssteuerelement
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: e54f79046113e5f1a1a1cc065606fd5b706b49ac
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272526"
---
# <a name="x509-certificate-validator"></a>X.509-Zertifikats-Validierungssteuerelement
In diesem Beispiel wird veranschaulicht, wie ein benutzerdefiniertes X.509-Zertifikats-Validierungssteuerelement implementiert wird. Dies ist nützlich, wenn keines der integrierten X.509-Zertifikats-Validierungsmodi den Anforderungen der Anwendung entspricht. Dieses Beispiel zeigt einen Dienst, der über ein benutzerdefiniertes Validierungssteuerelement verfügt, das selbst herausgegebene Zertifikate akzeptiert. Der Client verwendet solch ein Zertifikat, um den Dienst zu authentifizieren.  
  
 Hinweis: Da jeder ein selbst herausgegebenes Zertifikat erstellen kann, ist das vom Dienst verwendete benutzerdefinierte Validierungssteuerelement unsicherer als das Standardverhalten vom ChainTrust X509CertificateValidationMode. Die daraus resultierenden Sicherheitsauswirkungen sollten sorgfältig bedacht werden, bevor diese Validierungslogik im Produktionscode verwendet wird.  
  
 Insgesamt zeigt dieses Beispiel Folgendes:  
  
-   Der Client kann mit einem X.509-Zertifikat authentifiziert werden.  
  
-   Der Server überprüft die Clientanmeldeinformationen mithilfe eines benutzerdefinierten X509CertificateValidator.  
  
-   Der Server wird mit dem X.509-Zertifikat des Servers authentifiziert.  
  
 Der Dienst macht einen einzelnen Endpunkt zur Kommunikation mit dem Dienst verfügbar, der mit der Konfigurationsdatei "App.conf" definiert wird. Der Endpunkt besteht aus einer Adresse, einer Bindung und einem Vertrag. Die Bindung konfiguriert ist, mit einer normalen `wsHttpBinding` , die standardmäßig `WSSecurity` und Clientzertifikatauthentifizierung verwendet. Das Dienstverhalten gibt den benutzerdefinierten Modus zur Prüfung von X.509-Clientzertifikaten zusammen mit dem Typ der Validierungssteuerelementklasse an. Das Verhalten gibt auch das Serverzertifikat mit dem serviceCertificate-Element an. Das Serverzertifikat muss für den gleichen Wert enthalten die `SubjectName` als die `findValue` in die [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).  
  
```xml  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use host/baseAddresses to configure base address -->  
        <!-- provided by host -->  
        <host>  
          <baseAddresses>  
            <add baseAddress =  
                "http://localhost:8001/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address specified above, provide one endpoint -->  
        <endpoint address="certificate"  
               binding="wsHttpBinding"  
               bindingConfiguration="Binding"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <!-- X509 certificate binding -->  
        <binding name="Binding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults ="true"/>  
          <serviceCredentials>  
            <!--The serviceCredentials behavior allows one -->  
            <!-- to specify authentication constraints on -->  
            <!-- client certificates. -->  
            <clientCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- Custom means that if the custom -->  
              <!-- X509CertificateValidator does NOT throw -->  
              <!-- an exception, then the provided certificate -- >  
              <!-- will be trusted without performing any -->  
              <!-- validation beyond that performed by the custom-->  
              <!-- validator. The security implications of this -->  
              <!-- setting should be carefully considered before -->  
              <!-- using Custom in production code. -->  
              <authentication   
                 certificateValidationMode="Custom"   
                 customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />  
            </clientCertificate>  
            <!-- The serviceCredentials behavior allows one to -- >  
            <!--define a service certificate. -->  
            <!--A service certificate is used by a client to  -->  
            <!--authenticate the service and provide message  -->  
            <!--protection. This configuration references the  -->  
            <!--"localhost" certificate installed during the setup  -->  
            <!--instructions. -->  
            <serviceCertificate findValue="localhost"   
                 storeLocation="LocalMachine"   
                 storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
      </system.serviceModel>  
```  
  
 Die Clientendpunktkonfiguration besteht aus einem Konfigurationsnamen, einer absoluten Adresse für den Dienstendpunkt, der Bindung und dem Vertrag. Die Clientbindung wird mit dem entsprechenden Modus und der `clientCredentialType`-Nachricht konfiguriert.  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- X509 certificate based endpoint -->  
      <endpoint name="Certificate"  
        address=  
        "http://localhost:8001/servicemodelsamples/service/certificate"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
    <bindings>  
        <wsHttpBinding>  
            <!-- X509 certificate binding -->  
            <binding name="Binding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
               </security>  
            </binding>  
       </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- PeerOrChainTrust means that if the certificate -->  
              <!-- is in the user's Trusted People store, then it -->  
              <!-- is trusted without performing a validation of -->  
              <!-- the certificate's issuer chain. -->  
              <!-- This setting is used here for convenience so -->  
              <!-- that the sample can be run without having to -->  
              <!-- have certificates issued by a certification -->  
              <!-- authority (CA). This setting is less secure -->  
              <!-- than the default, ChainTrust. The security -->  
              <!-- implications of this setting should be -->  
              <!-- carefully considered before using -->  
              <!-- PeerOrChainTrust in production code.-->  
              <authentication   
                  certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 Die Clientimplementierung legt das zu verwendende Clientzertifikat fest.  
  
```csharp
// Create a client with Certificate endpoint configuration  
CalculatorClient client = new CalculatorClient("Certificate");  
try  
{  
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");  
  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    client.Close();  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine("Call timed out : {0}", e.Message);  
    client.Abort();  
}  
catch (CommunicationException e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
```  
  
 In diesem Beispiel wird ein benutzerdefinierter X509CertificateValidator verwendet, um Zertifikate zu überprüfen. Das Beispiel implementiert CustomX509CertificateValidator, das von <xref:System.IdentityModel.Selectors.X509CertificateValidator> abgeleitet ist. Weitere Informationen finden Sie in der Dokumentation zu <xref:System.IdentityModel.Selectors.X509CertificateValidator>. In diesem speziellen Beispiel zu einem benutzerdefinierten Validierungssteuerelement ist die Validate-Methode so implementiert, dass sie jedes selbst herausgegebene X.509-Zertifikat akzeptiert, wie im folgenden Code gezeigt.  
  
```csharp
public class CustomX509CertificateValidator : X509CertificateValidator  
{  
  public override void Validate ( X509Certificate2 certificate )  
  {  
   // Only accept self-issued certificates  
   if (certificate.Subject != certificate.Issuer)  
     throw new Exception("Certificate is not self-issued");  
   }  
}  
```  
  
 Nachdem das Validierungssteuerelement im Dienstcode implementiert ist, muss der Diensthost über die zu verwendende Validierungssteuerelementinstanz informiert werden. Dies wird mit dem folgenden Code durchgeführt.  
  
```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 Sie können dasselbe aber auch wie folgt in der Konfiguration vornehmen.  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
     <behavior name="CalculatorServiceBehavior">  
       ...  
   <serviceCredentials>  
    <!--The serviceCredentials behavior allows one to specify -->   
    <!--authentication constraints on client certificates.-->  
    <clientCertificate>  
    <!-- Setting the certificateValidationMode to Custom means -->   
    <!--that if the custom X509CertificateValidator does NOT -->   
    <!--throw an exception, then the provided certificate will-- >   
    <!-- be trusted without performing any validation beyond that-- >  
    <!-- performed by the custom validator. The security -- >   
    <!--implications of this setting should be carefully -- >  
    <!--considered before using Custom in production code. -->  
    <authentication certificateValidationMode="Custom"  
       customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />  
   </clientCertificate>  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 Wenn Sie das Beispiel ausführen, werden die Anforderungen und Antworten für den Vorgang im Clientkonsolenfenster angezeigt. Der Client sollte alle Methoden erfolgreich aufrufen. Drücken Sie im Clientfenster die EINGABETASTE, um den Client zu schließen.  
  
## <a name="setup-batch-file"></a>Setupbatchdatei  
 Mit der in diesem Beispiel enthaltenen Batchdatei Setup.bat können Sie den Server mit relevanten Zertifikaten zum Ausführen einer selbst gehosteten Anwendung konfigurieren, die serverzertifikatbasierte Sicherheit erfordert. Diese Batchdatei muss angepasst werden, wenn sie computerübergreifend oder in einem nicht gehosteten Szenario verwendet werden soll.  
  
 Nachfolgend erhalten Sie einen kurzen Überblick über die verschiedenen Abschnitte der Batchdateien, damit Sie sie so ändern können, dass sie in der entsprechenden Konfiguration ausgeführt werden:  
  
-   Erstellen des Serverzertifikats  
  
     Mit den folgenden Zeilen aus der Batchdatei "Setup.bat" wird das zu verwendende Serverzertifikat erstellt. Die Variable %SERVER_NAME% gibt den Servernamen an. Ändern Sie diese Variable, und geben Sie Ihren eigenen Servernamen an. Der Standardwert ist localhost.  
  
    ```bash  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Installieren des Serverzertifikats in den Clientspeicher für vertrauenswürdige Zertifikate:  
  
     Mit den folgenden Zeilen in der Batchdatei Setup.bat wird das Serverzertifikat in den Clientspeicher für vertrauenswürdige Personen kopiert. Dieser Schritt ist erforderlich, da von Makecert.exe generierten Zertifikaten nicht implizit vom Clientsystem vertraut wird. Wenn Sie bereits über ein Zertifikat verfügen, dass von einem vertrauenswürdigen Clientstammzertifikat abstammt (z. B. ein von Microsoft ausgegebenes Zertifikat), ist dieser Schritt zum Auffüllen des Clientzertifikatspeichers mit dem Serverzertifikat nicht erforderlich.  
  
    ```bash  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Erstellen des Clientzertifikats  
  
     Die folgenden Zeilen aus der Batchdatei Setup.bat erstellen das zu verwendende Clientzertifikat. Die Variable % USER_NAME% gibt den Clientnamen an. Dieser Wert wird auf "test1" festgelegt, da dies der Name ist, nach dem der Clientcode sucht. Wenn Sie den Wert von %USER_NAME% ändern, müssen Sie auch den zugehörigen Wert in der Client.cs-Quelldatei ändern und den Client neu erstellen.  
  
     Das Zertifikat wird im persönlichen Speicher unterhalb von CurrentUser gespeichert.  
  
    ```bash  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   Installieren des Clientzertifikats in den Serverspeicher für vertrauenswürdige Zertifikate:  
  
     Die folgenden Zeilen in der Batchdatei Setup.bat kopieren das Clientzertifikat in den Speicher für vertrauenswürdige Personen. Dieser Schritt ist erforderlich, da von "Makecert.exe" generierten Zertifikaten nicht implizit vom Serversystem vertraut wird. Wenn Sie bereits über ein Zertifikat verfügen, das von einem vertrauenswürdigen Stammzertifikat abstammt (z. B. ein von Microsoft ausgegebenes Zertifikat), ist dieser Schritt zum Auffüllen des Serverzertifikatspeichers mit dem Clientzertifikat nicht erforderlich.  
  
    ```bash  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>So richten Sie das Beispiel ein und erstellen es  
  
1.  Um die Projektmappe zu erstellen, folgen Sie den Anweisungen im [Erstellen der Windows Communication Foundation-Beispiele](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Um das Beispiel in einer Konfiguration mit einem einzigen Computer oder computerübergreifend auszuführen, befolgen Sie die folgenden Anweisungen.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>So führen Sie das Beispiel auf demselben Computer aus  
  
1.  Öffnen Sie eine [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]-Eingabeaufforderung mit Administratorrechten, und führen Sie Setup.bat aus dem Beispielinstallationsordner aus. Hiermit werden alle Zertifikate installiert, die zum Ausführen des Beispiels erforderlich sind.  
  
    > [!IMPORTANT]
    >  Die Batchdatei Setup.bat ist darauf ausgelegt, an einer [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]-Eingabeaufforderung ausgeführt zu werden. Die innerhalb der [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]-Eingabeaufforderung festgelegte PATH-Umgebungsvariable zeigt auf das Verzeichnis mit den ausführbaren Dateien, die für das Skript Setup.bat erforderlich sind.  
  
2.  Starten Sie Service.exe aus dem Ordner \service\bin.  
  
3.  Starten Sie Client.exe aus dem Ordner \client\bin. In der Clientkonsolenanwendung wird Clientaktivität angezeigt.  
  
4.  Wenn der Client und Dienst nicht kommunizieren können, finden Sie unter [Tipps zur Problembehandlung](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>So führen Sie das Beispiel computerübergreifend aus  
  
1.  Erstellen Sie auf dem Dienstcomputer ein Verzeichnis.  
  
2.  Kopieren Sie die Dienstprogrammdateien aus \service\bin in das virtuelle Verzeichnis auf dem Dienstcomputer. Kopieren Sie außerdem die Dateien Setup.bat, Cleanup.bat, GetComputerName.vbs und ImportClientCert.bat auf den Dienstcomputer.  
  
3.  Erstellen Sie auf dem Clientcomputer ein Verzeichnis für die Clientbinärdateien.  
  
4.  Kopieren Sie die Clientprogrammdateien in das Clientverzeichnis auf dem Clientcomputer. Kopieren Sie die Dateien Setup.bat, Cleanup.bat und ImportServiceCert.bat ebenfalls auf den Client.  
  
5.  Führen Sie auf dem Server `setup.bat service` an einer Visual Studio-Eingabeaufforderung mit Administratorrechten aus. Ausführung `setup.bat` mit der `service` Argument erstellt ein Dienstzertifikat mit dem vollqualifizierten Domänennamen des Computers erstellt und Exporte das Dienstzertifikat in eine Datei "Service.cer" exportiert.  
  
6.  Bearbeiten Sie Service.exe.config so, dass Sie den neuen Zertifikatnamen (im der `findValue` -Attribut in der [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) die ist identisch mit den vollständig qualifizierten Domänennamen des Computers. Ändern Sie auch den Computernamen in die \<Service > /\<BaseAddresses >-Element von "localhost" den vollqualifizierten Namen Ihres dienstcomputers.  
  
7.  Kopieren Sie die Datei Service.cer aus dem Dienstverzeichnis in das Clientverzeichnis auf dem Clientcomputer.  
  
8.  Führen Sie auf dem Client `setup.bat client` an einer Visual Studio-Eingabeaufforderung mit Administratorrechten aus. Durch Ausführen von `setup.bat` mit dem Argument `client` wird ein Clientzertifikat mit dem Namen client.com erstellt und in die Datei Client.cer exportiert.  
  
9. Ändern Sie in der Datei Client.exe.config auf dem Clientcomputer den Wert für die Adresse des Endpunkts, sodass er mit der neuen Adresse Ihres Diensts übereinstimmt. Ersetzen Sie dazu localhost durch den vollqualifizierten Domänennamen des Servers.  
  
10. Kopieren Sie die Datei Client.cer aus dem Clientverzeichnis in das Dienstverzeichnis auf dem Server.  
  
11. Führen Sie auf dem Client ImportServiceCert.bat an einer Visual Studio-Eingabeaufforderung mit Administratorrechten aus. Dadurch wird das Dienstzertifikat aus der Datei Service.cer in den Speicher CurrentUser – TrustedPeople importiert.  
  
12. Führen Sie auf dem Server ImportClientCert.bat an einer Visual Studio-Eingabeaufforderung mit Administratorrechten aus. Dadurch wird das Clientzertifikat aus der Datei Client.cer in den Speicher LocalMachine – TrustedPeople importiert.  
  
13. Starten Sie auf dem Servercomputer Service.exe in einem Eingabeaufforderungsfenster.  
  
14. Starten Sie auf dem Clientcomputer Client.exe in einem Eingabeaufforderungsfenster. Wenn der Client und Dienst nicht kommunizieren können, finden Sie unter [Tipps zur Problembehandlung](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>So stellen Sie den Zustand vor Ausführung des Beispiels wieder her  
  
1.  Führen Sie Cleanup.bat im Beispielordner aus, nachdem Sie das Beispiel fertig ausgeführt haben. Dadurch werden die Server- und Clientzertifikate aus dem Zertifikatspeicher entfernt.  
  
> [!NOTE]
>  Wenn dieses Beispiel computerübergreifend ausgeführt wird, entfernt dieses Skript keine Dienstzertifikate auf einem Client. Wenn Sie Windows Communication Foundation (WCF)-Beispiele, die Zertifikate computerübergreifend verwenden ausgeführt haben, achten Sie darauf, dass Sie die Dienstzertifikate entfernen, die in den Speicher CurrentUser – trustedpeople installiert wurden. Verwenden Sie dazu den folgenden Befehl: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Beispiel: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Siehe auch
