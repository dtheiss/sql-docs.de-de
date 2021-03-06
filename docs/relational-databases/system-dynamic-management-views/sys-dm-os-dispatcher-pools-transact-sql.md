---
title: Sys.dm_os_dispatcher_pools (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_dispatcher_pools_TSQL
- dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], views
- sys.dm_os_dispatcher_pools DMV
ms.assetid: b9edbc83-c6bc-4753-9bb5-a454cfe7d6bf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a7a03063ad61c380f72e9a52b71f268b06d822d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756508"
---
# <a name="sysdmosdispatcherpools-transact-sql"></a>sys.dm_os_dispatcher_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu Sitzungsverteilerpools zurück. Verteilerpools sind von Systemkomponenten verwendete Threadpools für die Hintergrundverarbeitung.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_os_dispatcher_pools**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|dispatcher_pool_address|**varbinary(8)**|Die Adresse des Verteilerpools. Dispatcher_pool_address ist eindeutig. Lässt keine NULL-Werte zu.|  
|Typ|**nvarchar(256)**|Der Typ des Verteilerpools. Lässt keine NULL-Werte zu. Es gibt zwei Typen von Verteilerpools:<br /><br /> DISP_POOL_XE_ENGINE<br /><br /> DISP_POOL_XE_SESSION<br /><br /> Die DMV für die vollständige Liste-Abfrage|  
|NAME|**nvarchar(256)**|Der Name des Verteilerpools Lässt keine NULL-Werte zu.|  
|dispatcher_count|**int**|Die Anzahl aktiver Verteilerthreads Lässt keine NULL-Werte zu.|  
|dispatcher_ideal_count|**int**|Die Anzahl zu verwendender Verteilerthreads, die der Verteilerpool erhöhen kann. Lässt keine NULL-Werte zu.|  
|dispatcher_timeout_ms|**int**|Die Zeit in Millisekunden, die ein Verteiler auf neue Arbeit wartet, bevor er beendet wird. Lässt keine NULL-Werte zu.|  
|dispatcher_waiting_count|**int**|Die Anzahl von Verteilerthreads im Leerlauf. Lässt keine NULL-Werte zu.|  
|queue_length|**int**|Die Anzahl von Arbeitselementen, die auf die Verarbeitung durch den Verteilerpool warten. Lässt keine NULL-Werte zu.|  
|pdw_node_id|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   

## <a name="see-also"></a>Siehe auch  
  
  


