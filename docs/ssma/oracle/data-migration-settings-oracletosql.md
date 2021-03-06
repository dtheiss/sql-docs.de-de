---
title: Data Migration Settings (OracleToSQL) Einstellungen | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 91f7f558-025d-4f4d-ac2c-aa095e7d1ace
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 96b60573b81625c8896fb9022a6a718770f349ed
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656137"
---
# <a name="data-migration-settings-oracletosql"></a>Einstellungen für die Datenmigration (OracleToSQL)
  
## <a name="data-migration-settings"></a>Einstellungen für die Datenmigration  
**Data Migration Settings** ermöglicht dem Benutzer, benutzerdefinierte Abfragen für die Datenmigration zu schreiben.  
  
-   Diese Registerkarte ist verfügbar, wenn **erweiterte Optionen für die Migration von Daten** nastaven NA hodnotu **anzeigen** und wird ausgeblendet, wenn die Einstellung, um festgelegt ist **ausblenden** in den Projekteinstellungen. Weitere Informationen zu Projekteinstellungen für die Migration, finden Sie unter [Project Settings (Migration)](https://msdn.microsoft.com/fcd6b988-633b-4b2b-9f36-6368b5e86b60) .  
  
-   Analysieren von benutzerdefinierten SQL-Anweisungen in implementiert **Data Migration Settings** Registerkarte der Tabelle.  
  
-   Es folgen die beiden Kontrollkästchen in verfügbaren der **Data Migration Settings** viz.:  
  
    1.  Abschneiden von SQL Server-Tabelle  
  
    2.  Verwenden Sie benutzerdefinierte auswählen  
  
1.  **Abschneiden von SQL Server-Tabelle:**  
     Hiermit kann die Benutzer ein klares Bild der migrierten Daten an die Zieldatenbank verfügen.  
  
    -   Standardmäßig wird dieses Textfeld überprüft.  
  
    -   Wenn dieses Textfeld deaktiviert ist, werden die Daten, die migriert werden an die vorhandenen Daten auf der Zieldatenbank hinzugefügt werden.  
  
2.  **Verwenden Sie benutzerdefinierte auswählen:**  
     Diese Option ermöglicht dem Benutzer zum Ändern der **wählen** Anweisung vorhanden (**wählen** -Anweisung können die Benutzer zur Auswahl der Daten, das an die Zieldatenbank angezeigt werden).  
  
    1.  In der Standardeinstellung ist deaktiviert dieses Textfeld.  
  
    2.  Wenn dieses Textfeld wird überprüft, es ermöglicht Benutzern das Ändern der **wählen** Anweisung vorhanden.  
  
Es befinden sich zwei Schaltflächen, die vorhanden viz.:  
  
-   **Anwenden:** klicken Sie auf **übernehmen** zum Anwenden der Einstellungen, die geändert wurden.  
  
-   **Abbrechen:** klicken Sie auf **Abbrechen** vorhanden wiederhergestellt, bevor die Änderungen durchgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Oracle-Daten in SQLServer](migrating-oracle-data-into-sql-server-oracletosql.md)  
  
