---
title: 'Gewusst wie: Implementieren von PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: a7729ec3d06ec701cf2194bed5d90b5bed76573a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44267020"
---
# <a name="how-to-implement-prioritybinding"></a>Gewusst wie: Implementieren von PriorityBinding
<xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funktioniert, indem Sie eine Liste der Bindungen angeben. Die Liste der Bindungen ist von der höchsten zur niedrigsten Priorität geordnet. Wenn die höchste Priorität Bindung einen Wert zurückgibt erfolgreich bei der Verarbeitung wird besteht nie die anderen Bindungen in der Liste verarbeitet werden muss. Es könnte den Fall, den die höchste Priorität Bindung sehr lange dauert, die ausgewertet werden, die nächstniedrigeren Priorität, die einen Wert, erfolgreich zurückgibt verwendet werden, bis eine Bindung mit einer höheren Priorität erfolgreich einen Wert zurückgibt.  
  
## <a name="example"></a>Beispiel  
 Zur Veranschaulichung wie <xref:System.Windows.Data.PriorityBinding> funktioniert, die `AsyncDataSource` Objekt mit den folgenden drei Eigenschaften erstellt wurde: `FastDP`, `SlowerDP`, und `SlowestDP`.  
  
 Get-Accessor der `FastDP` gibt den Wert des der `_fastDP` -Datenmember.  
  
 Get-Accessor der `SlowerDP` wartet 3 Sekunden vor der Rückgabe des Werts des der `_slowerDP` -Datenmember.  
  
 Get-Accessor der `SlowestDP` wartet fünf Sekunden vor der Rückgabe des Werts des der `_slowestDP` -Datenmember.  
  
> [!NOTE]
>  Das Beispiel dient nur der Veranschaulichung. Die [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Richtlinien wird die Definition von Eigenschaften, erheblich langsamer sind, als wäre eine Feldgruppe, empfohlen. Weitere Informationen finden Sie unter [NIB: Auswahl zwischen Eigenschaften und Methoden](https://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 Die <xref:System.Windows.Controls.TextBlock.Text%2A> Eigenschaft gebunden, die die oben genannten `AsyncDS` mit <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Wenn die Bindungs-Engine verarbeitet den <xref:System.Windows.Data.Binding> Objekten, die mit dem ersten Start <xref:System.Windows.Data.Binding>, das gebunden ist, um die `SlowestDP` Eigenschaft. Wenn dies <xref:System.Windows.Data.Binding> wird verarbeitet, es wird keinen Wert zurückgegeben wurde erfolgreich, da es 5 Sekunden, sodass die nächste aktiviert ist <xref:System.Windows.Data.Binding> Element verarbeitet wird. Die nächste <xref:System.Windows.Data.Binding> ist nicht Wert erfolgreich zurück, da es drei Sekunden aktiviert ist. Die Bindungs-Engine verschiebt anschließend die nächste <xref:System.Windows.Data.Binding> -Element, das gebunden ist die `FastDP` Eigenschaft. Dies <xref:System.Windows.Data.Binding> gibt den Wert "Schnell" Wert "zurück. Die <xref:System.Windows.Controls.TextBlock> zeigt nun den Wert "Fast Value".  
  
 Nach 3 Sekunden die `SlowerDP` Eigenschaft gibt den Wert "langsamer" zurück. Die <xref:System.Windows.Controls.TextBlock> zeigt dann den Wert "Langsamer Value".  
  
 Nach 5 Sekunden die `SlowestDP` -Eigenschaft gibt den Wert "Langsamste Value". Diese Bindung hat die höchste Priorität, da er zuerst aufgelistet wird. Die <xref:System.Windows.Controls.TextBlock> zeigt jetzt den Wert "Langsamste Value".  
  
 Finden Sie unter <xref:System.Windows.Data.PriorityBinding> Informationen, was einen erfolgreiche Rückgabewert aus einer Bindung gilt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [Übersicht zur Datenbindung](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Themen zu Vorgehensweisen](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
