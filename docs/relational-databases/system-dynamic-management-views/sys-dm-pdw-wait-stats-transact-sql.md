---
title: Sys.dm_pdw_wait_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cfb8d905-c34f-44de-9574-dde81e170916
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4bf4c0d15f2a27179d8f88831a940bca1ecb1aea
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020491"
---
# <a name="sysdmpdwwaitstats-transact-sql"></a>sys.dm_pdw_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen, die im Zusammenhang mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Betriebssystemstatus im Zusammenhang mit der Instanzen, die in den anderen Knoten ausgeführt. Eine Liste der Wartevorgänge Typen und die entsprechenden Beschreibungen, finden Sie unter [Sys. dm_os_wait_stats](https://msdn.microsoft.com/library/ms179984\(v=sql.120\).aspx).  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|**pdw_node_id**|**int**|Die ID des Knotens, auf die dieser Eintrag verweist.||  
|**wait_name**|**nvarchar(255)**|Name des Wartetyps.||  
|**max_wait_time**|**bigint**|Maximale Wartezeit von diesen Wartetyp.||  
|**request_count**|**bigint**|Anzahl von Wartevorgängen Dieser Wartetyp ausstehenden.||  
|**signal_time**|**bigint**|Differenz zwischen dem Zeitpunkt der Signalisierung des wartenden Threads und dem Beginn der Ausführung.||  
|**completed_count**|**bigint**|Gesamtanzahl von Wartevorgängen dieses Typs ausgeführt, die seit dem letzten Serverneustart neu starten.||  
|**wait_time**|**bigint**|Gesamtwartezeit für diesen Wartetyp in Millisecons. Inklusive der Signal_time.||  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
  
