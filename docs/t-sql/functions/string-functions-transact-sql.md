---
title: Zeichenfolgenfunktionen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/15/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], strings
- strings [SQL Server], functions
- string functions
- strings [SQL Server]
ms.assetid: 6940a83d-5374-4af3-bb27-5d89c8af83ac
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 34cb5a8bb16e86215217263f956e5d8111c56785
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54299997"
---
# <a name="string-functions-transact-sql"></a>Zeichenfolgenfunktionen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

> [!div class="nextstepaction"]
> [Senden Sie uns Ihr Feedback zum Inhaltsverzeichnis der SQL-Dokumentation!](https://aka.ms/sqldocsurvey)


Die folgenden Skalarfunktionen verarbeiten Zeichenfolgen-Eingabewerte und geben einen numerischen Wert oder eine Zeichenfolge zurück:  
  
||||  
|-|-|-| 
|[ASCII](../../t-sql/functions/ascii-transact-sql.md)|[CHAR](../../t-sql/functions/char-transact-sql.md)|[CHARINDEX](../../t-sql/functions/charindex-transact-sql.md)|
|[CONCAT](../../t-sql/functions/concat-transact-sql.md)|[CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md)|[DIFFERENCE](../../t-sql/functions/difference-transact-sql.md) |
|[FORMAT](../../t-sql/functions/format-transact-sql.md)|[LEFT](../../t-sql/functions/left-transact-sql.md)|[LEN](../../t-sql/functions/len-transact-sql.md) |
|[LOWER](../../t-sql/functions/lower-transact-sql.md)|[LTRIM](../../t-sql/functions/ltrim-transact-sql.md)|[NCHAR](../../t-sql/functions/nchar-transact-sql.md) |
|[PATINDEX](../../t-sql/functions/patindex-transact-sql.md)|[QUOTENAME](../../t-sql/functions/quotename-transact-sql.md)|[REPLACE](../../t-sql/functions/replace-transact-sql.md) |
|[REPLICATE](../../t-sql/functions/replicate-transact-sql.md)|[REVERSE](../../t-sql/functions/reverse-transact-sql.md) |[RIGHT](../../t-sql/functions/right-transact-sql.md) |
|[RTRIM](../../t-sql/functions/rtrim-transact-sql.md)|[SOUNDEX](../../t-sql/functions/soundex-transact-sql.md) |[SPACE](../../t-sql/functions/space-transact-sql.md) |
|[STR](../../t-sql/functions/str-transact-sql.md)|[STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md)|[STRING_ESCAPE](../../t-sql/functions/string-escape-transact-sql.md) |
|[STRING_SPLIT](../../t-sql/functions/string-split-transact-sql.md)|[STUFF](../../t-sql/functions/stuff-transact-sql.md)|[SUBSTRING](../../t-sql/functions/substring-transact-sql.md) |
|[TRANSLATE](../../t-sql/functions/translate-transact-sql.md)|[TRIM](../../t-sql/functions/trim-transact-sql.md)|[UNICODE](../../t-sql/functions/unicode-transact-sql.md) |
|[UPPER](../../t-sql/functions/upper-transact-sql.md) | | |


  
 Alle integrierten Zeichenfolgenfunktionen außer `FORMAT` sind deterministisch. Das bedeutet, dass sie stets denselben Wert zurückgeben, wenn sie mit bestimmten Eingabewerten aufgerufen werden. Weitere Informationen zu Funktionsdeterminismus finden Sie unter [Deterministische und nicht deterministische Funktionen](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
 Wenn an Zeichenfolgenfunktionen Argumente übergeben werden, die keine Zeichenfolgenwerte sind, wird der Eingabetyp implizit in einen Textdatentyp konvertiert. Weitere Informationen finden Sie unter [Datentypkonvertierung &#40;Datenbank-Engine&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integrierte Funktionen &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  

