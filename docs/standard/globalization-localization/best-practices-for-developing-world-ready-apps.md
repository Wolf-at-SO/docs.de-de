---
title: Empfehlungen für die Entwicklung weltweit einsatzfähiger Anwendungen
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35b8e062c9f207eba19bcee5593425095de2e267
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041469"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Empfehlungen für die Entwicklung weltweit einsatzfähiger Anwendungen
In diesem Abschnitt wird die empfohlene Vorgehensweise zum Entwickeln von weltweit einsatzfähigen Anwendungen beschrieben.  
  
## <a name="globalization-best-practices"></a>Empfohlene Vorgehensweise für die Globalisierung  
  
1.  Erstellen Sie den Anwendungs-Unicode intern.  
  
2.  Verwenden Sie die vom <xref:System.Globalization>-Namespace bereitgestellten kulturfähigen Klassen, um Daten zu ändern und zu formatieren.  
  
    -   Verwenden Sie zum Sortieren die <xref:System.Globalization.SortKey>-Klasse und die <xref:System.Globalization.CompareInfo>-Klasse.  
  
    -   Verwenden Sie für Zeichenfolgenvergleiche die <xref:System.Globalization.CompareInfo>-Klasse.  
  
    -   Verwenden Sie zum Formatieren von Datum und Uhrzeit die <xref:System.Globalization.DateTimeFormatInfo>-Klasse.  
  
    -   Verwenden Sie zum Formatieren von numerischen Daten die <xref:System.Globalization.NumberFormatInfo>-Klasse.  
  
    -   Verwenden Sie für gregorianische und nicht gregorianische Kalender die <xref:System.Globalization.Calendar>-Klasse oder eine spezifische Implementierung von Calendar.  
  
3.  Verwenden Sie die in den entsprechenden Situationen von der <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>-Klasse bereitgestellten Kultureigenschafteneinstellungen. Verwenden Sie für Formatierungsaufgaben (wie das Formatieren von Datum und Uhrzeit oder zum Formatieren numerischer Daten) die <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>-Eigenschaft. Verwenden Sie zum Abrufen von Ressourcen die <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>-Eigenschaft. Die `CurrentCulture`-Eigenschaft und die `CurrentUICulture`-Eigenschaft können für jeden Thread einzeln festgelegt werden.  
  
4.  Aktivieren Sie für die Anwendung das Lesen und Schreiben von Daten für eine Vielzahl von Codierungen, indem Sie die Codierungsklassen im <xref:System.Text>-Namespace verwenden. Gehen Sie nicht von ASCII-Daten aus. Gehen Sie davon aus, dass internationale Zeichen überall dort zur Verfügung gestellt werden, wo der Benutzer Text eingeben kann. Beispielsweise sollte die Anwendung internationale Zeichen in Servernamen, Verzeichnissen, Dateinamen, Benutzernamen und URLs akzeptieren.  
  
5.  Wenn Sie die <xref:System.Text.UTF8Encoding>-Klasse verwenden, sollten Sie aus Sicherheitsgründen die von dieser Klasse bereitgestellte Fehlererkennungsfunktion verwenden. Zum Aktivieren der Fehlererkennungsfunktion erstellt die Anwendung eine Instanz der Klasse mit dem Konstruktor, der einen `throwOnInvalidBytes`-Parameter akzeptiert, und legt den Wert dieses Parameters auf `true` fest.  
  
6.  Behandeln Sie Zeichenfolgen möglichst als ganze Zeichenfolgen und nicht als eine Reihe einzelner Zeichen. Dies ist besonders beim Sortieren von und Suchen nach untergeordneten Zeichenfolgen von Bedeutung. Dadurch werden Probleme vermieden, die beim Analysieren von kombinierten Zeichen auftreten können.  
  
7.  Zeigen Sie Text mithilfe der Klassen im <xref:System.Drawing>-Namespace an.  
  
8.  Damit die betriebssystemübergreifende Konsistenz gewährleistet ist, dürfen Benutzereinstellungen <xref:System.Globalization.CultureInfo> nicht überschreiben. Verwenden Sie den `CultureInfo`-Konstruktor, der einen `useUserOverride`-Parameter akzeptiert, und legen Sie diesen auf `false` fest.  
  
9. Testen Sie die Funktionsfähigkeit der Anwendung in internationalen Betriebssystemen und mit internationalen Daten.  
  
10. Wenn eine Sicherheitsentscheidung auf dem Ergebnis eines Zeichenfolgenvergleichs oder der Änderung der Groß-/Kleinschreibung beruht, führen Sie in der Anwendung eine kulturunabhängige Operation aus. Auf diese Weise stellen Sie sicher, dass das Ergebnis nicht vom Wert von `CultureInfo.CurrentCulture` beeinflusst wird. Im Abschnitt „Zeichenfolgenvergleiche mit der aktuellen Kultur“ im Artikel [Bewährte Methoden für die Verwendung von Zeichenfolgen in .NET](../../../docs/standard/base-types/best-practices-strings.md) finden Sie ein Beispiel, das veranschaulicht, wie kulturabhängige Zeichenfolgenvergleiche zu inkonsistenten Ergebnissen führen können.  
  
## <a name="localization-best-practices"></a>Empfohlene Vorgehensweise für die Lokalisierung  
  
1.  Verschieben Sie alle lokalisierbaren Ressourcen in DLLs, die nur für Ressourcen vorgesehen sind. Lokalisierbare Ressourcen sind Benutzeroberflächenelemente, z. B. Zeichenfolgen, Fehlermeldungen, Dialogfelder, Menüs und eingebettete Objektressourcen.  
  
2.  Zeichenfolgen und Benutzeroberflächenressourcen dürfen nicht hart codiert werden.  
  
3.  Legen Sie in den DLLs, die nur für Ressourcen vorgesehen sind, keine nicht lokalisierbaren Ressourcen ab, um Unklarheiten bei der Übersetzung zu vermeiden.  
  
4.  Verwenden Sie keine zusammengesetzten Zeichenfolgen, die während der Laufzeit aus verketteten Ausdrücken erstellt werden. Das Lokalisieren von zusammengesetzten Zeichenfolgen ist schwer, weil bei der Reihenfolge häufig von der englischen Grammatik ausgegangen wird, die in anderen Sprachen nicht zutrifft.  
  
5.  Vermeiden Sie unklare Konstrukte wie "Empty Folder", in denen die Zeichenfolgen je nach grammatischen Rollen der Zeichenfolgenkomponenten unterschiedlich übersetzt werden können. "Empty" kann beispielsweise entweder ein Verb oder ein Adjektiv sein, d. h., das Konstrukt kann in Sprachen wie Deutsch, Italienisch oder Französisch unterschiedlich übersetzt werden.  
  
6.  Vermeiden Sie in der Anwendung die Verwendung von Bildern und Symbolen, die Text enthalten. Das Lokalisieren dieser Texte ist teuer.  
  
7.  Für die Erweiterung der Zeichenfolgen sollte auf der Benutzeroberfläche viel Platz vorhanden sein. In einigen Sprachen sind für manche Ausdrücke 50 bis 75 % mehr Platz als in anderen Sprachen erforderlich.  
  
8.  Verwenden Sie die <xref:System.Resources.ResourceManager?displayProperty=nameWithType>-Klasse, um Ressourcen basierend auf der Kultur abzurufen.  
  
9. Verwenden Sie Visual Studio zum Erstellen von Windows Forms-Dialogfeldern, sodass diese mit dem [Windows Forms Resource Editor (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md) lokalisiert werden können. Windows Forms-Dialogfelder dürfen nicht manuell codiert werden.  
  
10. Es empfiehlt sich, eine professionelle Lokalisierung (Übersetzung) anfertigen zu lassen.  
  
11. Eine vollständige Beschreibung des Erstellens und Lokalisierens von Ressourcen finden Sie unter [Ressourcen in Anwendungen](../../../docs/framework/resources/index.md).  
  
## <a name="globalization-best-practices-for-aspnet-applications"></a>Empfohlene Vorgehensweise für die Globalisierung von ASP.NET-Anwendungen  
  
1.  Legen Sie die <xref:System.Globalization.CultureInfo.CurrentUICulture%2A>-Eigenschaft und die <xref:System.Globalization.CultureInfo.CurrentCulture%2A>-Eigenschaft in der Anwendung explizit fest. Verlassen Sie sich nicht auf Standardwerte.  
  
2.  Bei ASP.NET-Anwendungen handelt es sich um verwaltete Anwendungen, und sie können daher dieselben Klassen wie andere verwaltete Anwendungen zum Abrufen, Anzeigen und Bearbeiten von Informationen auf der Grundlage der Kultur verwenden.  
  
3.  Sie können in ASP.NET die folgenden drei Codierungstypen angeben:  
  
    -   requestEncoding gibt die Codierung an, die der Clientbrowser empfängt.  
  
    -   responseEncoding gibt die Codierung an, die an den Clientbrowser gesendet wird. In den meisten Situationen sollte diese Codierung mit der für requestEncoding angegebenen identisch sein.  
  
    -   fileEncoding gibt die Standardcodierung für die Analyse von ASPX-, ASMX- und ASAX-Dateien an.  
  
4.  Geben Sie die Werte für das requestEncoding-Attribut, das responseEncoding-Attribut, das fileEncoding-Attribut, das culture-Attribut und das uiCulture-Attribut an den folgenden drei Stellen in der ASP.NET-Anwendung an:  
  
    -   Im Globalisierungsabschnitt einer Web.config-Datei. Diese Datei befindet sich außerhalb der ASP.NET-Anwendung. Weitere Informationen finden Sie unter [\<globalization>-Element](https://msdn.microsoft.com/library/e2dffc8e-ebd2-439b-a2fd-e3ac5e620da7).  
  
    -   In einer Seitenanweisung. Wenn sich eine Anwendung auf einer Seite befindet, wurde die Datei bereits gelesen. Daher können für fileEncoding und requestEncoding keine Werte mehr festgesetzt werden. Nur für uiCulture, Culture und responseEncoding können in einer Seitenanweisung Werte angegeben werden.  
  
    -   Programmgesteuert im Anwendungscode. Diese Einstellung kann auf Anforderung geändert werden. Wie bei der Seitendirektive ist es bei Erreichen des Anwendungscodes bereits zu spät für die Festlegung von Werten für fileEncoding und requestEncoding. Nur uiCulture, Culture und responseEncoding können im Anwendungscode angegeben werden.  
  
5.  Der uiCulture-Wert kann auf die vom Browser akzeptierte Sprache festgelegt werden.  
  
## <a name="see-also"></a>Siehe auch

- [Globalisierung und Lokalisierung](../../../docs/standard/globalization-localization/index.md)  
- [Ressourcen in Desktop-Apps](../../../docs/framework/resources/index.md)
