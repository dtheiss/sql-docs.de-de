---
title: Sys. database_connection_stats (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.database_connection_stats
- database_connection_stats
- database_connection_stats_TSQL
- sys.database_connection_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_connection_stats
- database_connection_stats
ms.assetid: 5c8cece0-63b0-4dee-8db7-6b43d94027ec
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 9d9e6f23d9e73295f34f23777c76253d27671ed8
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56012361"
---
# <a name="sysdatabaseconnectionstats-azure-sql-database"></a>sys.database_connection_stats (Azure SQL-Datenbank)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Enthält Statistiken für [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Datenbank **Konnektivität** Ereignisse, und eine Übersicht über Datenbank erfolgreichen und fehlgeschlagenen Datenbankverbindungen. Weitere Informationen zu konnektivitätsereignissen finden Sie unter Ereignistypen in [Sys. event_log &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md).  
  
|Statistik|Typ|Description|  
|---------------|----------|-----------------|  
|**database_name**|**sysname**|Der Name der Datenbank.|  
|**start_time**|**datetime2**|UTC-Datum und -Zeit des Beginns des Aggregationsintervalls. Die Uhrzeit ist immer ein Vielfaches von 5 Minuten. Zum Beispiel:<br /><br /> '2011-09-28 16:00:00'<br />'2011-09-28 16:05:00'<br />'2011-09-28 16:10:00'|  
|**end_time**|**datetime2**|UTC-Datum und -Zeit des Endes des Aggregationsintervalls. **End_time** liegt immer genau 5 Minuten später als die entsprechende **Start_time** in derselben Zeile.|  
|**success_count**|**int**|Anzahl erfolgreicher Verbindungen.|  
|**total_failure_count**|**int**|Gesamtzahl fehlerhafter Verbindungen. Dies ist die Summe der **Connection_failure_count**, **Terminated_connection_count**, und **Throttled_connection_count**, und schließt keine Deadlockereignisse.|  
|**connection_failure_count**|**int**|Anzahl der Anmeldefehler.|  
|**terminated_connection_count**|**int**|**_Gilt nur für [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] v11._**<br /><br /> Anzahl beendeter Verbindungen.|  
|**throttled_connection_count**|**int**|**_Gilt nur für [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] v11._**<br /><br /> Anzahl gedrosselter Verbindungen.|  
  
## <a name="remarks"></a>Hinweise  
  
### <a name="event-aggregation"></a>Ereignisaggregation

 Die Ereignisinformationen für diese Sicht werden gesammelt und innerhalb von 5-minütigen Intervallen aggregiert. Die Anzahlspalten stellen die Häufigkeit dar, mit der ein bestimmtes Konnektivitätsereignis für eine bestimmte Datenbank innerhalb eines angegebenen Zeitintervalls aufgetreten ist.  
  
 Wenn ein Benutzer beispielsweise am 05.02.2012 zwischen 11:00 und 11:05 Uhr (UTC) sieben Mal eine Verbindung mit der Datenbank „Database1“ herstellt, sind diese Informationen in dieser Sicht in einer einzelnen Zeile verfügbar:  
  
|**database_name**|**start_time**|**end_time**|**success_count**|**total_failure_count**|**connection_failure_count**|**terminated_connection_count**|**throttled_connection_count**|  
|------------------------|---------------------|-------------------|------------------------|-------------------------------|------------------------------------|---------------------------------------|--------------------------------------|  
|`Database1`|`2012-02-05 11:00:00`|`2012-02-05 11:05:00`|`0`|`7`|`7`|`0`|`0`|  
  
### <a name="interval-starttime-and-endtime"></a>start_time und end_time des Intervalls

 Ein Ereignis wird in ein aggregationsintervall eingefügt, wenn das Ereignis tritt auf, *auf* oder _nach_**Start_time** und _vor_  **End_time** für dieses Intervall. Beispielsweise würde ein Ereignis, das genau zum Zeitpunkt `2012-10-30 19:25:00.0000000` eintritt, nur im zweiten unten gezeigten Intervall aufgenommen werden:  
  
```  
  
start_time                    end_time  
2012-10-30 19:20:00.0000000   2012-10-30 19:25:00.0000000  
2012-10-30 19:25:00.0000000   2012-10-30 19:30:00.0000000  
```  
  
### <a name="data-updates"></a>Datenupdates

 Die Daten in dieser Sicht werden im Zeitverlauf gesammelt. Normalerweise werden die Daten innerhalb einer Stunde nach Beginn des Aggregationsintervalls gesammelt, es kann aber maximal 24 Stunden dauern, bis alle Daten in der Sicht angezeigt werden. Während dieser Zeit werden die Informationen in einer einzelnen Zeile möglicherweise gelegentlich aktualisiert.  
  
### <a name="data-retention"></a>Datenbeibehaltung

 Die Daten in dieser Ansicht werden beibehalten, für bis zu 30 Tage oder kürzer abhängig von der Anzahl der Datenbanken und die Anzahl der eindeutigen Ereignisse, die jede Datenbank generiert. Um diese Informationen für einen längeren Zeitraum beizubehalten, kopieren Sie die Daten in eine separate Datenbank. Nachdem Sie eine erste Kopie der Sicht erstellt haben, werden die Zeilen in der Sicht möglicherweise aktualisiert, während die Daten gesammelt werden. Damit die Kopie der Daten aktuell bleibt, führen Sie regelmäßig einen Tabellenscan der Zeilen aus, um nach einer Erhöhung der Ereignisanzahl für vorhandene Zeilen zu suchen und um neue Zeilen zu ermitteln (eindeutige Zeilen bestimmen Sie anhand der Start- und Endzeiten). Aktualisieren Sie dann die Kopie der Daten mit diesen Änderungen.  
  
### <a name="errors-not-included"></a>Fehler nicht enthalten

 Diese Sicht enthält möglicherweise nicht alle Verbindungs- und Fehlerinformationen:  
  
- In dieser Ansicht enthält nicht alle [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Datenbank Fehler auf, die auftreten können, sondern nur die unter den Ereignistypen in [Sys. event_log &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md).  
  
- Es ist ein Computerfehler innerhalb der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Datacenter, ist eine kleine Menge Daten möglicherweise in der Ereignistabelle fehlt.  
  
- Wenn eine IP-Adresse von DoSGuard blockiert wurde, können Verbindungsversuchsereignisse von dieser IP-Adresse nicht gesammelt werden. Diese werden in dieser Sicht nicht angezeigt.  
  
## <a name="permissions"></a>Berechtigungen

 Benutzer mit Berechtigung zum Zugriff auf die **master** Datenbank haben schreibgeschützten Zugriff auf diese Sicht.  
  
## <a name="example"></a>Beispiel

 Das folgende Beispiel zeigt eine Abfrage der **Sys. database_connection_stats** eine Zusammenfassung der Datenbankverbindungen zurückgegeben, die zwischen Mittag für 9/25/2011 und Mittag für 9/28/2011 (UTC) eingetreten sind. Standardmäßig werden die Ergebnisse der Abfrage nach sortiert **Start_time** (aufsteigende Reihenfolge).  
  
```sql
SELECT *  
FROM sys.database_connection_stats
WHERE start_time>='2011-09-25:12:00:00' and end_time<='2011-09-28 12:00:00';  
```  

## <a name="see-also"></a>Siehe auch

 [Problembehandlung bei Windows Azure SQL-Datenbank](https://msdn.microsoft.com/library/windowsazure/ee730906.aspx)  
  
  
