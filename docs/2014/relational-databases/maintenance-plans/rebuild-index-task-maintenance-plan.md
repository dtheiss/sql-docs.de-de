---
title: Task 'Index neu erstellen' (Wartungsplan) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reindex.f1
- reindex
helpviewer_keywords:
- Rebuild Index Task dialog box
ms.assetid: 33e2940b-139f-4563-b0cb-5683f08bd879
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34bd5a607998c6e37f688ccbadcd4d612d3daea7
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52818212"
---
# <a name="rebuild-index-task-maintenance-plan"></a>Task 'Index neu erstellen' (Wartungsplan)
  Mithilfe des Dialogfelds **Task „Index neu erstellen“** können Sie Indizes für Tabellen in der Datenbank mit einem neuen Füllfaktor neu erstellen. Der Füllfaktor bestimmt die Menge an leeren Speicherplatz auf jeder Seite im Index, der Platz für zukünftige Erweiterungen bieten soll. Wenn der Tabelle Daten hinzugefügt werden, wird der freie Speicherplatz aufgefüllt, da der Wert für den Füllfaktor nicht beibehalten wird. Der freie Speicherplatz kann durch Neuorganisieren der Daten- und Indexseiten wiederhergestellt werden.  
  
 **Task „Index neu erstellen“** verwendet die ALTER INDEX-Anweisung.  
  
## <a name="options"></a>Optionen  
 **Verbindung**  
 Wählen Sie die Serververbindung aus, die bei der Ausführung dieses Tasks verwendet werden soll.  
  
 **Neu**  
 Erstellen Sie eine neue Serververbindung, die bei der Ausführung dieses Tasks verwendet werden soll. Das Dialogfeld **Neue Verbindung** wird im Folgenden beschrieben.  
  
 **Datenbanken**  
 Gibt die Datenbanken an, die von dieser Aufgabe betroffen sind.  
  
-   **Alle Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken außer tempdb ausführt.  
  
-   **Alle Systemdatenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemdatenbanken außer tempdb ausführt. Für benutzerdefinierte Datenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Alle Benutzerdatenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle benutzerdefinierten Datenbanken ausführt. Für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemdatenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Diese Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks nur für die ausgewählten Datenbanken ausführt. Wenn diese Option ausgewählt wird, muss mindestens eine Datenbank in der Liste ausgewählt werden.  
  
    > [!NOTE]  
    >  Wartungspläne werden nur für Datenbanken mit Kompatibilitätsgrad 80 oder höher ausgeführt. Datenbanken mit Kompatibilitätsgrad 70 oder niedriger werden nicht angezeigt.  
  
 **Objekt**  
 Begrenzt das Raster **Auswahl** auf die Anzeige von Tabellen, Sichten oder beides.  
  
 **Auswahl**  
 Gibt die Tabellen oder Indizes an, auf die sich dieser Task auswirkt. Nicht verfügbar, wenn im Objektfeld der Eintrag **Tabellen und Sichten** ausgewählt ist.  
  
 **Organisieren Sie Seiten mit der standardmäßigen freien Speicherplatzmenge neu**  
 Löscht die Indizes für die Tabellen in der Datenbank und erstellt sie mit dem Füllfaktor, der beim Erstellen der Indizes angegeben wurde, neu.  
  
 **Freien Speicherplatz pro Seite Prozentsatz zu ändern**  
 Löscht die Indizes für die Tabellen in der Datenbank und erstellt sie mit einem neuen, automatisch berechneten Füllfaktor neu. Auf diese Weise wird der angegebene freie Speicherplatz auf den Indexseiten reserviert. Ein höherer Prozentsatz bedeutet, dass mehr freier Speicherplatz auf den Indexseiten reserviert wird und der Index entsprechend wachsen kann. Die gültigen Werte sind 0 bis 100.  
  
 **Ergebnisse in 'tempdb' sortieren**  
 Verwenden der `SORT_IN_TEMPDB`Option fest, wo die während der indexerstellung generierten Zwischenergebnisse des Sortierens Ergebnisse vorübergehend gespeichert werden. Wenn ein Sortiervorgang nicht erforderlich ist oder im Arbeitsspeicher ausgeführt werden kann, wird die Option `SORT_IN_TEMPDB`ignoriert.  
  
 **Behalten Sie Index online während neuindizierung**  
 Die Option `ONLINE` ermöglicht es Benutzern, während Indexvorgängen auf die zugrunde liegenden Tabellen- bzw. gruppierten Indexdaten und alle zugehörigen nicht gruppierten Indizes zuzugreifen.  
  
> [!NOTE]  
>  Onlineindexvorgänge sind nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **T-SQL anzeigen**  
 Zeigt die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen an, die für diesen Task auf dem Server auf Basis der ausgewählten Optionen ausgeführt werden.  
  
> [!NOTE]  
>  Wenn die Anzahl der betroffenen Objekte groß ist, kann die Anzeige erhebliche Zeit in Anspruch nehmen.  
  
## <a name="new-connection-dialog-box"></a>Neue Verbindung (Dialogfeld)  
 **Verbindungsname**  
 Geben Sie einen Namen für die neue Verbindung ein.  
  
 **Wählen Sie einen Servernamen aus, oder geben Sie ihn ein.**  
 Wählen Sie den Server aus, zu dem bei der Ausführung dieses Tasks eine Verbindung hergestellt werden soll.  
  
 **Aktualisieren**  
 Mithilfe dieser Option aktualisieren Sie die Liste der verfügbaren Server.  
  
 **Geben Sie Informationen zum Anmelden am Server ein**  
 Legt fest, wie die Authentifizierung gegenüber dem Server stattfindet.  
  
 **Integrierte Sicherheit von Windows NT verwenden**  
 Stellt mithilfe der Windows-Authentifizierung eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] her.  
  
 **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden**  
 Stellt mithilfe der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Authentifizierung eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her. Diese Option ist nicht verfügbar.  
  
 **Benutzername**  
 Stellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
 **Kennwort**  
 Stellt ein Kennwort für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [SORT_IN_TEMPDB-Option für Indizes](../indexes/indexes.md)   
 [Richtlinien für Onlineindexvorgänge](../indexes/guidelines-for-online-index-operations.md)   
 [Funktionsweise von Onlineindexvorgängen](../indexes/how-online-index-operations-work.md)   
 [Ausführen von Onlineindexvorgängen](../indexes/perform-index-operations-online.md)  
  
  
