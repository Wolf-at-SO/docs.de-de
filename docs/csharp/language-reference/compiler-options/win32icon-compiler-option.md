---
title: -win32icon (C#-Compileroptionen)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 5014b1da714f8e29f869d4641da93796a607aa4d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2018
ms.locfileid: "44225346"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (C#-Compileroptionen)
Die Option **-win32icon** fügt der Ausgabedatei eine ICO-Datei hinzu, die der Ausgabedatei im Datei-Explorer das gewünschte Aussehen verleiht.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Argumente  
 `filename`  
 Die ICO-Datei, die Sie Ihrer Ausgabedatei hinzufügen möchten  
  
## <a name="remarks"></a>Hinweise  
 Eine ICO-Datei kann mit dem [Ressourcencompiler](/windows/desktop/menurc/resource-compiler) erstellt werden. Der Ressourcencompiler wird gestartet, wenn Sie ein Visual C++-Programm kompilieren. Aus der RC-Datei wird eine ICO-Datei erstellt.  
  
 Weitere Informationen zum Verweisen auf eine .NET Framework-Ressourcendatei finden Sie unter [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md), weitere Informationen zum Anfügen einer .NET Framework-Ressourcendatei unter [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md). Weitere Informationen zum Importieren einer RES-Datei finden Sie unter [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest  
  
1.  Öffnen Sie die **Eigenschaftenseite**des Projekts.  
  
2.  Klicken Sie auf die Eigenschaftenseite **Anwendung**.  
  
3.  Ändern Sie die Eigenschaft **Anwendungssymbol**.  
  
 Informationen zum programmgesteuerten Festlegen dieser Compileroption finden Sie unter <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## <a name="example"></a>Beispiel  
 Kompilieren Sie `in.cs`, und fügen Sie eine ICO-Datei `rf.ico` hinzu, um `in.exe` zu erzeugen.  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Siehe auch  

- [C#-Compileroptionen](../../../csharp/language-reference/compiler-options/index.md)  
- [Verwalten von Projekt- und Projektmappeneigenschaften](/visualstudio/ide/managing-project-and-solution-properties)
