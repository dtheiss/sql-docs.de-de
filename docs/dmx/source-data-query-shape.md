---
title: FORM (DMX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHAPE
dev_langs:
- DMX
helpviewer_keywords:
- SHAPE statement
- multiple data sources
ms.assetid: b9526ec2-40bc-4bf5-b4e5-774f71075065
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dcd4940769fc52852b1d48feb453f1393c754084
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="ltsource-data-querygt---shape"></a>&lt;quelldatenabfrage&gt; -Form
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Kombiniert Abfragen aus mehreren Datenquellen in einer hierarchischen Tabelle (eine Tabelle mit geschachtelten Tabellen), die zur Falltabelle für das Miningmodell wird.  
  
 Die vollständige Syntax eines der **Form** Befehl finden Sie der [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Access Components (MDAC) Software Development Kit (SDK).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Argumente  
 *Master-Abfrage*  
 Die Abfrage, die die übergeordnete Tabelle zurückgibt.  
  
 *Abfrage der untergeordneten Tabelle*  
 Die Abfrage, die die geschachtelte Tabelle zurückgibt.  
  
 *Master-Spalte*  
 Die Spalte in der übergeordneten Tabelle, die die untergeordneten Zeilen aus dem Ergebnis einer Abfrage der untergeordneten Tabelle (child table query) kennzeichnet.  
  
 *untergeordnete Spalte*  
 Die Spalte in der untergeordneten Tabelle, die die übergeordneten Zeilen aus dem Ergebnis einer Masterabfrage (master query) kennzeichnet.  
  
 *Spaltenname für die Tabelle*  
 Der neu angefügte Spaltenname in der übergeordneten Tabelle für die geschachtelte Tabelle.  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen die Abfragen nach der Spalte sortieren, die die übergeordnete Tabelle und die untergeordnete Tabelle verknüpft.  
  
## <a name="examples"></a>Beispiele  
 Sie können das folgende Beispiel in einer [INSERT INTO & #40; DMX & #41;](../dmx/insert-into-dmx.md) Anweisung zum Trainieren eines Modells, das eine geschachtelte Tabelle enthält. Die beiden Tabellen in der **Form** Anweisung beziehen sich über die **OrderNumber** Spalte.  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>Siehe auch  
 [& #60; quelldatenabfrage & #62;](../dmx/source-data-query.md)   
 [Datamining-Erweiterungen & #40; DMX & #41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen & #40; DMX & #41; Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Datamining-Erweiterungen & #40; DMX & #41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
