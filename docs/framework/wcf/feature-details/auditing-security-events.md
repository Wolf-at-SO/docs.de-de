---
title: Überwachen von Sicherheitsereignissen
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bad963db8d0e3644204824645f702c7b7b84963d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864241"
---
# <a name="auditing-security-events"></a>Überwachen von Sicherheitsereignissen
Anwendungen, die mit Windows Communication Foundation (WCF) erstellt, können mit der Überwachungsfunktion Sicherheitsereignisse (Erfolg, Fehler, oder beides) protokollieren. Die Ereignisse werden in das Ereignisprotokoll von Windows geschrieben und können in der Ereignisanzeige untersucht werden.  
  
 Mithilfe der Überwachung können Administratoren bereits stattgefundene oder gerade laufende Angriffe erkennen. Darüber hinaus können Entwickler mittels Überwachung sicherheitsrelevante Probleme debuggen. Falls beispielsweise berechtigten Benutzern versehentlich aufgrund eines Fehlers in der Konfiguration der Autorisierung oder Überprüfungsrichtlinie der Zugriff verweigert wird, kann die Ursache für diesen Fehler schnell durch Überprüfung des Ereignisprotokolls erkannt und isoliert werden.  
  
 Weitere Informationen zu WCF-Sicherheit, finden Sie unter [Sicherheitsübersicht](../../../../docs/framework/wcf/feature-details/security-overview.md). Weitere Informationen zur Programmierung von WCF finden Sie unter [Basis-WCF-Programmierung](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Überwachungsstufe und Überwachungsverhalten  
 Es gibt zwei Stufen für die Sicherheitsüberwachung:  
  
-   Autorisierung auf Dienstebene: Es wird ein Aufrufer autorisiert.  
  
-   Auf der Nachrichtenebene, in der WCF für die Gültigkeit der Nachricht überprüft und authentifiziert den Aufrufer.  
  
 Sie können beide Überwachungsstufen auf Erfolg oder Fehler, die so genannte überprüfen die *Überwachungsverhalten*.  
  
## <a name="audit-log-location"></a>Auswahl des Überwachungsprotokolls  
 Nachdem Überwachungsstufe und Überwachungsverhalten festgelegt wurden, können Sie (oder ein Administrator) angeben, in welches Überwachungsprotokoll geschrieben werden soll. Zur Auswahl stehen drei Optionen: Standard (Default), Anwendung (Application) und Sicherheit (Security). Wenn Sie Standard auswählen, ist das tatsächlich verwendete Protokoll vom verwendeten Betriebssystem abhängig und davon, ob auf diesem System in das Sicherheitsprotokoll geschrieben werden darf. Weitere Informationen finden Sie im Abschnitt "Betriebssystem" weiter unten in diesem Thema.  
  
 Zum Schreiben in das Sicherheitsprotokoll ist die Berechtigungsstufe `SeAuditPrivilege` erforderlich. Standardmäßig verfügen nur die Konten "Lokales System" und "Netzwerkdienst" über diese Berechtigung. Zum Verwalten der Sicherheitsprotokollfunktionen `read` und `delete` ist die Berechtigungsstufe `SeSecurityPrivilege` erforderlich. Standardmäßig verfügen nur Administratoren über diese Berechtigung.  
  
 Authentifizierte Benutzer dagegen dürfen das Anwendungsprotokoll anzeigen und in dieses Protokoll schreiben. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] schreibt standardmäßig Überwachungsereignisse in das Anwendungsprotokoll. Dieses Protokoll kann auch persönliche Daten enthalten, die allen authentifizierten Benutzern zugänglich sind.  
  
## <a name="suppressing-audit-failures"></a>Unterdrücken von Überwachungsfehlern  
 Eine weitere Option bei der Überwachung ist die Unterdrückung von Überwachungsfehlern. Standardmäßig wirken sich Überwachungsfehler nicht auf die Anwendung aus. Bei Bedarf können Sie diese Option jedoch auf `false` setzen. In diesem Fall wird eine Ausnahme ausgelöst.  
  
## <a name="programming-auditing"></a>Programmieren der Überwachung  
 Sie können das Überwachungsverhalten entweder programmatisch oder über die Konfiguration festlegen.  
  
### <a name="auditing-classes"></a>Überwachen von Klassen  
 In der folgenden Tabelle werden die Klassen und Eigenschaften vorgestellt, mit denen das Überwachungsverhalten programmiert wird.  
  
|Klasse|Beschreibung|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Ermöglicht das Festlegen von Optionen für die Überwachung als Dienstverhalten.|  
|<xref:System.ServiceModel.AuditLogLocation>|Eine Enumeration, mit der festgelegt wird, in welches Protokoll geschrieben werden soll. Die möglichen Werte sind Standard (Default), Anwendung (Application) und Sicherheit (Security). Bei Auswahl von "Standard" (Default) wird das Protokoll durch das Betriebssystem bestimmt. Weitere Informationen finden Sie unter "Auswählen des Anwendungsereignisprotokolls oder des Sicherheitsereignisprotokolls" weiter unten in diesem Thema.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Legt fest, welche Arten von Ereignissen für die Nachrichtenauthentifizierung auf Nachrichtenebene überwacht werden. Zur Auswahl stehen `None`, `Failure`, `Success` und `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Legt fest, welche Arten von Ereignissen für die Dienstautorisierung auf Dienstebene überwacht werden. Zur Auswahl stehen `None`, `Failure`, `Success` und `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Legt fest, was mit der Clientanforderung geschieht, wenn bei der Überwachung ein Fehler auftritt. Zum Beispiel, wenn der Dienst versucht, in das Sicherheitsprotokoll zu schreiben, ohne über die `SeAuditPrivilege`-Berechtigung zu verfügen. Der Standardwert `true` gibt an, dass Fehler ignoriert werden und die Clientanforderung normal verarbeitet wird.|  
  
 Ein Beispiel für das Einrichten einer Anwendung, Überwachungsereignisse zu protokollieren, finden Sie unter [Vorgehensweise: Überwachen von Sicherheitsereignissen](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Konfiguration  
 Sie können auch die Konfiguration verwenden, an Überwachungsverhalten durch Hinzufügen einer [ \<ServiceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) unter der [ \<Verhaltensweisen >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Sie müssen das Element unter Hinzufügen einer [ \<Verhalten >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) wie im folgenden Code gezeigt.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!— auditLogLocation="Application" or "Security" -—>  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />   
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Falls bei aktivierter Überwachung `auditLogLocation` nicht angegeben wird, lautet der standardmäßige Protokollname "Security" bei Plattformen, auf denen in das Sicherheitsprotokoll geschrieben werden darf. Andernfalls wird "Application" verwendet. Das Schreiben in das Sicherheitsprotokoll wird nur von den Betriebssystemen [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] und [!INCLUDE[wv](../../../../includes/wv-md.md)] unterstützt. Weitere Informationen finden Sie im Abschnitt "Betriebssystem" weiter unten in diesem Thema.  
  
## <a name="security-considerations"></a>Sicherheitsüberlegungen  
 Wenn böswillige Benutzer erkennen, dass die Überwachung aktiviert ist, können diese Angreifer ungültige Nachrichten senden, die dazu führen, dass Überwachungseinträge geschrieben werden. Wenn das Überwachungsprotokoll auf diese Weise ausgefüllt wird, schlägt das Überwachungssystem fehl. Legen Sie die <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>-Eigenschaft auf `true` fest, und verwenden Sie die Eigenschaften der Ereignisanzeige zum Steuern des Überwachungsverhaltens, um diese Gefahr zu umgehen. Weitere Informationen finden Sie unter den Microsoft Support-Artikel zum Anzeigen und Verwalten von Ereignisprotokollen mithilfe der Ereignisanzeige in Windows XP unter [anzeigen und Verwalten von Ereignisprotokollen in der Ereignisanzeige in Windows XP](https://go.microsoft.com/fwlink/?LinkId=89150).  
  
 Unter [!INCLUDE[wxp](../../../../includes/wxp-md.md)] sind die in das Anwendungsprotokoll geschriebenen Überwachungsereignisse für alle authentifizierten Benutzer sichtbar.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Auswählen des Anwendungsereignisprotokolls oder des Sicherheitsereignisprotokolls  
 Die folgenden Tabellen enthalten Informationen, die Ihnen dabei helfen sollen zu entscheiden, ob in das Anwendungsereignisprotokoll oder in das Sicherheitsereignisprotokoll geschrieben werden soll.  
  
#### <a name="operating-system"></a>Betriebssystem  
  
|System|Anwendungsprotokoll|Sicherheitsprotokoll|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] oder höher|Unterstützt|Nicht unterstützt|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] und [!INCLUDE[wv](../../../../includes/wv-md.md)]|Unterstützt|Threadkontext muss `SeAuditPrivilege` verarbeiten|  
  
#### <a name="other-factors"></a>Andere Faktoren  
 Neben dem Betriebssystem wird die Aktivierung der Protokollierung noch durch andere, in der folgenden Tabelle beschriebene Einstellungen gesteuert.  
  
|Faktor|Anwendungsprotokoll|Sicherheitsprotokoll|  
|------------|---------------------|------------------|  
|Überwachungsrichtlinienverwaltung|Nicht zutreffend.|Das Sicherheitsprotokoll wird nicht nur über die Konfiguration, sondern auch über die Richtlinie der lokalen Sicherheitsautorität (LSA) gesteuert. Darüber hinaus muss die Kategorie "Objektzugriffsversuche überwachen" aktiviert sein.|  
|Standardmäßige Benutzerfreundlichkeit|Alle authentifizierten Benutzer können in das Anwendungsprotokoll schreiben, es sind also für Anwendungsprozesse keine weiteren Berechtigungsschritte erforderlich.|Der Anwendungsprozess (Kontext) muss über die `SeAuditPrivilege`-Berechtigung verfügen.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Übersicht über die Sicherheit](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Einfache WCF-Programmierung](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Vorgehensweise: Überwachen von Sicherheitsereignissen](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [\<ServiceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
 [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [Sicherheitsmodell für Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
