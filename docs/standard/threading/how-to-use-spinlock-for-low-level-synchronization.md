---
title: 'Gewusst wie: Synchronisierung auf niedriger Ebene mit SpinLock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 216480e893f6dbebbb204cbf2bfebae8dc139ec4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2018
ms.locfileid: "44190701"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Gewusst wie: Synchronisierung auf niedriger Ebene mit SpinLock
Das folgende Beispiel zeigt die Verwendung eines <xref:System.Threading.SpinLock>.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel ist der Arbeitsaufwand für den kritischen Abschnitt minimal, wodurch dieser zu einem guten Kandidaten für ein <xref:System.Threading.SpinLock> wird. Durch geringfügige Erhöhung des Aufwands erhöht sich die Leistung des <xref:System.Threading.SpinLock> im Vergleich zu einer Standardsperre. Ab einem bestimmten Punkt wird ein SpinLock jedoch aufwändiger als eine Standardsperre. Mit der neuen Parallelitätsprofilerstellungsfunktion in den Profilerstellungstools können Sie feststellen, welcher Sperrentyp in Ihrem Programm die bessere Leistung bietet. Weitere Informationen finden Sie unter [Parallelitätsschnellansicht](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> kann geeignet sein, wenn die Sperre einer freigegebenen Ressource nicht sehr lange gehalten werden soll. In solchen Fällen wird auf Multikerncomputern möglicherweise ein effizientes Verhalten erzielt, wenn der blockierte Thread einige Spinzyklen ausführt, bis die Sperre aufgehoben wird. Durch die Spinzyklen wird der Thread nicht blockiert, was zu einer hohen CPU-Auslastung führt. Unter bestimmten Bedingungen beendet <xref:System.Threading.SpinLock> den Spinvorgang, um Ressourcenmangel (Starvation) logischer Prozessoren oder Prioritätsumkehrung in Systemen mit Hyperthreading zu verhindern.  
  
 In diesem Beispiel wird die <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>-Klasse verwendet, die Benutzersynchronisierung für den Multithreadzugriff erfordert. In Anwendungen für .NET Framework Version 4 ist die Verwendung von <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, die keine Benutzersperren erfordert, eine weitere Option.  
  
 Beachten Sie die Verwendung von `false` (`False` in Visual Basic) im Aufruf von <xref:System.Threading.SpinLock.Exit%2A>. Dieser Ansatz bietet die beste Leistung. Geben Sie bei IA64-Architekturen `true` (`True`) an, um die Arbeitsspeicherumgrenzung zu verwenden. Dadurch werden die Schreibpuffer geleert, um sicherzustellen, dass die Sperre jetzt verfügbar ist und andere Threads beendet werden können.  
  
## <a name="see-also"></a>Siehe auch

- [Threading Objects and Features (Threadingobjekte und -funktionen)](../../../docs/standard/threading/threading-objects-and-features.md)
