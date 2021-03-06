---
title: '@@ROWCOUNT (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@ROWCOUNT_TSQL'
- '@@ROWCOUNT'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@ROWCOUNT function'
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 97a47998-81d9-4331-a244-9eb8b6fe4a56
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3f3919729fc29933d348f8ef0e10d697c5e00646
ms.sourcegitcommit: a94cf79160e22fa8b4bafe3e6e50bb54e20b1bca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805706"
---
# <a name="x40x40rowcount-transact-sql"></a>&#x40;&#x40;ROWCOUNT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die Anzahl der Zeilen zurück, auf die sich die letzte Anweisung ausgewirkt hat. Beträgt die Anzahl der Zeilen mehr als 2 Milliarden, verwenden Sie [ROWCOUNT_BIG](../../t-sql/functions/rowcount-big-transact-sql.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
@@ROWCOUNT  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen können den Wert in @@ROWCOUNT auf folgende Weise festlegen:  
  
-   @@ROWCOUNT wird auf die Anzahl der betroffenen oder gelesenen Zeilen festgelegt. Zeilen werden möglicherweise an den Client gesendet.  
  
-   @@ROWCOUNT wird aus der vorherigen Anweisungsausführung übernommen.  
  
-   @@ROWCOUNT wird auf 0 (null) zurückgesetzt, jedoch ohne den Wert an den Client zurückzugeben.  
  
 Anweisungen, die eine einfache Zuweisung vornehmen, legen den Wert für @@ROWCOUNT stets auf 1 fest. Es werden keine Zeilen an den Client gesendet. Beispiele für diese Anweisungen: SET @*local_variable*, RETURN, READTEXT und SELECT ohne Abfrageanweisungen wie SELECT GETDATE() oder SELECT **'***Generic Text***'**.  
  
 Anweisungen, die eine Zuweisung in einer Abfrage vornehmen oder RETURN in einer Abfrage verwenden, legen den Wert für @@ROWCOUNT auf die Anzahl der von der Abfrage betroffenen oder gelesenen Zeilen fest, z. B.: SELECT @*local_variable* = c1 FROM t1.  
  
 DML-Anweisungen (Data Manipulation Language = Datenbearbeitungssprache) legen den Wert für @@ROWCOUNT auf die Anzahl der von der Abfrage betroffenen Zeilen fest und geben diesen Wert an den Client zurück. Die DML-Anweisungen senden möglicherweise keine Zeilen an den Client.  
  
 DECLARE CURSOR und FETCH legen den Wert für @@ROWCOUNT auf 1 fest.  
  
 EXECUTE-Anweisungen behalten die vorherige @@ROWCOUNT-Einstellung bei.  
  
 Mit Anweisungen wie USE, SET \<Option>, DEALLOCATE CURSOR, CLOSE CURSOR, PRINT, RAISERROR, BEGIN TRANSACTION oder COMMIT TRANSACTION wird der ROWCOUNT-Wert auf 0 (null) zurückgesetzt.  
  
 Nativ kompilierte gespeicherte Prozeduren behalten die vorherige @@ROWCOUNT-Einstellung bei. [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen in nativ kompilierten gespeicherten Prozeduren legen die @@ROWCOUNT-Einstellung nicht fest. Weitere Informationen finden Sie unter [Nativ kompilierte gespeicherte Prozeduren](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel führt eine `UPDATE`-Anweisung aus und erkennt mithilfe von `@@ROWCOUNT`, ob Zeilen geändert wurden.  
  
```  
USE AdventureWorks2012;  
GO  
UPDATE HumanResources.Employee   
SET JobTitle = N'Executive'  
WHERE NationalIDNumber = 123456789  
IF @@ROWCOUNT = 0  
PRINT 'Warning: No rows were updated';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [SET ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/statements/set-rowcount-transact-sql.md)  
  
  
