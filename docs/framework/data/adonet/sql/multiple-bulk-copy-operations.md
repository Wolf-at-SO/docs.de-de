---
title: Mehrere Massenkopiervorgänge
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: e6a9a82a49d2db2f1a49420c296be6dbf6d37d67
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520295"
---
# <a name="multiple-bulk-copy-operations"></a>Mehrere Massenkopiervorgänge
Sie können mehrere Massenkopiervorgänge mithilfe einer einzigen Instanz der <xref:System.Data.SqlClient.SqlBulkCopy>-Klasse durchführen. Wenn die Parameter der Vorgänge zwischen den Kopien (z. B. den Namen der Zieltabelle) zu ändern, müssen Sie diese aktualisieren, vor allen nachfolgenden Aufrufen auf der **WriteToServer** Methoden, wie im folgenden Beispiel gezeigt. Sofern sie nicht explizit geändert werden, bleiben alle Eigenschaftswerte wie im vorherigen Massenkopiervorgang einer angegebenen Instanz erhalten.  
  
> [!NOTE]
>  Es ist effizienter, mehrere Massenkopiervorgänge mithilfe derselben Instanz der <xref:System.Data.SqlClient.SqlBulkCopy> durchzuführen, als für jeden Vorgang eine separate Instanz zu verwenden.  
  
 Wenn Sie mehrere Massenkopiervorgänge mithilfe desselben <xref:System.Data.SqlClient.SqlBulkCopy>-Objekts durchführen, bestehen keine Einschränkungen, ob sich die Quell- oder Zielinformationen bei jedem Vorgang gleichen oder unterscheiden. Sie müssen sich jedoch vergewissern, dass die Informationen der Spaltenzuordnung immer ordnungsgemäß festgelegt sind, wenn Sie auf den Server schreiben.  
  
> [!IMPORTANT]
>  In diesem Beispiel wird nicht ausgeführt werden, es sei denn, Sie die Arbeitstabellen erstellt haben, wie in beschrieben [Einrichtung der Massenkopierbeispiele](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Dieser Code wird bereitgestellt, um zu veranschaulichen die Syntax für die Verwendung von **"SqlBulkCopy"** nur. Wenn sich die Quell- und die Zieltabelle in derselben SQL Server-Instanz befinden, lassen sich die Daten einfacher und schneller mit einer Transact-SQL-`INSERT … SELECT`-Anweisung kopieren.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopiervorgänge in SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET Managed Provider und DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)
