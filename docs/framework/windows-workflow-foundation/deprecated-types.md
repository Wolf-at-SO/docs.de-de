---
title: Veraltete Typen in Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: b25be26d4c0ad6c423b011cd7cad24a8728333f5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857641"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Veraltete Typen in Windows Workflow Foundation
In .NET 4 hat das Workflowteam eine neue Workflow-Engine im <xref:System.Activities>-Namespace eingeführt. Mit der Version von .NET 4.5 Beta markieren wir die meisten Typen in den "WF3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, und <xref:System.Workflow.Runtime> Namespaces als veraltet.  
  
## <a name="obsolete-namespaces-and-tools"></a>Veraltete Namespaces und Tools  
 Die folgenden Assemblys enthalten mindestens einen öffentlichen Typ, der veraltet sein wird:  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   Wfc.exe  
  
 Daher werden bei Kunden, die veraltete WF3-APIs verwenden, Erstellungswarnungen mit einer Meldung angezeigt, die der folgenden ähnelt:  
  
 **Warnung: BC40000: "X" ist veraltet: wf3-Typen sind veraltet. Verwenden Sie stattdessen wf4.** In einem zukünftigen Release werden die Typen aus .NET Framework entfernt, doch der genaue Zeitpunkt hierfür steht noch nicht fest (nicht in 4.5). Dieser Schritt ermöglicht es uns, unseren Kunden unsere Pläne mitzuteilen und ihnen ausreichend Zeit zu geben, zum neuen WF4-Modell zu wechseln. Zur Unterstützung dieser in WF 3-Typen werden natürlich weiterhin die [Microsoft Support Lifecycle-Richtlinie](https://aka.ms/MicrosoftSupportLifecycle). Vorhandene WF3-Anwendungen können ohne Probleme unter .NET 4.5 ausgeführt werden. [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] unterstützt neue und vorhandene WF3-basierte Lösungen.  
  
 Regelbezogene Typen im <xref:System.Workflow.Activities.Rules>-Namespace, für die es in WF 4.5 keinen Ersatz gibt, wurden nicht als veraltet markiert.  
  
 Kunden, die ihre Anwendungen zu wf4 migrieren möchten, findet in der Hilfe der [Workflow 4 Migrationsanleitung](migration-guidance.md).
