---
title: Sp_stop_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_stop_job_TSQL
- sp_stop_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_stop_job
ms.assetid: 64b4cc75-99a0-421e-b418-94e37595bbb0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8c5f625b2fa697a305cf6ea96b3ace59f9f5ee0b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843915"
---
# <a name="spstopjob-transact-sql"></a>sp_stop_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Weist den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent an, die Ausführung des Auftrags zu beenden.  

  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_stop_job   
      [@job_name =] 'job_name'  
    | [@job_id =] job_id   
    | [@originating_server =] 'master_server'  
    | [@server_name =] 'target_server'  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@job_name =**] **'***job_name***'**  
 Der Name des Auftrags, der beendet werden soll. *Job_name* ist **Sysname**, hat den Standardwert NULL.  
  
 [ **@job_id =**] *job_id*  
 Die ID des Auftrags, der beendet werden soll. *Job_id* ist **Uniqueidentifier**, hat den Standardwert NULL.  
  
 [ **@originating_server =**] **'***master_server***'**  
 Der Name des Masterservers. Wenn angegeben, werden alle Multiserveraufträge beendet. *Master_server* ist **vom Datentyp nvarchar(128)**, hat den Standardwert NULL. Geben Sie diesen Parameter nur, wenn aufgerufen **Sp_stop_job** an einen Zielserver.  
  
> [!NOTE]  
>  Es kann jeweils nur einer der ersten drei Parameter angegeben werden.  
  
 [ **@server_name =**] **'***target_server***'**  
 Der Name des Zielservers, auf dem ein Multiserverauftrag beendet werden soll. *Target_server* ist **vom Datentyp nvarchar(128)**, hat den Standardwert NULL. Geben Sie diesen Parameter nur, wenn aufgerufen **Sp_stop_job** auf einem Masterserver für einen Multiserverauftrag.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_stop_job** sendet ein stoppsignal an die Datenbank. Einige Prozesse können sofort beendet werden, und einige muss einen stabilen Punkt (oder einen Einstiegspunkt für den Codepfad) erreichen, bevor sie unterbrochen werden können. Bei einigen zeitaufwändigen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen, etwa BACKUP, RESTORE oder einigen DBCC-Befehlen, kann es längere Zeit dauern, bis sie abgeschlossen sind. Wenn diese ausgeführt werden, kann es eine Weile dauern, bis der Auftrag abgebrochen wird. Der Abbruch eines Auftrags führt dazu, dass ein entsprechender Eintrag im Auftragsverlauf aufgezeichnet wird.  
  
 Wenn ein Auftrag derzeit, einen Schritt des Typs ausgeführt wird **CmdExec** oder **PowerShell**, wird der Prozess ausgeführt wird (z. B. MyProgram.exe) vorzeitig beendet erzwungen. Ein vorzeitiger Abbruch kann unvorhersehbare Folgen haben, z. B. dass Dateien, die von dem Prozess verwendet wurden, geöffnet bleiben. Folglich **Sp_stop_job** sollte nur in Ausnahmesituationen verwendet werden, wenn der Auftrag Schritte des Typs enthält **CmdExec** oder **PowerShell**.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder der **SQLAgentUserRole** und **SQLAgentReaderRole** können nur die Aufträge, deren Besitzer sie, beenden. Mitglieder der **SQLAgentOperatorRole** können alle lokalen Aufträge einschließlich derjenigen, die von anderen Benutzern gehören beenden. Mitglieder der **Sysadmin** können alle Aufträge von lokalen und Multiserveraufträge beenden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Auftrag `Weekly Sales Data Backup` beendet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_stop_job  
    N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
