---
title: MSSQL_ENG014144 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fcae6ec80f755c762201f030d2a97fac905aa3d8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747144"
---
# <a name="mssqleng014144"></a>MSSQL_ENG014144
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14144|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der '%s'-Abonnent kann nicht gelöscht werden. Für ihn sind Abonnements in der %2!s!-Veröffentlichungsdatenbank vorhanden.|  
  
## <a name="explanation"></a>Erklärung  
 Eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, die als Abonnent konfiguriert ist, kann nicht aus der Rolle des Abonnenten entfernt werden, so lange für die Instanz aktive Abonnements konfiguriert sind.  
  
## <a name="user-action"></a>Benutzeraktion  
 Löschen Sie alle zugeordneten Abonnements, bevor Sie versuchen, den Abonnentenstatus der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz zu ändern:  
  
1.  Führen Sie [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md) in der Publikationsdatenbank auf dem Verleger aus, um nach Abonnements zu suchen.  
  
2.  Führen Sie [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md) in der Publikationsdatenbank aus, um Abonnements zu löschen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
