---
title: sys.dm_pdw_component_health_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 602b8ed0c338ba85c35137cd2752fa4357bf63ce
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014061"
---
# <a name="sysdmpdwcomponenthealthstatus-transact-sql"></a>sys.dm_pdw_component_health_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen über den aktuellen Status der Komponenten der Appliance.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||Nicht NULL|  
|component_id|ssNoversion|Die ID der Komponente. Finden Sie unter [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> Pdw_node_id, Component_id, Property_id und Component_instance_id bilden den Schlüssel für diese Ansicht ein.|Nicht NULL|  
|property_id|**int**|Die ID der Eigenschaft. Finden Sie unter [sys.pdw_health_component_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md).|NOT NULL|  
|component_instance_id|**nvarchar(255)**|Identifiziert eine Instanz einer Komponente. Beispielsweise kann eine Instanz einer CPU identifiziert werden, indem Component_instance_id = 'CPU 1'.<br /><br /> Pdw_node_id, Component_id, Property_id und Component_instance_id bilden den Schlüssel für diese Ansicht ein.|NOT NULL|  
|property_value|**nvarchar(255)**|Der aktuelle Eigenschaftswert.|NULL|  
|update_time|**datetime**|Zeitpunkt der letzten die Metrik Aktualisierung.|NOT NULL|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
