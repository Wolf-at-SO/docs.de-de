---
title: Einführung in Delegaten
description: Erfahren Sie in diesem Überblick etwas über die Grundlagen und die Ziele beim Sprachentwurf von Delegaten.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: d42d9d10aeaa153f12933fa3a59e58719f7741e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212186"
---
# <a name="introduction-to-delegates"></a>Einführung in Delegaten

[Vorheriges](delegates-events.md)

Delegaten bieten einen Mechanismus mit *später Bindung* in .NET. Späte Bindung bedeutet, dass Sie einen Algorithmus erstellen, in dem der Aufrufer auch mindestens eine Methode bereitstellt, die einen Teil des Algorithmus implementiert.

Sie können z.B. eine Liste von Sternen in einer Astronomie-Anwendung sortieren.
Sie können diese Sterne nach ihrer Entfernung von der Erde, nach der Größe des Sterns oder ihrer wahrgenommenen Helligkeit sortieren.

In all diesen Fällen macht die Sort()-Methode im Prinzip das Gleiche: Sie ordnet die Elemente in der Liste basierend auf einen Vergleich. Der Code, der zwei Sterne vergleicht, ist bei jeder Sortierreihenfolge unterschiedlich.

Diese Arten von Lösungen wurden in der Softwareentwicklung für ein halbes Jahrhundert verwendet.
Das Delegatenkonzept von C# bietet erstklassige Sprachunterstützung und Typsicherheit rund um das Konzept.

Wie Sie später in dieser Serie sehen werden, ist der C#-Code, den Sie für Algorithmen wie diesen schreiben, typsicher und nutzt die Sprache und den Compiler, um sicherzustellen, dass die Typen mit Argumenten und Rückgabetypen übereinstimmen.

## <a name="language-design-goals-for-delegates"></a>Sprachliche Entwurfsziele für Delegaten

Die Sprachentwickler haben mehrere Ziele für die Funktion aufgezählt, die schließlich Delegaten geworden sind.

Das Team wollte ein allgemeines Sprachkonstrukt entwerfen, das für alle Algorithmen mit später Bindung verwendet werden kann. Dadurch können Softwareentwickler ein Konzept erlernen und dasselbe Konzept bei vielen verschiedenen Softwareproblemen anwenden.

Außerdem sollten sowohl einzelne als auch Multicast-Methodenaufrufe unterstützt werden. Multicastdelegaten sind Delegaten, in denen mehrere Methoden miteinander verbunden wurden. Beispiele dafür finden Sie [später in dieser Serie](delegate-class.md). 

Delegaten sollten dieselbe Typsicherheit unterstützen, die Entwickler von allen C#-Konstrukten erwarten. 

Die Sprachentwickler erkannten schließlich, dass ein Ereignismuster ein bestimmtes Muster ist, in dem Delegaten (oder jeder beliebige Algorithmus mit später Bindung) sehr nützlich sind. Daher sollte sichergestellt werden, dass der Code für den Delegaten die Basis für das .NET-Ereignismuster bereitstellen konnte.

Das Ergebnis dieser Arbeit war die Delegat- und Ereignisunterstützung in C# und .NET. Die übrigen Artikel in diesem Abschnitt behandeln die Sprachfunktionen, die Bibliotheksunterstützung und die allgemeinen Ausdrücke, die bei der Arbeit mit Delegaten verwendet werden.

Sie werden das `delegate`-Schlüsselwort kennenlernen und erfahren, welchen Code es generiert. Außerdem werden Sie die Funktionen der `System.Delegate`-Klasse kennenlernen und erfahren, wie diese Funktionen verwendet werden. Darüber hinaus erfahren Sie, wie Sie typsichere Delegaten erstellen und wie Sie Methoden erstellen, die durch Delegaten aufgerufen werden können. Sie erfahren, wie Sie mithilfe von Lambdaausdrücken mit Delegaten und Ereignissen arbeiten und an welcher Stelle Delegaten einer der Bausteine für LINQ werden. Darüber hinaus erfahren Sie, warum Delegaten die Grundlage für das .NET-Ereignismuster sind und wie sie sich unterscheiden.

Alles in allem wird erläutert, warum Delegaten ein wesentlicher Bestandteil in der .NET-Programmierung sind und wie sie mit den Framework-APIs arbeiten.

Fangen wir also an.

[Nächste](delegate-class.md)
