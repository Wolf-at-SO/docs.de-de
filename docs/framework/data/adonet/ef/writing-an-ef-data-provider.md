---
title: Schreiben eines Entity Framework-Datenanbieters
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 50c0555d84c5b5f180c8c49a8419e8a414a4befe
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863400"
---
# <a name="writing-an-entity-framework-data-provider"></a>Schreiben eines Entity Framework-Datenanbieters
In diesem Abschnitt wird erläutert, wie zum Schreiben einer [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Anbieter, um eine Datenquelle als SQL Server unterstützt. Die [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] umfasst einen Anbieter, die SQL Server unterstützt.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Einführung in das Entity Framework-Anbietermodell  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ist Datenbank-unabhängig. Sie können mit dem ADO.NET-Anbietermodell einen Anbieter schreiben, um eine Verbindung mit verschiedenen Datenquellen herzustellen.  
  
 Der mit dem ADO.NET-Datenanbietermodell erstellte Entity Framework-Datenanbieter führt die folgenden Funktionen aus:  
  
-   Zuordnen von primitiven Typen des Entity Data Model (EDM) zu Anbietertypen.  
  
-   Bereitstellen von anbieterspezifischen Funktionen.  
  
-   Generieren von anbieterspezifischen Befehlen für einen angegebenen DbQueryCommandTree zur Unterstützung von [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]-Abfragen.  
  
-   Generieren von anbieterspezifischen Updatebefehlen für einen angegebenen DbModificationCommandTree zur Unterstützung von Updates durch den [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Bereitstellen von Zuordnungsdateien für die Speicherschemadefinition zur Unterstützung der Generierung eines Modells auf Grundlage einer Datenbank.  
  
-   Bereitstellen von Metadaten (z. B. Tabellen und Sichten) über ein konzeptionelles Modell.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Beispiel  
 Finden Sie unter den [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) ein Beispiel für eine [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Anbieter, der eine Datenquelle als SQL Server unterstützt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [SQL-Generierung](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [Generierung von Änderungen in SQL](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [Anbietermanifestspezifikation](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Datenanbietern](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
