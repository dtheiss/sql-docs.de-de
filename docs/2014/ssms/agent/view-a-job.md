---
title: Anzeigen eines Auftrags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], viewing
- viewing jobs
- SQL Server Agent jobs, viewing
- displaying jobs
ms.assetid: d2241a3f-dbcf-433c-b7bc-f96bdf0eac8c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a732ccf71e0b52b83ae1fabdef88235595d4c194
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53366432"
---
# <a name="view-a-job"></a>View a Job
  In diesem Thema wird beschrieben, wie Sie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträge in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]anzeigen können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So zeigen Sie einen Auftrag an mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
 Sie können nur die Aufträge anzeigen, die Sie besitzen, es sei denn, Sie sind ein Mitglied der festen Serverrolle **sysadmin** . Mitglieder dieser Rolle können alle Aufträge anzeigen. Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-view-a-job"></a>So zeigen Sie einen Auftrag an  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, und klicken Sie auf **Aufträge**.  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag, und klicken Sie dann auf **Eigenschaften**.  
  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-a-job"></a>So zeigen Sie einen Auftrag an  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- lists all aspects of the information for the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_job  
        @job_name = N'NightlyBackups',  
        @job_aspect = N'ALL' ;  
    GO  
    ```  
  
##  <a name="SMO"></a> Verwendung von SQL Server Management Objects  
 **So zeigen Sie einen Auftrag an**  
  
 Verwenden Sie die `Job`-Klasse in einer von Ihnen ausgewählten Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
  
