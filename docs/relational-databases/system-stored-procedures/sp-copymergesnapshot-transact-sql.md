---
title: Sp_copymergesnapshot (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copymergesnapshot
- sp_copymergesnapshot_TSQL
helpviewer_keywords:
- sp_copymergesnapshot
ms.assetid: eaecd6e0-8486-4e5d-ace7-8ae75768c0a8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f308f86de68c672a64f78da0a6b1bd54cde82a2b
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54133800"
---
# <a name="spcopymergesnapshot-transact-sql"></a>sp_copymergesnapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Kopiert den momentaufnahmeordner der angegebenen Veröffentlichung in den Ordner aufgeführt, die der **@destination_folde** _r_. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_copymergesnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder'  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=**] **"**_Veröffentlichung_**"**  
 Der Name der Veröffentlichung, deren Momentaufnahmeinhalt kopiert werden soll. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@destination_folder=**] **"**_Destination_folder_**"**  
 Der Name des Ordners, in den der Inhalt der Veröffentlichungsmomentaufnahme kopiert werden soll. *Destination_folder*ist **nvarchar(255)**, hat keinen Standardwert. Die *Destination_folder* kann ein anderen Speicherort wie z. B. auf einem anderen Server, auf einem Netzlaufwerk oder auf Wechselmedien (z. B. CD-ROMs oder Wechseldatenträger) sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_copymergesnapshot** wird bei der Mergereplikation verwendet. Abonnenten, auf denen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 und früher kann nicht am alternativen momentaufnahmespeicherort verwenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_copymergesnapshot**.  
  
## <a name="see-also"></a>Siehe auch  
 [Alternative Speicherorte für Momentaufnahmeordner](../../relational-databases/replication/snapshot-options.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
