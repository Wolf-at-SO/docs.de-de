---
title: ASP.NET-Zwischenspeicherungsintegration
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 55e6213bf0c4c212ebcf4e68882d16532c0e4229
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271183"
---
# <a name="aspnet-caching-integration"></a>ASP.NET-Zwischenspeicherungsintegration
In diesem Beispiel wird gezeigt, wie der ASP.NET-Ausgabecache mit dem WCF-WEB HTTP-Programmiermodell verwendet wird. Informieren Sie sich die [grundlegenden Ressourcendiensts](../../../../docs/framework/wcf/samples/basic-resource-service.md) Beispiel eine selbst gehostete Version dieses Szenarios, die die dienstimplementierung eingehend erläutert wird. Dieses Thema befasst sich mit den Integrationsfunktion des ASP.NET-Ausgabecaches.  
  
## <a name="demonstrates"></a>Veranschaulicht  
 Integration in den ASP.NET-Ausgabecache  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, fahren Sie mit [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF) Samples für .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) alle Windows Communication Foundation (WCF) herunterladen und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Beispiele. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>Diskussion  
 Das Beispiel verwendet die <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ASP.NET nutzen die ausgabezwischenspeicherung mit den Windows Communication Foundation (WCF)-Dienst. Das <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> wird auf Dienstvorgänge angewendet und gibt den Namen eines Cacheprofils in einer Konfigurationsdatei an, die auf Antworten vom angegebenen Vorgang angewendet werden soll.  
  
 In der Datei "Service.cs" beispieldienstprojekt sowohl die `GetCustomer` und `GetCustomers` Vorgänge mit markiert sind, die <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, dem bietet es sich um des cacheprofilnamen "CacheFor60Seconds". In der Datei "Web.config" des Dienstprojekts wird das Cacheprofil "CacheFor60Seconds" bereitgestellt, unter der <`caching`>-Element von <`system.web`>. Für dieses Cacheprofil wird der Wert des der `duration` -Attribut ist "60", damit dieses Profil zugeordnete Antworten 60 Sekunden lang im ASP.NET-Ausgabecache zwischengespeichert werden. Für dieses Cacheprofil wird die `varmByParam` -Attribut festgelegt ist, um Anforderungen mit unterschiedlichen Werten für "formatieren" der `format` -Abfragezeichenfolgenparameter die Antworten getrennt zwischengespeichert. Und schließlich des Cacheprofils des `varyByHeader` -Attribut auf "Akzeptieren", festgelegt ist, sodass Anforderungen mit anderen Accept-Headerwerte die Antworten getrennt zwischengespeichert.  
  
 Program.cs im Clientprojekt zeigt, wie ein Client dieser Art mit <xref:System.Net.HttpWebRequest> erstellt werden kann. Beachten Sie, dass dies nur eine Möglichkeit für den Zugriff auf einen WCF-Dienst darstellt. Es ist auch möglich, die Zugriff auf den Dienst mit anderen .NET Framework-Klassen wie die WCF-Kanalfactory und <xref:System.Net.WebClient>. In anderen Beispielen im SDK (z. B. die [grundlegenden HTTP-Dienst](../../../../docs/framework/wcf/samples/basic-http-service.md) Beispiel und die [automatische Formatauswahl](../../../../docs/framework/wcf/samples/automatic-format-selection.md) Beispiel) veranschaulichen, wie Sie diese Klassen verwenden, um die Kommunikation mit einem WCF-Dienst.  
  
## <a name="to-run-the-sample"></a>So führen Sie das Beispiel aus  
 Das Beispiel umfasst drei Projekte:  
  
-   **Dienst**: ein Webanwendungsprojekt, die einen WCF-HTTP-Dienst, gehostet in ASP.NET enthält.  
  
-   **Client**: ein Konsolenanwendungsprojekt, das Aufrufe an den Dienst ausführt.  
  
-   **Allgemeine**: eine freigegebene Bibliothek, die die vom Client und Dienst verwendeten Kundentyp enthält.  
  
 Während die Clientkonsolenanwendung ausgeführt wird, sendet der Client Anforderungen an den Dienst und schreibt die in den Antworten enthaltenen wichtigen Informationen in das Konsolenfenster.  
  
#### <a name="to-run-the-sample"></a>So führen Sie das Beispiel aus  
  
1.  Öffnen Sie die Projektmappe für das Beispiel der Integration von ASP.NET-Zwischenspeicherung.  
  
2.  Drücken Sie STRG+UMSCHALT+B, um die Projektmappe zu erstellen.  
  
3.  Wenn die **Projektmappen-Explorer** nicht bereits geöffnet ist, drücken Sie STRG + W + s.  
  
4.  Von der **Projektmappen-Explorer** rechts klicken die **Service** Projekt, und wählen **neue Instanz starten**. Der ASP.NET-Entwicklungsserver, der den Dienst hostet, wird gestartet.  
  
5.  Von der **Projektmappen-Explorer** rechts klicken die **Client** Projekt, und wählen **neue Instanz starten**.  
  
6.  Im eingeblendeten Clientkonsolenfenster werden der URI des ausgeführten Diensts und der URI der HTML-Hilfeseite für den ausgeführten Dienst angezeigt. Sie können die HTML-Hilfeseite jederzeit anzeigen, indem sie den URI der Hilfeseite in einem Browser eingeben.  
  
7.  Während das Beispiel ausgeführt wird, schreibt der Client den Status der aktuellen Aktivität.  
  
8.  Drücken Sie eine beliebige Taste, um die Clientkonsolenanwendung zu beenden.  
  
9. Drücken Sie UMSCHALT+F5, um das Debugging des Diensts zu beenden.  
  
10. In den Windows-Benachrichtigungsbereich, klicken Sie mit der rechten Maustaste auf das Symbol für das ASP.NET Development Server aus, und wählen Sie **beenden**.
