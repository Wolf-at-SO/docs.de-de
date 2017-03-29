---
title: "virtual (C#-Referenz) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "virtual_CSharpKeyword"
  - "virtual"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "virtual-Schlüsselwort [C#]"
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# virtual (C#-Referenz)
Mit dem `virtual`\-Schlüsselwort können eine Methode, eine Eigenschaft, ein Indexer oder eine Ereignisdeklaration geändert und in einer abgeleiteten Klasse überschrieben werden.  Zum Beispiel kann diese Methode von jeder Klasse überschrieben werden, die diese Methode erbt:  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 Die Implementierung eines virtuellen Members kann durch einen [override](../../../csharp/language-reference/keywords/override.md)\-Member in einer abgeleiteten Klasse geändert werden.  Weitere Informationen zur Verwendung des `virtual`\-Schlüsselworts finden Sie unter [Versionsverwaltung mit den Schlüsselwörtern "override" und "new"](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) und [Wann müssen die Schlüsselwörter "override" und "new" verwendet werden?](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## Hinweise  
 Wenn eine virtuelle Methode aufgerufen wird, wird der Laufzeittyp des Objekts auf einen überschreibenden Member hin überprüft  und der überschreibende Member der tiefsten abgeleiteten Klasse aufgerufen. Wenn keine abgeleitete Klasse den Member überschrieben hat, handelt es sich hierbei möglicherweise um den ursprünglichen Member.  
  
 Standardmäßig sind Methoden nicht virtuell.  Eine nicht virtuelle Methode darf nicht überschrieben werden.  
  
 Der `virtual`\-Modifizierer kann nicht zusammen mit den Modifizierern `static`, `abstract, private` oder `override` verwendet werden.  Im folgenden Beispiel wird eine virtuelle Eigenschaft veranschaulicht:  
  
 [!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 Virtuelle Eigenschaften verhalten sich wie abstrakte Methoden, mit Ausnahme der Unterschiede bei der Deklaration und der Syntax für den Aufruf.  
  
-   Der `virtual`\-Modifizierer darf nicht für eine statische Eigenschaft verwendet werden.  
  
-   In einer abgeleiteten Klasse kann eine virtuelle vererbte Eigenschaft überschrieben werden, indem eine Eigenschaftendeklaration, die den `override`\-Modifizierer verwendet, eingeschlossen wird.  
  
## Beispiel  
 In diesem Beispiel enthält die `Shape`\-Klasse die beiden Koordinaten `x` und `y` sowie die virtuelle `Area()`\-Methode.  Verschiedene Formklassen wie `Circle`, `Cylinder` und `Sphere` erben die `Shape`\-Klasse, und für jede Figur wird die Oberfläche berechnet.  Jede abgeleitete Klasse verfügt über ihre eigene override\-Implementierung von `Area()`.  
  
 Beachten Sie, dass die geerbten Klassen `Circle`, `Sphere`und alle `Cylinder` verwenden konstruktoren, die die Basisklasse initialisiert werden, wie in der folgenden Deklaration veranschaulicht.  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 Das folgende Programm berechnet und zeigt den entsprechenden Bereich für jede Figur an, indem er die entsprechende Implementierung der `Area()`\-Methode entsprechend dem Objekt aufruft, das mit der Methode zugeordnet ist.  
  
 [!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## C\#\-Programmiersprachenspezifikation  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Siehe auch  
 [C\#\-Referenz](../../../csharp/language-reference/index.md)   
 [C\#\-Programmierhandbuch](../../../csharp/programming-guide/index.md)   
 [Modifizierer](../../../csharp/language-reference/keywords/modifiers.md)   
 [C\#\-Schlüsselwörter](../../../csharp/language-reference/keywords/index.md)   
 [Polymorphismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [neu](../../../csharp/language-reference/keywords/new.md)