---
title: Einfaches Beispiel
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 8c99b4955dcc00015d54391dcb509b312190ddab
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508708"
---
# <a name="basic-sample"></a>Einfaches Beispiel
In diesem Beispiel wird erläutert, wie ein Dienst sichtbar gemacht wird und wie nach einem sichtbaren Dienst gesucht und dieser aufgerufen wird. Dieses Beispiel besteht aus zwei Projekten: Dienst und Client.  
  
> [!NOTE]
>  In diesem Beispiel wird die Suche in Code implementiert.  Ein Beispiel, das in der Konfiguration Suche implementiert, finden Sie unter [Konfiguration](../../../../docs/framework/wcf/samples/configuration-sample.md).  
  
## <a name="service"></a>Dienst  
 Dies ist eine einfache Rechnerdienstimplementierung. Der mit der Suche verbundene Code befindet sich in `Main`. Dort wird dem Diensthost ein <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hinzugefügt, und es wird wie im folgenden Code dargestellt ein <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> hinzugefügt.  
  
```  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new   
      WSHttpBinding(), String.Empty);  
  
    // Make the service discoverable over UDP multicast  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>Client  
 Der Client verwendet einen <xref:System.ServiceModel.Discovery.DynamicEndpoint>, um den Dienst zu ermitteln. Der <xref:System.ServiceModel.Discovery.DynamicEndpoint>, ein Standardendpunkt, löst den Endpunkt des Diensts auf, wenn der Client geöffnet wird. In diesem Fall sucht der <xref:System.ServiceModel.Discovery.DynamicEndpoint> auf Grundlage des Dienstvertrags nach dem Dienst. Der <xref:System.ServiceModel.Discovery.DynamicEndpoint> führt die Suche standardmäßig über einen <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> durch. Sobald ein Dienstendpunkt gefunden wurde, stellt der Client über die angegebene Bindung eine Verbindung mit dem Dienst her.  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 Der Client definiert eine Methode namens `InvokeCalculatorService`, die mithilfe der <xref:System.ServiceModel.Discovery.DiscoveryClient>-Klasse nach verfügbaren Diensten sucht. Der <xref:System.ServiceModel.Discovery.DynamicEndpoint> erbt vom <xref:System.ServiceModel.Description.ServiceEndpoint>. Deshalb kann er an die `InvokeCalculatorService`-Methode übergeben werden. Im Beispiel wird dann mithilfe des <xref:System.ServiceModel.Discovery.DynamicEndpoint> eine Instanz des `CalculatorServiceClient` erstellt und die verschiedenen Vorgänge des Rechnerdiensts aufgerufen.  
  
```csharp  
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)  
{  
   // Create a client  
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);  
  
   Console.WriteLine("Invoking CalculatorService");  
   Console.WriteLine();  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Subtract service operation.  
   result = client.Subtract(value1, value2);  
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Multiply service operation.  
   result = client.Multiply(value1, value2);  
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Divide service operation.  
   result = client.Divide(value1, value2);  
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
   Console.WriteLine();  
  
   //Closing the client gracefully closes the connection and cleans up resources  
   client.Close();  
}  
```  
  
#### <a name="to-use-this-sample"></a>So verwenden Sie dieses Beispiel  
  
1.  In diesem Beispiel werden HTTP-Endpunkte verwendet. Zur Ausführung des Beispiels müssen die richtigen URL-ACLs hinzugefügt werden. Weitere Informationen finden Sie unter [Konfigurieren von HTTP und HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353). Durch die Ausführung des folgenden Befehls mit erweiterten Berechtigungen werden die entsprechenden ACLs hinzugefügt. Es empfiehlt sich, die Domäne und den Benutzernamen durch die folgenden Argumente zu ersetzen, wenn der Befehl nicht funktioniert. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Öffnen Sie Basic.sln mit [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], und erstellen Sie das Beispiel.  
  
3.  Führen Sie die SERVICE.EXE-Anwendung aus.  
  
4.  Führen Sie nach dem Starten des Diensts client.exe aus.  
  
5.  Beachten Sie, dass der Client den Dienst ermitteln konnte, ohne seine Adresse zu kennen.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, fahren Sie mit [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF) Samples für .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) alle Windows Communication Foundation (WCF) herunterladen und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Beispiele. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a>Siehe auch
