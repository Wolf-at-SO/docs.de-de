---
title: Entfernen von Elementen, Attributen und Knoten aus einem XML-Baum (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 9ce63ce6a4ef75dedc788efca11e8dd2bdb471eb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2018
ms.locfileid: "44217489"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>Entfernen von Elementen, Attributen und Knoten aus einem XML-Baum (C#)
Sie können eine XML-Struktur ändern, indem Sie Elemente, Attribute und andere Knotentypen entfernen.  
  
 Das Entfernen eines einzelnen Elements oder Attributs aus einem XML-Dokument ist unkompliziert. Wenn Sie aber Auflistungen von Elementen oder Attributen entfernen, sollten Sie zuerst eine Auflistung in einer Liste materialisieren, bevor Sie die Elemente oder Attribute aus der Liste löschen. Verwenden Sie dazu am besten die <xref:System.Xml.Linq.Extensions.Remove%2A>-Erweiterungsmethode, die diese Aufgabe für Sie übernimmt.  
  
 Der Hauptgrund für diese Vorgehensweise besteht darin, dass die meisten Auflistungen, die Sie aus einer XML-Struktur abrufen, mit verzögerter Ausführung zurückgegeben werden. Wenn Sie die Auflistungen nicht zunächst in einer Liste materialisieren oder wenn Sie nicht die Erweiterungsmethoden verwenden, kommt es möglicherweise zu einer bestimmten Form von Fehlern. Weitere Informationen finden Sie unter [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#) (Fehler durch Vermischung von deklarativem und imperativem Code (LINQ to XML) (C#))](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Die folgenden Methoden entfernen Knoten und Attribute aus einer XML-Struktur.  
  
|Methode|Beschreibung |  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Entfernt einen <xref:System.Xml.Linq.XAttribute> aus seinem übergeordneten Knoten.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Entfernt die untergeordneten Knoten aus einem <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Entfernt Inhalt und Attribute aus einem <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Entfernt die Attribute eines <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Entfernt das Attribut, wenn Sie als Wert `null` übergeben.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Entfernt das untergeordnete Element, wenn Sie als Wert `null` übergeben.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Entfernt einen <xref:System.Xml.Linq.XNode> aus seinem übergeordneten Knoten.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Entfernt jedes Attribut oder Element in der Quellauflistung aus seinem übergeordneten Element.|  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung   
 In diesem Beispiel werden drei Ansätze zum Entfernen von Elementen gezeigt. Zuerst entfernt das Beispiel ein einzelnes Element. Als Zweites ruft das Beispiel eine Auflistung von Elementen ab, materialisiert sie mit dem <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>-Operator und entfernt die Auflistung. Zum Schluss ruft das Beispiel eine Auflistung von Elementen ab und entfernt diese mit der <xref:System.Xml.Linq.Extensions.Remove%2A>-Erweiterungsmethode.  
  
 Weitere Informationen zum <xref:System.Linq.Enumerable.ToList%2A>-Operator finden Sie unter [Konvertieren von Datentypen (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).  
  
### <a name="code"></a>Code  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
    <Child1>  
        <GrandChild1/>  
        <GrandChild2/>  
        <GrandChild3/>  
    </Child1>  
    <Child2>  
        <GrandChild4/>  
        <GrandChild5/>  
        <GrandChild6/>  
    </Child2>  
    <Child3>  
        <GrandChild7/>  
        <GrandChild8/>  
        <GrandChild9/>  
    </Child3>  
</Root>");  
root.Element("Child1").Element("GrandChild1").Remove();  
root.Element("Child2").Elements().ToList().Remove();  
root.Element("Child3").Elements().Remove();  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a>Kommentare  
 Dieser Code erzeugt die folgende Ausgabe:  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 Beachten Sie, dass das erste Element der zweiten Unterebene aus `Child1` entfernt wurde. Alle Elemente der zweiten Unterebene wurden aus `Child2` und `Child3` entfernt.  
  
## <a name="see-also"></a>Siehe auch

- [Modifying XML Trees (LINQ to XML) (C#) (Ändern von XML-Strukturen (LINQ to XML) (C#))](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
