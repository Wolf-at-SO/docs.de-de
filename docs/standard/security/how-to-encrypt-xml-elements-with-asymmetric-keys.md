---
title: 'Gewusst wie: Entschlüsseln von XML-Elementen mit asymmetrischen Schlüsseln'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b1ca4f0809659b3e164623f488a8585a33ea718
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177285"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Gewusst wie: Entschlüsseln von XML-Elementen mit asymmetrischen Schlüsseln
Sie können die Klassen im <xref:System.Security.Cryptography.Xml>-Namespace verwenden, um ein Element in einem XML-Dokument zu verschlüsseln.  XML-Verschlüsselung ist ein gängiges Verfahren zum Austauschen oder Speichern von verschlüsselten XML-Daten, ohne sich Gedanken machen zu müssen, dass die Daten einfach gelesen werden können.  Weitere Informationen zu XML-Verschlüsselungsstandard, finden Sie die Spezifikation des World Wide Web Consortium (W3C) XML-Verschlüsselung im Pfad http://www.w3.org/TR/xmldsig-core/.  
  
 Sie können die XML-Verschlüsselung verwenden, um jedes XML-Element oder XML-Dokument durch ein <`EncryptedData`>-Element zu ersetzen, das die verschlüsselten XML-Daten enthält.  Das <`EncryptedData`>-Element kann auch Unterelemente mit Informationen über die bei der Verschlüsselung verwendeten Schlüssel und Prozesse enthalten.  XML-Verschlüsselung unterstützt, dass ein Dokument mehrere verschlüsselte Elemente enthält und dass ein Element mehrfach verschlüsselt ist.  Das Codebeispiel in dieser Vorgehensweise veranschaulicht das Erstellen eines <`EncryptedData`>-Elements zusammen mit weiteren Unterelementen, die Sie später bei der Entschlüsselung verwenden können.  
  
 In diesem Beispiel wird ein XML-Element mithilfe zweier Schlüssel verschlüsselt.  Es wird ein öffentliches/privates RSA-Schlüsselpaar generiert und in einem sicheren Schlüsselcontainer gespeichert.  Anschließend wird ein separater Sitzungsschlüssel mithilfe des AES-Algorithmus (Advanced Encryption Standard) erstellt, der auch als Rijndael-Algorithmus bezeichnet wird.  Dieser AES-Sitzungsschlüssel wird verwendet, um das XML-Dokument zu verschlüsseln, und anschließend wird der öffentliche RSA-Schlüssel verwendet, um den AES-Sitzungsschlüssel zu verschlüsseln.  Schließlich werden in diesem Beispiel der verschlüsselte AES-Sitzungsschlüssel sowie die verschlüsselten XML-Daten im XML-Dokument innerhalb eines neuen <`EncryptedData`>-Elements gespeichert.  
  
 Um das XML-Element zu entschlüsseln, rufen Sie den privaten RSA-Schlüssel aus dem Schlüsselcontainer ab, verwenden ihn zum Entschlüsseln des Sitzungsschlüssels und entschlüsseln mit diesem Sitzungsschlüssel das Dokument.  Weitere Informationen dazu, wie Sie ein XML-Element zu entschlüsseln, die mit dieser Vorgehensweise verschlüsselt wurde, finden Sie unter [wie: Entschlüsseln von XML-Elementen mit asymmetrischen Schlüsseln](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Das Beispiel eignet sich für Situationen, in denen mehrere Anwendungen verschlüsselte Daten gemeinsam nutzen müssen, oder in denen eine Anwendung verschlüsselte Daten zwischen den Zeiten speichern muss, in denen sie ausgeführt wird.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>So verschlüsseln Sie ein XML-Element mit einem asymmetrischen Schlüsseln  
  
1.  Erstellen Sie ein <xref:System.Security.Cryptography.CspParameters>-Objekt, und geben Sie den Namen des Schlüsselcontainers an.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Generieren Sie mit der <xref:System.Security.Cryptography.RSACryptoServiceProvider>-Klasse einen symmetrischen Schlüssel.  Der Schlüssel wird automatisch im Schlüsselcontainer gespeichert, wenn Sie das <xref:System.Security.Cryptography.CspParameters>-Objekt an den Konstruktor der <xref:System.Security.Cryptography.RSACryptoServiceProvider>-Klasse übergeben.  Dieser Schlüssel wird zum Verschlüsseln des AES-Sitzungsschlüssels verwendet und kann später abgerufen werden, um den Sitzungsschlüssel zu entschlüsseln.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Erstellen Sie ein <xref:System.Xml.XmlDocument>-Objekt, indem Sie eine XML-Datei von einem Datenträger laden.  Das <xref:System.Xml.XmlDocument>-Objekt enthält das zu verschlüsselnde XML-Element.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  Suchen Sie das angegebene Element im <xref:System.Xml.XmlDocument>-Objekt, und erstellen Sie ein neues <xref:System.Xml.XmlElement>-Objekt, das dem Element entspricht, das Sie verschlüsseln möchten. In diesem Beispiel wird das `"creditcard"`-Element verschlüsselt.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  Erstellen Sie mit der <xref:System.Security.Cryptography.RijndaelManaged>-Klasse einen neuen Sitzungsschlüssel.  Dieser Schlüssel verschlüsselt das XML-Element und wird dann selbst verschlüsselt und im XML-Dokument platziert.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  Erstellen Sie eine neue Instanz der <xref:System.Security.Cryptography.Xml.EncryptedXml>-Klasse, und verwenden Sie diese zusammen mit dem Sitzungsschlüssel zum Verschlüsseln des angegebenen Elements.  Die <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A>-Methode gibt das verschlüsselte Element als Array von verschlüsselten Bytes zurück.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  Erstellen Sie ein <xref:System.Security.Cryptography.Xml.EncryptedData>-Objekt, und weisen Sie ihm den URL-Bezeichner des verschlüsselten XML-Elements zu.  Dieser URL-Bezeichner teilt einem entschlüsselnden Teilnehmer mit, dass das XML-Dokument ein verschlüsseltes Element enthält.  Sie können das <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>-Feld verwenden, um den URL-Bezeichner anzugeben.  Das Klartext-XML-Element wird durch ein `EncryptedData`-Element ersetzt, das von diesem <xref:System.Security.Cryptography.Xml.EncryptedData>-Objekt gekapselt wird.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  Erstellen Sie ein <xref:System.Security.Cryptography.Xml.EncryptionMethod>-Objekt, das mit dem URL-Bezeichner des kryptografischen Algorithmus initialisiert wird, mit dem der Sitzungsschlüssel generiert wurde.  Übergeben Sie das <xref:System.Security.Cryptography.Xml.EncryptionMethod>-Objekt an die <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>-Eigenschaft.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Erstellen Sie ein <xref:System.Security.Cryptography.Xml.EncryptedKey>-Objekt, das den verschlüsselten Sitzungsschlüssel enthalten soll.  Verschlüsseln Sie den Sitzungsschlüssel, fügen Sie ihn dem <xref:System.Security.Cryptography.Xml.EncryptedKey>y-Objekt hinzu, und geben Sie für diesen Sitzungsschlüssel einen Namen und einen URL-Bezeichner ein.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Erstellen Sie ein neues <xref:System.Security.Cryptography.Xml.DataReference>-Objekt, das die verschlüsselten Daten einem bestimmten Sitzungsschlüssel zuordnet.  Mit diesem optionalen Schritt können Sie ohne großen Aufwand angeben, dass mehrere Teile eines XML-Dokuments mit einem einzigen Schlüssel verschlüsselt wurden.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Fügen Sie den verschlüsselten Schlüssel dem <xref:System.Security.Cryptography.Xml.EncryptedData>-Objekt hinzu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Erstellen Sie ein neues <xref:System.Security.Cryptography.Xml.KeyInfo>-Objekt, um den Namen des RSA-Schlüssels anzugeben.  Fügen Sie dieses Objekt dem <xref:System.Security.Cryptography.Xml.EncryptedData>-Objekt hinzu. Dadurch wird der entschlüsselnde Teilnehmer in die Lage versetzt, den richtigen asymmetrischen Schlüssel zu ermitteln, der zum Entschlüsseln des Sitzungsschlüssels zu verwenden ist.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Fügen Sie die verschlüsselten Elementdaten dem <xref:System.Security.Cryptography.Xml.EncryptedData>-Objekt hinzu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Ersetzen Sie das Element aus dem ursprünglichen <xref:System.Xml.XmlDocument>-Objekt durch das <xref:System.Security.Cryptography.Xml.EncryptedData>-Element.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Speichern Sie das <xref:System.Xml.XmlDocument>-Objekt.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a>Beispiel  
 Für dieses Beispiel wird angenommen, dass eine Datei namens `"test.xml"` im selben Verzeichnis wie das kompilierte Programm vorhanden ist.  Außerdem wird angenommen, dass `"test.xml"` ein `"creditcard"`-Element enthält.  Sie können den folgenden XML-Code in eine Datei namens `test.xml` einfügen und mit diesem Beispiel verwenden.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
  
-   Um dieses Beispiel zu kompilieren, müssen Sie einen Verweis auf `System.Security.dll` einfügen.  
  
-   Fügen Sie die folgenden Namespaces hinzu: <xref:System.Xml>, <xref:System.Security.Cryptography> und <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Speichern Sie einen symmetrischen kryptografischen Schlüssel nie im Klartextformat, und übertragen Sie einen symmetrischen Schlüssel nie im Klartextformat zwischen Computern.  Außerdem sollten Sie den privaten Schlüssel eines asymmetrischen Schlüsselpaars niemals in Klartext speichern oder übertragen.  Weitere Informationen über symmetrische und asymmetrische kryptografische Schlüssel finden Sie unter [Erzeugen von Schlüsseln für die Ver- und Entschlüsselung](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Sie sollten einen Schlüssel niemals direkt in Ihren Quellcode einbetten.  Eingebettete Schlüssel können problemlos gelesen werden, aus einer Assembly mithilfe der [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) oder durch die Assembly in einem Text-Editor wie Editor geöffnet.  
  
 Wenn Sie einen kryptografischen Schlüssel nicht mehr benötigen, entfernen Sie ihn aus dem Arbeitsspeicher, indem Sie jedes Byte auf 0 (null) festlegen oder indem Sie die <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A>-Methode der verwalteten Kryptografieklasse aufrufen.  Kryptografische Schlüssel können manchmal von einem Debugger aus dem Arbeitsspeicher oder von einer Festplatte gelesen werden, falls der entsprechende Arbeitsspeicherbereich auf den Datenträger ausgelagert wurde.  
  
## <a name="see-also"></a>Siehe auch

- <xref:System.Security.Cryptography.Xml>  
- [Gewusst wie: Entschlüsseln von XML-Elementen mit asymmetrischen Schlüsseln](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
