---
title: "' sp_adjustpublisheridentityrange ' aus (Transact-SQL) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adjustpublisheridentityrange_TSQL
- sp_adjustpublisheridentityrange
helpviewer_keywords:
- sp_adjustpublisheridentityrange
ms.assetid: 64f111fd-fb7d-4459-93f7-65f0f8dd7efe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 508eaa25657393dba0d84e0bda6eb0582b3f90fb
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52822074"
---
# <a name="spadjustpublisheridentityrange-transact-sql"></a>sp_adjustpublisheridentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Passt den Identitätsbereich für eine Veröffentlichung an und ordnet neue Bereiche auf der Grundlage des Schwellenwerts für die Veröffentlichung neu zu. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_adjustpublisheridentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @table_name = ] 'table_name' ]  
    [ , [ @table_owner= ] 'table_owner' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung, in der neue Identitätsbereiche erneut zugeordnet werden. *Veröffentlichung* ist **Sysname**, hat den Standardwert NULL.  
  
 [ **@table_name=**] **'***table_name***'**  
 Der Name der Tabelle, in der neue Identitätsbereiche erneut zugeordnet werden. *TABLE_NAME* ist **Sysname**, hat den Standardwert NULL.  
  
 [ **@table_owner=**] **'***table_owner***'**  
 Der Besitzer der Tabelle beim Verleger. *Table_owner* ist **Sysname**, hat den Standardwert NULL. Wenn *Table_owner* nicht angegeben ist, wird der Name des aktuellen Benutzers verwendet.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_adjustpublisheridentityrange** wird in allen Replikationstypen verwendet.  
  
 Für eine Veröffentlichung mit aktiviertem automatischem Identitätsbereich ist der Verteilungs- oder Merge-Agent für die automatische Anpassung des Identitätsbereichs in einer Veröffentlichung auf der Basis des Schwellenwerts verantwortlich. Wenn aus irgendeinem Grund Verteilungs-Agent oder Merge-Agent nicht für eine bestimmte Zeitspanne ausgeführt wurde und Identitätsbereichsressource verbraucht wurde bis zum Zeitpunkt des Schwellenwerts, Benutzer können jedoch aufrufen **Sp_adjustpublisheridentityrange** Um einen neuen Bereich von Werten für einen Verleger zuzuordnen.  
  
 Beim Ausführen **Sp_adjustpublisheridentityrange**, entweder *Veröffentlichung* oder *Table_name* muss angegeben werden. Wenn beide oder keiner der Parameter angegeben wird, wird ein Fehler zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** festen Serverrolle oder **Db_owner** feste Datenbankrolle können ausführen **Sp_adjustpublisheridentityrange**.  
  
## <a name="see-also"></a>Siehe auch  
 [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
