---
title: 'Gewusst wie: Ausführen von parallelen Vorgängen mithilfe von Parallel.Invoke'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d0870d23c5606fbdd8b4a2f78c4d8b9f4ddc93e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259635"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Gewusst wie: Ausführen von parallelen Vorgängen mithilfe von Parallel.Invoke
In diesem Beispiel wird veranschaulicht, wie Vorgänge parallelisiert werden können, indem <xref:System.Threading.Tasks.Parallel.Invoke%2A> in der Task Parallel Library verwendet wird. Es werden drei Vorgänge für eine freigegebene Datenquelle ausgeführt. Da die Quelle durch keinen der Vorgänge geändert wird, können diese auf einfache Weise parallel ausgeführt werden.  
  
> [!NOTE]
>  Diese Dokumentation definiert Delegaten in TPL mithilfe von Lambdaausdrücken. Falls Sie mit der Verwendung von Lambdaausdrücken in C# oder Visual Basic nicht vertraut sind, finden Sie entsprechende Informationen unter [Lambdaausdrücke in PLINQ und TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 Beachten Sie, dass Sie mit <xref:System.Threading.Tasks.Parallel.Invoke%2A> nur angeben, welche Aktionen gleichzeitig ausgeführt werden sollen. Alle Details der Threadplanung, einschließlich automatischem Skalieren entsprechend der Anzahl von Kernen auf dem Hostcomputer, werden von der Common Language Runtime verwaltet.  
  
 In diesem Beispiel werden die Vorgänge, nicht die Daten parallelisiert. Eine alternative Vorgehensweise besteht darin, die LINQ-Abfragen mithilfe von PLINQ zu parallelisieren und die Abfragen sequenziell auszuführen. Sie könnten die Daten aber auch parallelisieren, indem Sie PLINQ verwenden. Eine weitere Möglichkeit ist, sowohl die Abfragen als auch die Aufgaben zu parallelisieren. Durch den resultierenden Mehraufwand kann zwar die Leistung auf Hostcomputern mit relativ wenigen Prozessoren beeinträchtigt werden, die Skalierung auf Computern mit vielen Prozessoren ist jedoch deutlich besser.  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
  
-   Kopieren Sie das gesamte Beispiel, fügen Sie es in ein Microsoft Visual Studio 2010-Projekt ein, und drücken Sie F5.  
  
## <a name="see-also"></a>Siehe auch

- [Parallele Programmierung](../../../docs/standard/parallel-programming/index.md)  
- [Gewusst wie: Abbrechen einer Aufgabe und ihrer untergeordneten Elemente](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
- [Parallel LINQ (PLINQ) (Paralleles LINQ (PLINQ))](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
