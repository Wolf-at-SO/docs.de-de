---
title: Installieren von f#
description: Erfahren Sie, wie Sie F#-basierend auf Ihrer Umgebung installieren.
ms.date: 08/28/2018
ms.openlocfilehash: 6c10b958e35bf7925965d076a48839b0ce19d2c0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515896"
---
# <a name="install-f"></a>Installieren von f# #

Sie können f# auf verschiedene Arten, abhängig von Ihrer Umgebung installieren.

## <a name="install-f-with-visual-studio"></a>F# mit Visual Studio installieren.

Wenn Sie herunterladen werden [Visual Studio](https://visualstudio.microsoft.com/) zum ersten Mal wird es zunächst Visual Studio-Installer installieren. Installieren Sie die entsprechende SKU von Visual Studio über den Installer. Wenn Sie bereits installiert haben, klicken Sie auf **ändern**.

Als Nächstes sehen Sie, eine Liste von Workloads. Wählen Sie **ASP.NET und Webentwicklung**, die f#-Unterstützung, Unterstützung für .NET Core, installiert und F#-Unterstützung für ASP.NET Core-Projekte.

Klicken Sie anschließend **ändern** in der unteren rechten Ecke.  Dadurch wird alles, was installiert, die Sie ausgewählt haben. Anschließend können Sie Visual Studio 2017 mit F#-sprachunterstützung öffnen, indem Sie auf **starten**.

## <a name="install-f-with-visual-studio-for-mac"></a>Installieren von f# in Visual Studio für Mac

F# ist standardmäßig unter installiert [Visual Studio für Mac](https://visualstudio.microsoft.com/vs/mac/), unabhängig davon, welche Konfiguration Sie auswählen.

Nachdem die Installation abgeschlossen ist, wählen Sie "Starten Sie Visual Studio". Sie können es auch über den Finder unter MacOS starten.

## <a name="install-f-with-visual-studio-code"></a>Installieren von f# mit Visual Studio Code

Sie benötigen [Git-Installation](https://git-scm.com/download) und verfügbar ist, auf dem Weg zur Stellen verwenden der Projektvorlagen das Projekt. Sie können überprüfen, dass es ordnungsgemäß, durch Eingabe installiert ist `git --version` an einer Eingabeaufforderung, und drücken **EINGABETASTE**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](http://www.mono-project.com) dient zur [f# Interactive](../tutorials/fsharp-interactive/index.md) unterstützen. Die einfachste Möglichkeit zum Installieren von Mono unter MacOS ist über Homebrew. Geben Sie einfach Folgendes in Ihrem Terminal ein:

```console
brew install mono
```

Installieren Sie auch die [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com) dient zur [f# Interactive](../tutorials/fsharp-interactive/index.md) unterstützen. Wenn Sie sich unter Debian oder Ubuntu sind, können Sie Folgendes:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Installieren Sie auch die [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Installieren Sie [Visual Studio mit f#-Unterstützung](#install-f-with-visual-studio). Dadurch werden alle erforderlichen Komponenten zum Schreiben, kompilieren und Ausführen von f#-Code installiert.

Installieren Sie auch die [.NET Core SDK](https://www.microsoft.com/net/download/).

---

Sie müssen dann [Visual Studio Code](https://code.visualstudio.com) installiert.

Klicken Sie dann auf das Symbol "Erweiterungen" und suchen Sie nach "Ionide":

Erforderlich für f#-Unterstützung in Visual Studio Code ist die einzige-Plug-in [Ionide-Fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Allerdings können Sie auch installieren [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) abzurufenden [FAKE](https://fsharp.github.io/FAKE/) unterstützen und [Ionide-Paket-Abhängigkeits](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) abzurufenden [Paket-Abhängigkeits](https://fsprojects.github.io/Paket/) unterstützen. Falsche und Paket-Abhängigkeits sind zusätzliche F#-Community-Tools für Projekte erstellen und Verwalten von Abhängigkeiten, bzw.
