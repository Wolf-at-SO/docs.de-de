---
title: Zeigerkonvertierungen (C#-Programmierhandbuch)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: db809fa9e086351184adcac43d67f53e9456894c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43777387"
---
# <a name="pointer-conversions-c-programming-guide"></a>Zeigerkonvertierungen (C#-Programmierhandbuch)
Die folgende Tabelle zeigt vordefinierte implizite Zeigerkonvertierungen. Implizite Konvertierungen können in vielen Situationen auftreten, einschließlich methodenaufrufender und Zuweisungsansweisungen.  
  
## <a name="implicit-pointer-conversions"></a>Implizite Zeigerkonvertierungen  
  
|Von|Beschreibung|  
|----------|--------|  
|Beliebiger Zeigertyp|void*|  
|NULL|Beliebiger Zeigertyp|  
  
 Die explizite Zeigerkonvertierung wird verwendet, um Konvertierungen, für die keine implizite Konvertierung vorliegt, mithilfe eines CAST-Ausdrucks durchzuführen. Die folgende Tabelle zeigt diese Konvertierungen.  
  
## <a name="explicit-pointer-conversions"></a>Explizite Zeigerkonvertierungen  
  
|Von|Beschreibung|  
|----------|--------|  
|Beliebiger Zeigertyp|Ein beliebiger anderer Zeigertyp|  
|sbyte, byte, short, ushort, int, uint, long oder ulong|Beliebiger Zeigertyp|  
|Beliebiger Zeigertyp|sbyte, byte, short, ushort, int, uint, long oder ulong|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Zeiger auf `int` in einen Zeiger auf `byte` konvertiert. Beachten Sie, dass der Zeiger auf das Byte der Variable mit der niedrigsten Adresse zeigt. Wenn Sie das Ergebnis nach und nach bis auf die Größe von `int` (4 Bytes) erhöhen, können Sie die verbleibenden Bytes der Variable anzeigen.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>Siehe auch

- [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
- [Zeigerausdrücke](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Zeigertypen](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Typen](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed-Anweisung](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
