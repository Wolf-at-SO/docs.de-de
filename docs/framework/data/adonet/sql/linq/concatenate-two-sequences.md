---
title: Verketten von zwei Sequenzen
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: c0a6dde667c4f858d8177dc80a726619f463f3a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354052"
---
# <a name="concatenate-two-sequences"></a>Verketten von zwei Sequenzen
Verwenden Sie den <xref:System.Linq.Queryable.Concat%2A>-Operator, um zwei Sequenzen zu verketten.  
  
 Der <xref:System.Linq.Queryable.Concat%2A>-Operator wurde für geordnete Multisets definiert, bei denen die Reihenfolgen des Empfängers und das Argument identisch sind.  
  
 Die Sortierung in SQL ist der letzte Schritt vor dem Erzeugen von Ergebnissen. Aus diesem Grund wird der <xref:System.Linq.Queryable.Concat%2A> durch Verwendung von `UNION ALL`-Operator implementiert, und die Reihenfolge der Argumente wird nicht beibehalten. Um zu gewährleisten, dass die Sortierung der Ergebnisse richtig ist, stellen Sie sicher, dass diese explizit sortiert werden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird <xref:System.Linq.Queryable.Concat%2A> verwendet, um eine Sequenz der Telefon- und Faxnummern aller `Customer` (Kunden) und `Employee` (Mitarbeiter) zurückzugeben.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird <xref:System.Linq.Queryable.Concat%2A> verwendet, um eine Sequenz aller Namens- und Telefonnummernzuordnungen für `Customer` (Kunden) und `Employee` (Mitarbeiter) zurückzugeben.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Siehe auch  
 [Abfragebeispiele](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Übersetzen von Standardabfrageoperatoren](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
