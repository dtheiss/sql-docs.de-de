---
title: Sp_fulltext_keymappings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_keymappings_TSQL
- sp_fulltext_keymappings
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], key column
- sp_fulltext_keymappings
- full-text indexes [SQL Server], troubleshooting
ms.assetid: 2818fa42-072d-4664-a2f7-7ec363b51d81
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0e9f8894376712472c13479a32503954ad2694d7
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52506320"
---
# <a name="spfulltextkeymappings-transact-sql"></a>sp_fulltext_keymappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Gibt Zuordnungen zwischen Dokumentbezeichnern (DocIds) und Volltextschlüsselwerten zurück. Die DocId-Spalte enthält Werte für eine **Bigint** Zahl, die einen bestimmten Volltext-Schlüssel-Wert in einer volltextindizierten Tabelle zugeordnet. DocId-Werte, die eine Suchbedingung erfüllen, werden von der Volltext-Engine an die Datenbank-Engine übergeben. Dort werden sie Volltextschlüsselwerten aus der abgefragten Basistabelle zugeordnet. Die Volltextschlüsselspalte ist ein eindeutiger Index, der in einer Spalte der Tabelle erforderlich ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_fulltext_keymappings { table_id | table_id, docid | table_id, NULL, key }  
```  
  
#### <a name="parameters"></a>Parameter  
 *table_id*  
 Ist die Objekt-ID der volltextindizierten Tabelle. Wenn Sie angeben, dass eine ungültige *Table_id*, wird ein Fehler zurückgegeben. Informationen zum Abrufen der ObjectID einer Tabelle finden Sie unter [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md).  
  
 *docid*  
 Ein interner Dokumentbezeichner (DocId), der dem Schlüsselwert entspricht. Ein ungültiger *docid* -Wert gibt keine Ergebnisse zurück.  
  
 *key*  
 Der Wert des Volltextschlüssels aus der angegebenen Tabelle. Ein ungültiger *key* -Wert gibt keine Ergebnisse zurück. Informationen zum Volltext-Schlüsselwerte, finden Sie unter [Verwalten von Volltextindizes](https://msdn.microsoft.com/library/28ff17dc-172b-4ac4-853f-990b5dc02fd1).  
  
> [!IMPORTANT]  
>  Informationen zur Verwendung von einem, zwei oder drei Parametern finden Sie unter "Hinweise" später in diesem Thema.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|DocId|**bigint**|Eine interne Dokumentbezeichnerspalte (DocId), die dem Schlüsselwert entspricht.|  
|Key|*|Der Wert des Volltextschlüssels aus der angegebenen Tabelle.<br /><br /> Wenn in der Zuordnungstabelle keine Volltextschlüssel vorhanden sind, wird ein leeres Rowset zurückgegeben.|  
  
 <sup>*</sup> Der Datentyp für Key ist identisch mit dem Datentyp der Volltext-Schlüsselspalte in der Basistabelle.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Funktion ist öffentlich und erfordert keine besonderen Berechtigungen.  
  
## <a name="remarks"></a>Hinweise  
 In der folgenden Tabelle sind die Auswirkungen beschrieben, die sich ergeben, wenn ein, zwei oder drei Parameter verwendet werden.  
  
|Diese Parameterliste...|Hat dieses Ergebnis...|  
|--------------------------|----------------------|  
|*table_id*|Wenn Sie mit nur aufgerufen, die *Table_id* Parameter Sp_fulltext_keymappings gibt alle Werte der Volltextschlüssel (Key) aus der angegebenen Basistabelle sowie die DocId, die jedem Schlüssel entspricht. Dies schließt auch Schlüssel mit ein, für die ein Löschvorgang aussteht.<br /><br /> Diese Funktion ist hilfreich zur Behebung zahlreicher Probleme. Insbesondere bietet sie sich zum Anzeigen des Inhalts des Volltextindex an, wenn der ausgewählte Volltextschlüssel keinen ganzzahligen Datentyp aufweist. Dies schließt den Join der Ergebnisse von Sp_fulltext_keymappings mit den Ergebnissen der **dm_fts_index_keywords_by_document**. Weitere Informationen finden Sie unter [dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md).<br /><br /> Im Allgemeinen sollten Sie jedoch , falls möglich, sp_fulltext_keymappings mit Parametern ausführen, die einen bestimmten Volltextschlüssel oder DocId angeben. Dies ist erheblich effizienter als eine gesamte Schlüsselzuordnung zurückzugeben, insbesondere für eine sehr große Tabelle, für die die Leistungskosten der Rückgabe der gesamten Schlüsselzuordnung erheblich sein könnten.|  
|*table_id*, *docid*|Wenn nur die *Table_id* und *Docid* angegeben sind, *Docid* nicht NULL sein müssen, und geben Sie eine gültige DocId in der angegebenen Tabelle. Diese Funktion ist hilfreich, um den benutzerdefinierten Volltextschlüssel aus der Basistabelle zu isolieren, die der DocId eines bestimmten Volltextindex entspricht.|  
|*Table_id*, NULL, *Schlüssel*|Wenn drei Parameter vorhanden sind, muss der zweite Parameter NULL sein und *Schlüssel* nicht NULL sein müssen, und geben Sie einen gültigen Volltext-Schlüsselwert aus der angegebenen Tabelle. Diese Funktion ist hilfreich, um die DocID zu isolieren, die einem bestimmten Volltextschlüssel aus der Basistabelle entspricht.|  
  
 Wenn eine der folgenden Bedingungen zutrifft, wird ein Fehler zurückgegeben:  
  
-   Sie geben eine ungültige *Table_id*.  
  
-   Die Tabelle ist nicht volltextindiziert.  
  
-   NULL tritt für einen Parameter auf, der möglicherweise ungleich NULL ist  
  
## <a name="examples"></a>Beispiele  
  
> [!NOTE]  
>  Die Beispiele in diesem Abschnitt verwenden die `Production.ProductReview` -Tabelle der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] -Beispieldatenbank. Sie können diesen Index erstellen, durch Ausführen der im Beispiel für die `ProductReview` -Tabelle [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
### <a name="a-obtaining-all-the-key-and-docid-values"></a>A. Abrufen aller Schlüssel- und DocId-Werte  
 Im folgenden Beispiel wird eine [DECLARE](../../t-sql/language-elements/declare-local-variable-transact-sql.md) Anweisung, um eine lokale Variable `@table_id` und die ID des Zuweisen der `ProductReview` -Tabelle als Wert. Das Beispiel führt **Sp_fulltext_keymappings** angeben `@table_id` für die *Table_id* Parameter.  
  
> [!NOTE]  
>  Mithilfe von **Sp_fulltext_keymappings** nur mit der *Table_id* Parameter ist für kleine Tabellen geeignet.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @table_id int = OBJECT_ID(N'Production.ProductReview');  
EXEC sp_fulltext_keymappings @table_id;  
GO  
  
```  
  
 In diesem Beispiel werden alle DocIds und Volltextschlüssel folgendermaßen von der Tabelle zurückgegeben:  
  
||||  
|-|-|-|  
||`docid`|`key`|  
|`1`|`1`|`1`|  
|`2`|`2`|`2`|  
|`3`|`3`|`3`|  
|`4`|`4`|`4`|  
  
### <a name="b-obtaining-the-docid-value-for-a-specific-key-value"></a>B. Abrufen des DocId-Werts für einen bestimmten Schlüsselwert  
 Im folgenden Beispiel wird eine DECLARE-Anweisung verwendet, um die lokale Variable `@table_id`zu erstellen und ihr die ID der `ProductReview` -Tabelle als Wert zuzuweisen. Das Beispiel führt **Sp_fulltext_keymappings** angeben `@table_id` für die *Table_id* Parameter, NULL für den *Docid* Parameter, und 4 für die *Schlüssel* Parameter.  
  
> [!NOTE]  
>  Mithilfe von **Sp_fulltext_keymappings** nur mit der *Table_id* -Parameter ist für kleine Tabellen.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @table_id int = OBJECT_ID(N'Production.ProductReview');  
EXEC sp_fulltext_keymappings @table_id, NULL, 4;  
GO  
  
```  
  
 Dieses Beispiel gibt die folgenden Ergebnisse zurück:  
  
||||  
|-|-|-|  
||`docid`|`key`|  
|`4`|`4`|`4`|  
  
## <a name="see-also"></a>Siehe auch  
 [Volltextsuche und semantische Suche von gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
