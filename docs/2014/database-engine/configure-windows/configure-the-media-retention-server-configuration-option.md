---
title: Konfigurieren der Serverkonfigurationsoption „Medienbeibehaltung“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- backup retention duration [SQL Server]
- backup sets [SQL Server], retention duration
- media retention option
ms.assetid: 12e9fe6a-20a5-4c6e-9cc9-d500c003b70a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f073c73568a5ef9a48c9157dcb41b46430a5ab84
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52641485"
---
# <a name="configure-the-media-retention-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Medienbeibehaltung
  In diesem Thema wird beschrieben, wie die Serverkonfigurationsoption **Medienbeibehaltung** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert werden kann. Die Option **Medienbeibehaltung** gibt den Zeitraum an, wie lange jeder Sicherungssatz beibehalten werden soll. Mithilfe dieser Option wird verhindert, dass Sicherungen vor Ablauf der angegebenen Anzahl von Tagen überschrieben werden. Nachdem Sie die Option **Medienbeibehaltung** konfiguriert haben, müssen Sie nicht jedes Mal beim Ausführen einer Sicherung den Zeitraum angeben, wie lange die Systemsicherungen beibehalten werden sollen. Der Standardwert ist 0 Tage, und der Maximalwert ist 365 Tage.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Sicherheit](#Security)  
  
-   **So konfigurieren Sie die Option Medienbeibehaltung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option medienbeibehaltung](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn Sie das Sicherungsmedium verwenden, bevor die festgelegte Anzahl von Tagen verstrichen ist, wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Warnmeldung ausgegeben. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird nur dann eine Warnmeldung ausgegeben, wenn Sie die Standardeinstellung ändern.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   Die Option **Medienbeibehaltung** kann außer Kraft gesetzt werden, indem die RETAINDAYS-Klausel der [BACKUP](/sql/t-sql/statements/backup-transact-sql) -Anweisung verwendet wird.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-configure-the-media-retention-option"></a>So konfigurieren Sie die Option Medienbeibehaltung  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den Knoten **Datenbankeinstellungen** .  
  
3.  Geben Sie im Feld **Standardbeibehaltungsdauer für Sicherungsmedien (in Tagen)** unter **Sicherung/Wiederherstellung** einen Wert zwischen 0 und 365 ein, oder wählen Sie einen Wert aus, um in Tagen festzulegen, wie lange das Sicherungsmedium nach dem Sichern einer Datenbank oder eines Transaktionsprotokolls beibehalten werden soll.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-media-retention-option"></a>So konfigurieren Sie die Option Medienbeibehaltung  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `media retention` auf `60` Tage festzulegen.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'media retention', 60 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="FollowUp"></a> Zur Nachverfolgung: Nach dem Konfigurieren der Option medienbeibehaltung  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
