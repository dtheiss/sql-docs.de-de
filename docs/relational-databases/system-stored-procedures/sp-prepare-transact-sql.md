---
title: Sp_prepare (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepare
ms.assetid: f328c9eb-8211-4863-bafa-347e1bf7bb3f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9b52f71577bed8a0433c8d516cdc9cbd877066e4
ms.sourcegitcommit: f46fd79fd32a894c8174a5cb246d9d34db75e5df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/26/2018
ms.locfileid: "53785931"
---
# <a name="spprepare-transact-sql"></a>sp_prepare (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Bereitet eine parametrisierte [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung und gibt eine Anweisung *behandeln* für die Ausführung.  `sp_prepare` wird aufgerufen, indem ID = 11 in einem tabular Data Stream (TDS)-Paket.  
  
 ![Artikellinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_prepare handle OUTPUT, params, stmt, options  
```  
  
## <a name="arguments"></a>Argumente  
 *Handle*  
 Ein SQL Server generierter *vorbereitete Handle* Bezeichner. *handle* ist ein erforderlicher Parameter mit einem **int** -Rückgabewert.  
  
 *params*  
 Identifiziert parametrisierte Anweisungen. Die *params* -Definition der Variablen wird in der Anweisung an die Stelle der Parametermarkierungen gesetzt. *params* ist ein erforderlicher Parameter, der einen Eingabewert vom Typ **ntext**, **nchar**,oder **nvarchar** erfordert. Geben Sie einen NULL-Wert ein, wenn die Anweisung nicht parametrisiert ist.  
  
 *stmt*  
 Definiert das Resultset des Cursors. Die *Stmt* -Parameter ist erforderlich und erfordert eine **Ntext**, **Nchar**, oder **Nvarchar** Eingabewert.  
  
 *options*  
 Ein optionaler Parameter, der eine Beschreibung der Spalten im Cursorresultset zurückgibt. *Optionen* erfordert den folgenden Eingabedaten Int-Wert:  
  
|Wert|Description|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
## <a name="examples"></a>Beispiele  
A. Im folgenden Beispiel wird eine einfache Anweisung vorbereitet und ausgeführt.  
  
```sql  
DECLARE @P1 int;  
EXEC sp_prepare @P1 output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name FROM sys.databases WHERE name=@P1 AND state_desc = @P2';  
EXEC sp_execute @P1, N'tempdb', N'ONLINE';  
EXEC sp_unprepare @P1;  
```

B. Im folgende Beispiel bereitet eine Anweisung in der AdventureWorks2016-Datenbank vor, und es später noch Mal mit dem Handle ausgeführt.

```sql
-- Prepare query
DECLARE @P1 int;  
EXEC sp_prepare @P1 output,   
    N'@Param int',  
    N'SELECT *
FROM Sales.SalesOrderDetail AS sod
INNER JOIN Production.Product AS p ON sod.ProductID = p.ProductID
WHERE SalesOrderID = @Param
ORDER BY Style DESC;';  

-- Return handle for calling application
SELECT @P1;
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
-----------
1

(1 row affected)
```

Die Anwendung führt dann die Abfrage zweimal unter Verwendung den Handlewert 1, vor dem Verwerfen des vorbereiteten Plans.

```sql
EXEC sp_execute 1, 49879;  
GO

EXEC sp_execute 1, 48766;
GO

EXEC sp_unprepare 1; 
GO
```
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  

