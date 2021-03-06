---
title: Erneutes Hosten von Designern
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 1901df62ccdeec3f75ce0d8cd85484f46fac4541
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274095"
---
# <a name="designer-rehosting"></a>Erneutes Hosten von Designern
Das erneute Hosten des Designers ist ein allgemeines Szenario, das sich auf das Hosting des Entwurfszeichnungsbereichs des Workflows in einer benutzerdefinierten Anwendung bezieht. Die Hostinganwendung, mit der die meisten Personen vertraut sind, ist Visual Studio, es gibt jedoch eine Reihe von Szenarien, in denen das Anzeigen des Workflow-Designers in einer Anwendung hilfreich sein kann:  
  
-   Das Überwachen von Anwendungen (die Schaffung von Möglichkeiten für einen Endbenutzer, den Prozess sowie Laufzeitdaten zum Prozess, z. B. die gerade aktiven Zustände, die kombinierten Ausführungszeitdaten oder andere Informationen zu einer Instanz des Workflows, visuell darzustellen).  
  
-   Anwendungen, die es einem Benutzer ermöglichen, den Prozess mit einem beschränkten Satz von Aktivitäten anzupassen.  
  
 Zur Unterstützung dieser Anwendungstypen wird der Workflow-Designer als Bestandteil von .NET Framework ausgeliefert und kann in einer WPF-Anwendung oder in einer WinForms-Anwendung mit dem entsprechenden WPF-Hostingcode gehostet werden. Dieses Beispiel veranschaulicht Folgendes:  
  
-   Erneutes Hosten des Workflow-Designers  
  
-   Verwenden der neu gehosteten Toolbox und auch des Eigenschaftenrasters.  
  
## <a name="rehosting-the-designer"></a>Erneutes Hosten des Workflow-Designers  
 In diesem Beispiel wird veranschaulicht, wie das WPF-Layout so erstellt wird, dass es den Designer enthält, wie im folgenden Rasterlayout dargestellt (der Toolboxcode wurde aus Platzgründen weggelassen). Beachten Sie die Benennung der Rahmen, die den Designer und das Eigenschaftenraster enthalten.  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 Im Beispiel wird dann der Designer erstellt und seine primäre <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> und <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> dem entsprechenden Container in der Benutzeroberfläche zugeordnet. Im folgenden Beispiel gibt es einige zusätzliche Codezeilen, die einer Erläuterung bedürfen. Der <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A>-Aufruf ist erforderlich, um die Standardaktivitätsdesigner für die Aktivitäten zuzuordnen, die im Lieferumfang von [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] enthalten sind. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> wird aufgerufen, um das zu bearbeitende WF-Element zu übergeben. Schließlich werden die <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primärer Zeichnungsbereich) und die <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (Eigenschaftenraster) auf der Benutzeroberfläche platziert.  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a>Verwenden der neu gehosteten Toolbox  
 In diesem Beispiel wird das neu gehostete Toolboxsteuerelement deklarativ in XAML verwendet. Beachten Sie, dass in Code ein Typ an den <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper>-Konstruktor übergeben werden kann.  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a>Verwenden des Beispiels  
  
1.  Öffnen Sie die Projektmappe DesignerRehosting.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Drücken Sie F5, um die Anwendung zu kompilieren und auszuführen.  
  
3.  Eine WPF-Anwendung beginnt mit einem neu gehosteten Designer.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, fahren Sie mit [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF) Samples für .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) alle Windows Communication Foundation (WCF) herunterladen und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Beispiele. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`