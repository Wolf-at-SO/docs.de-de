---
title: Nachverfolgen von Ereignissen in der Ereignisablaufverfolgung in Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 5b2e43e169faade06d8816d9ae517b6957fbf1ee
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527095"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Nachverfolgen von Ereignissen in der Ereignisablaufverfolgung in Windows
In diesem Beispiel wird veranschaulicht, wie Windows Workflow Foundation (WF) für einen Workflowdienst nachverfolgung aktivieren und die Überwachungsereignisse in Event Tracing for Windows (ETW) ausgegeben wird. In dem Beispiel wird der ETW-Überwachungsteilnehmer (<xref:System.Activities.Tracking.EtwTrackingParticipant>) zur Ausgabe von Workflowüberwachungsdatensätzen in ETW verwendet.  
  
 Der Workflow in dem Beispiel erhält eine Anforderung, weist den Umkehrwert der Eingabedaten der Eingabevariablen zu und gibt den Umkehrwert an den Client zurück. Wenn die Eingabedaten 0 betragen, tritt eine nicht behandelte Ausnahme aufgrund einer Division durch 0 (null) auf, aufgrund der der Workflow abgebrochen wird. Wenn die Nachverfolgung aktiviert ist, wird der Fehlerdatensatz an ETW ausgegeben, sodass der Fehler später behoben werden kann. Der ETW-Überwachungsteilnehmer ist mit einem Überwachungsprofil konfiguriert, um Überwachungsdatensätze zu abonnieren. Das Überwachungsprofil ist in der Datei "Web.config" definiert und für den ETW-Überwachungsteilnehmer als Konfigurationsparameter bereitgestellt. Der ETW-Überwachungsteilnehmer ist in der Datei "Web.config" des Workflowdiensts konfiguriert und wird auf den Dienst als Dienstverhalten angewendet. In diesem Beispiel zeigen Sie die Überwachungsereignisse im Ereignisprotokoll mithilfe der Ereignisanzeige an.  
  
## <a name="workflow-tracking-details"></a>Workflowüberwachungsdetails  
 Windows Workflow Foundation stellt eine Überwachungsinfrastruktur, um die Ausführung einer Workflowinstanz nachzuverfolgen. Die Überwachungslaufzeit erstellt eine Workflowinstanz, um Ereignisse in Verbindung mit dem Workflowlebenszyklus, Ereignisse aus den Workflowaktivitäten sowie benutzerdefinierte Ereignissen auszugeben. In der folgenden Tabelle sind die primären Komponenten der Überwachungsinfrastruktur aufgeführt.  
  
|Komponente|Beschreibung|  
|---------------|-----------------|  
|Überwachungslaufzeit|Stellt die Infrastruktur bereit, um Überwachungsdatensätze auszugeben.|  
|Überwachungsteilnehmer|Greift auf die Nachverfolgungsdatensätze zu. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] wird mit einem Nachverfolgungsteilnehmer geliefert, der Nachverfolgungsdatensätze als Ereignisse der Ereignisablaufverfolgung für Windows (ETW) schreibt.|  
|Überwachungsprofil|Ein Filtermechanismus, der einem Überwachungsteilnehmer das Abonnieren einer Teilmenge der Überwachungsdatensätze ermöglicht, die von einer Workflowinstanz ausgegeben werden.|  
  
 In der folgenden Tabelle sind die Überwachungsdatensätze aufgeführt, die von der Workflowlaufzeit ausgegeben werden.  
  
|Überwachungsdatensatz|Beschreibung|  
|---------------------|-----------------|  
|Überwachungsdatensätze zur Workflowinstanz.|Beschreibt den Lebenszyklus der Workflowinstanz. Wenn der Workflow gestartet oder abgeschlossen wird, wird beispielsweise ein Instanzdatensatz ausgegeben.|  
|Überwachungsdatensätze zum Aktivitätszustand.|Führen Einzelheiten zur Aktivitätsausführung auf. Diese Datensätze geben den Zustand einer Workflowaktivität an, z. B. wenn eine Aktivität geplant oder abgeschlossen wird oder wenn ein Fehler ausgelöst wird.|  
|Datensatz zur Wiederaufnahme von Lesezeichen.|Wird immer dann ausgegeben, wenn ein Lesezeichen in einer Workflowinstanz wieder aufgenommen wird.|  
|Benutzerdefinierte Überwachungsdatensätze.|Ein Workflowautor kann benutzerdefinierte Überwachungsdatensätze erstellen und in einer benutzerdefinierten Aktivität ausgeben.|  
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Dieser Datensatz wird ausgegeben, wenn eine Aktivität eine andere Aktivität plant.|  
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Dieser Datensatz wird ausgegeben, wenn ein Fehler von einer Aktivität weitergegeben wird.|  
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Dieser Datensatz wird ausgegeben, wenn eine Aktivität von einer anderen Aktivität abgebrochen wird.|  
  
 Der Überwachungsteilnehmer abonniert eine Teilmenge der ausgegebenen Überwachungsdatensätze mithilfe von Überwachungsprofilen. Ein Überwachungsprofil enthält Überwachungsabfragen, die das Abonnieren eines bestimmten Typs von Überwachungsdatensätzen ermöglichen. Überwachungsprofile können im Code oder in der Konfiguration angegeben werden.  
  
#### <a name="to-use-this-sample"></a>So verwenden Sie dieses Beispiel  
  
1.  Öffnen Sie die Projektmappendatei "EtwTrackingParticipantSample.sln" in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Drücken Sie STRG+UMSCHALT+B, um die Projektmappe zu erstellen.  
  
3.  Drücken Sie F5, um die Projektmappe auszuführen.  
  
     Der Dienst lauscht standardmäßig an Port 53797 (http://localhost:53797/SampleWorkflowService.xamlx).  
  
4.  Öffnen Sie den WCF-Testclient mit [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)].  
  
     WCF-Testclient (WcfTestClient.exe) befindet sich in der \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] -Installationsordner > \Common7\IDE\-Ordner.  
  
     Der standardmäßige [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]-Installationsordner ist "C:\Programme\Microsoft-Visual Studio 10.0".  
  
5.  Wählen Sie im WCF-Testclient **Dienst hinzufügen** aus der **Datei** Menü.  
  
     Fügen Sie die Endpunktadresse im Eingabefeld hinzu. Die Standardeinstellung ist http://localhost:53797/SampleWorkflowService.xamlx.  
  
6.  Öffnen Sie die Ereignisanzeige.  
  
     Starten Sie vor dem Aufrufen des Diensts die Ereignisanzeige über den **starten** , wählen Sie im Menü **ausführen** und geben Sie im `eventvwr.exe`. Stellen Sie sicher, dass das Ereignisprotokoll eine Überwachung für vom Workflowdienst ausgegebene Überwachungsereignisse ausführt.  
  
7.  In der Strukturansicht der Ereignisanzeige, navigieren Sie zu **Ereignisanzeige**, **Anwendungs- und Dienstprotokolle**, und **Microsoft**. Mit der rechten Maustaste **Microsoft** , und wählen Sie **Ansicht** und dann **analytische und Debugprotokolle** , aktivieren Sie die analytischen und Debugprotokolle  
  
     Sicherstellen, dass die **analytische und Debugprotokolle** Option aktiviert ist.  
  
8.  In der Strukturansicht in der Ereignisanzeige, navigieren Sie zu **Ereignisanzeige**, **Anwendungs- und Dienstprotokolle**, **Microsoft**, **Windows**,  **Anwendungsserver-Anwendungen**. Mit der rechten Maustaste **analytisch** , und wählen Sie **Protokoll aktivieren** zum Aktivieren der **analytisch** Protokoll.  
  
9. Testen Sie den Dienst mithilfe des WCF-Testclients, indem Sie auf `GetData` doppelklicken.  
  
     Dadurch wird die `GetData`-Methode geöffnet. Die Anforderung akzeptiert einen Parameter und stellt sicher, dass der Wert 0 beträgt, was dem Standard entspricht.  
  
     Klicken Sie auf **Aufrufen**.  
  
10. Achten Sie auf die vom Workflow ausgegebenen Ereignisse.  
  
     Wechseln Sie zurück zur Ereignisanzeige, und navigieren Sie zu **Ereignisanzeige**, **Anwendungs- und Dienstprotokolle**, **Microsoft**, **Windows**,  **Anwendungsserver-Anwendungen**. Mit der rechten Maustaste **analytisch** , und wählen Sie **aktualisieren**.  
  
     Die Workflowereignisse werden in der Ereignisanzeige angezeigt. Beachten Sie, dass Workflowausführungsereignisse angezeigt werden und dass es sich bei einem dieser Ereignisse um eine unbehandelte Ausnahme handelt, die dem Fehler im Workflow entspricht. Es wird auch ein Warnungsereignis von der Workflowaktivität ausgegeben, das angibt, dass die Aktivität einen Fehler auslöst.  
  
11. Wiederholen Sie Schritt 9 und 10, und geben Sie andere Daten als 0 ein, damit kein Fehler ausgelöst wird.  
  
 Mithilfe von Nachverfolgungsprofilen können Sie Ereignisse abonnieren, die von der Laufzeit ausgegeben werden, wenn sich der Zustand eines Workflowinstanz ändert. In Abhängigkeit von Ihren Überwachungsanforderungen können Sie ein Profil erstellen, das sehr grob gehalten ist und einen kleinen Satz von unspezifischen Zustandsänderungen eines Workflows abonniert. Sie können jedoch auch ein sehr präzises Profil erstellen, dessen Ausgabe so umfangreich ist, dass später die Ausführung rekonstruiert werden kann. In dem Beispiel sind die Ereignisse veranschaulicht, die mithilfe des `HealthMonitoring Tracking Profile`, das eine geringe Menge von Ereignissen ausgibt, von der Workflowlaufzeit an ETW ausgegeben werden. Ein anderes Profil, das weitere Workflownachverfolgungsereignisse ausgibt, wird auch in der Datei "Web.config" mit dem Namen `Troubleshooting Tracking Profile` bereitgestellt. Wenn [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] installiert ist, wird ein Standardprofil mit einem leeren Namen in der Datei "Machine.config" konfiguriert. Dieses Profil wird von der ETW-Überwachungsverhaltenskonfiguration verwendet, wenn kein Profilname oder ein leerer Profilname angegeben wird.  
  
 Das Nachverfolgungsprofil für die Systemüberwachung gibt Workflowinstanzdatensätze und Aktivitätsdatensätze für die Fehlerweitergabe aus. Dieses Profil wird erstellt, indem einer Web.config-Konfigurationsdatei das folgende Nachverfolgungsprofil hinzugefügt wird.  
  
```xml  
<<tracking>  
      <profiles>  
        <trackingProfile name="HealthMonitoring Tracking Profile">  
          <workflow activityDefinitionId="*">  
            <workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="Started"/>  
                  <state name="Completed"/>  
                  <state name="Aborted"/>  
                  <state name="UnhandledException"/>  
                </states>  
            </workflowInstanceQuery>  
           </workflowInstanceQueries>  
            <faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
            </faultPropagationQueries>  
          </workflow>  
        </trackingProfile>  
       </profiles>  
</tracking>  
```  
  
 Das Profil kann geändert werden, indem die `EtwTrackingParticipant`-Konfiguration folgendermaßen geändert wird.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
#### <a name="to-clean-up-optional"></a>So führen Sie eine Bereinigung aus (optional)  
  
1.  Öffnen Sie die Ereignisanzeige.  
  
2.  Navigieren Sie zu **Ereignisanzeige**, **Anwendungs- und Dienstprotokolle**, **Microsoft**, **Windows**, **Anwendung Server-Anwendungen**. Mit der rechten Maustaste **analytisch** , und wählen Sie **Protokoll deaktivieren**.  
  
3.  Navigieren Sie zu **Ereignisanzeige**, **Anwendungs- und Dienstprotokolle**, **Microsoft**, **Windows**, **Anwendung Server-Anwendungen**. Mit der rechten Maustaste **analytisch** , und wählen Sie **Protokoll löschen**.  
  
4.  Wählen Sie die **löschen** Option aus, um die Ereignisse zu löschen.  
  
## <a name="known-issue"></a>Bekanntes Problem  
  
> [!NOTE]
>  Es gibt ein bekanntes Problem in der Ereignisanzeige, bei dem bei der Decodierung von ETW-Ereignissen ein Fehler auftritt. Möglicherweise wird eine Fehlermeldung ähnlich der Folgenden angezeigt.  
>   
>  Die Beschreibung für Ereigniskennung \<Id > aus der Quelle Microsoft Windows-Anwendungsserver-Anwendungen wurde nicht gefunden. Entweder ist die Komponente, die dieses Ereignis auslöst, nicht auf dem lokalen Computer installiert, oder die Installation ist beschädigt. Sie können die Komponente auf dem lokalen Computer installieren oder reparieren.  
>   
>  Wenn dieser Fehler auftritt, klicken Sie im Aktionsbereich auf "Aktualisieren". Das Ereignis sollte jetzt ordnungsgemäß decodiert werden.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, fahren Sie mit [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF) Samples für .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) alle Windows Communication Foundation (WCF) herunterladen und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Beispiele. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a>Siehe auch  
 [AppFabric-Überwachungsbeispiele](https://go.microsoft.com/fwlink/?LinkId=193959)
