---
title: 'Vorgehensweise: Auflisten von Verzeichnisinhalt mit FTP'
description: In diesem Artikel wird ein Beispiel für die Vorgehensweise zum Auflisten von Verzeichnisinhalten eines FTP-Servers veranschaulicht.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
ms.assetid: 130c64c9-7b7f-4672-9b3b-d946bd2616c5
ms.openlocfilehash: 26a02cdacfb73b9fa75976ee67c2ef09784cfc71
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028213"
---
# <a name="how-to-list-directory-contents-with-ftp"></a>Vorgehensweise: Auflisten von Verzeichnisinhalt mit FTP

In diesem Beispiel wird gezeigt, wie Sie den Verzeichnisinhalt eines FTP-Servers auflisten können.

## <a name="example"></a>Beispiel

```csharp
using System;
using System.IO;
using System.Net;

namespace Examples.System.Net
{
    public class WebRequestGetExample
    {
        public static void Main ()
        {
            // Get the object used to communicate with the server.
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/");
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails;

            // This example assumes the FTP site uses anonymous logon.
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");

            FtpWebResponse response = (FtpWebResponse)request.GetResponse();

            Stream responseStream = response.GetResponseStream();
            StreamReader reader = new StreamReader(responseStream);
            Console.WriteLine(reader.ReadToEnd());

            Console.WriteLine($"Directory List Complete, status {response.StatusDescription}");

            reader.Close();
            response.Close();
        }
    }
}
```

```vb
Imports System.IO
Imports System.Net

Namespace Examples.System.Net
    Public Module WebRequestGetExample
        Public Sub Main()
            ' Get the object used to communicate with the server.
            Dim request As FtpWebRequest = CType(WebRequest.Create("ftp://www.contoso.com/"), FtpWebRequest)
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails

            ' This example assumes the FTP site uses anonymous logon.
            request.Credentials = New NetworkCredential("anonymous", "janeDoe@contoso.com")

            Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)

            Dim responseStream As Stream = response.GetResponseStream()
            Dim reader As StreamReader = New StreamReader(responseStream)
            Console.WriteLine(reader.ReadToEnd())

            Console.WriteLine($"Directory List Complete, status {response.StatusDescription}")

            reader.Close()
            response.Close()
        End Sub
    End Module
End Namespace
```