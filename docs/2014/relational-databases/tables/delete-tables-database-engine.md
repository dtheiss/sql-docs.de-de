---
title: Löschen von Tabellen (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- table deletions [SQL Server]
- deleting tables
- removing tables
- dropping tables
ms.assetid: ca6aa3e9-9885-44c3-bafc-aec441fd97ec
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: de80b12cb5fbe72e520c6f6cf53e671cabfa7145
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201170"
---
# <a name="delete-tables-database-engine"></a>Löschen von Tabellen (Datenbank-Engine)
  Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine Tabelle aus der Datenbank in [!INCLUDE[tsql](../../includes/tsql-md.md)]löschen (DROP).  
  
> [!CAUTION]  
>  Das Löschen einer Tabelle muss sorgfältig durchdacht werden. Alle Abfragen, Sichten, benutzerdefinierten Funktionen, gespeicherten Prozeduren und Programme, die auf diese Tabelle verweisen, verlieren durch den Löschvorgang ihre Gültigkeit.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So löschen Sie eine Tabelle mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Sie können keine Tabelle löschen, auf die mit einer FOREIGN KEY-Einschränkung verwiesen wird. Die verweisende FOREIGN KEY-Einschränkung oder die verweisende Tabelle muss zuerst gelöscht werden. Wenn sowohl die verweisende Tabelle als auch die Tabelle mit dem Primärschlüssel in derselben DROP TABLE-Anweisung gelöscht werden, muss die verweisende Tabelle zuerst aufgelistet werden.  
  
-   Wird eine Tabelle gelöscht, werden alle Bindungen von Regeln und Standardwerten zur Tabelle entfernt, und alle der Tabelle zugeordneten Einschränkungen und Trigger werden automatisch gelöscht. Wenn Sie die Tabelle neu erstellen, müssen Sie auch die entsprechenden Regeln und Standardwerte neu binden, die Trigger neu erstellen und alle erforderlichen Einschränkungen hinzufügen.  
  
-   Wenn Sie eine Tabelle löschen, enthält eine `varbinary (max)` Spalte mit dem FILESTREAM-Attribut, alle im Dateisystem gespeicherten Daten werden nicht entfernt werden.  
  
-   DROP TABLE und CREATE TABLE dürfen nicht in der gleichen Tabelle im gleichen Batch ausgeführt werden. Andernfalls tritt möglicherweise ein unerwarteter Fehler auf.  
  
-   Jede Sicht oder gespeicherte Prozedur, die auf die gelöschte Tabelle verweist, muss explizit gelöscht oder bearbeitet werden,, um den Verweis auf die Tabelle zu entfernen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für das Schema, zu dem die Tabelle gehört, die CONTROL-Berechtigung für die Tabelle oder die Mitgliedschaft in der festen Datenbankrolle **db_ddladmin** .  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-table-from-the-database"></a>So entfernen Sie eine Tabelle aus der Datenbank  
  
1.  Wählen Sie im Objekt-Explorer die zu löschende Tabelle aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Tabelle, und wählen Sie im Kontextmenü die Option **Löschen** aus.  
  
3.  In einem Meldungsfeld werden Sie zum Bestätigen des Löschvorgangs aufgefordert. Klicken Sie auf **Ja**.  
  
    > [!NOTE]  
    >  Beim Löschen einer Tabelle werden automatisch alle Beziehungen zu der Tabelle entfernt.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-table-in-query-editor"></a>So löschen Sie eine Tabelle im Abfrage-Editor  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    DROP TABLE dbo.PurchaseOrderDetail;  
  
    ```  
  
 Weitere Informationen finden Sie unter [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql).  
  
  