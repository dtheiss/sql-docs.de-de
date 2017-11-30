---
title: Sys. function_order_columns (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- function_order_columns
- sys.function_order_columns_TSQL
- function_order_columns_TSQL
- sys.function_order_columns
dev_langs: TSQL
helpviewer_keywords: sys.function_order_columns catalog view
ms.assetid: 29287973-3125-4d35-8ca9-92cb45828854
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 151d91a53092b9303f576d5b650abdc71a797039
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="sysfunctionordercolumns-transact-sql"></a>sys.function_order_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile pro Spalte zurück, die Teil eines **ORDER** -Ausdrucks einer CLR-Tabellenwertfunktion (Common Language Runtime) ist.  

  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID des Objekts (CLR-Tabellenwertfunktion), das die Reihenfolge definiert.|  
|**order_column_id**|**int**|Die ID der Sortierspalte. **order_column_id** ist nur innerhalb von **object_id**eindeutig.<br /><br /> **order_column_id** stellt die Position dieser Spalte in der Sortierung dar.|  
|**column_id**|**int**|ID der Spalte in **object_id**.<br /><br /> **column_id** ist nur innerhalb von **object_id**eindeutig.|  
|**is_descending wurde**|**bit**|1 = Die Sortierspalte hat eine absteigende Sortierreihenfolge.<br /><br /> 0 = Die Sortierspalte hat eine aufsteigende Sortierreihenfolge.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  