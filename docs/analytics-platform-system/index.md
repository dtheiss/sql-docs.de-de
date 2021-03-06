---
title: Dokumentation zu Analytics Platform System | Microsoft-Dokumentation
description: Microsoft Analytics Platform System (APS) ist eine Datenplattform, die für Data Warehousing und Big Data-Analysen entwickelt wurde. Sie bietet nahtlose Datenintegration, schnelle Abfrageverarbeitung, hochgradig skalierbaren Speicher sowie eine unkomplizierte Wartung für End-to-End-Lösungen für Business Intelligence.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ed7ba4a6b5b2f69c51f06a4dbf2947d97981c38f
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52419101"
---
# <a name="microsoft-analytics-platform-system"></a>Microsoft Analytics Platform System  
Microsoft Analytics Platform System (APS) ist eine Datenplattform, die für Data Warehousing und Big Data-Analysen entwickelt wurde. Sie bietet nahtlose Datenintegration, schnelle Abfrageverarbeitung, hochgradig skalierbaren Speicher sowie eine unkomplizierte Wartung für End-to-End-Lösungen für Business Intelligence.  
  
![Appliancearchitektur](media/architecture-high-level.png "appliance architecture")  
  
APS hostet SQL Server Parallel Data Warehouse (PDW). Dabei handelt es sich um eine Software, die ein MPP-Data Warehouse (Massively Parallel Processing) ausführt.  
  
Die PolyBase-Technologie kombiniert relationale PDW-Daten mit Hadoop-Daten aus verschiedenen Quellen, unter anderem Hortonworks unter Windows Server, Hortonworks unter Linux, Cloudera unter Linux und Microsoft Azure Blob Storage von HDInsight. Durch diese erweiterten Datenintegrationsfunktionen und die nahtlose Integration in Business Intelligence-Tools kann Analytics Platform System integrierte Analysen zurückgeben, mit denen Entscheidungsträger Ihres Unternehmens bessere und informiertere Unternehmensentscheidungen treffen können.  
  
Analytics Platform System wird als Appliance mit Hardware und vorinstallierter Software in Ihr Rechenzentrum geliefert, und ist so konfiguriert, dass es mehrere Workloads ausführen kann. Wenn Sie Analytics Platform System erwerben, kaufen Sie auch Computeknoten für PDW entsprechend Ihren Geschäftsanforderungen.  
  
Analytics Platform System ist nicht nur schnell und skalierbar, sondern weist auch eine hohe Redundanz und Hochverfügbarkeit auf. Dies macht es zu einer zuverlässigen Plattform für Ihre unternehmenswichtigen Daten. Analytics Platform System ist auf Einfachheit getrimmt, sodass Sie schnell damit zurecht kommen und es leicht verwalten können. Die PolyBase-Technologie von Parallel Data Warehouse, die zur Analyse von Hadoop-Daten eingesetzt wird, und die nahtlose Integration in Business Intelligence-Tools machen Analytics Platform System zu einer umfangreichen Plattform zum Erstellen von End-to-End-Lösungen.  
  
  
## <a name="parallel-data-warehouse-software-designed-for-massively-parallel-processing"></a>Parallel Data Warehouse: für MPP entwickelt
  
Verwenden Sie Parallel Data Warehouse als Hauptkomponente Ihrer Business Intelligence-End-to-End-Lösung für relationales Data Warehousing. Mit dem MPP-Design von PDW können Abfragen meist 50-mal schneller als traditionelle Data Warehouses abgeschlossen werden, die auf SMP-DBMS aufbauen (Datenbankverwaltungssysteme).  
  
> [!NOTE]  
> Dies bedeutet, dass Abfrage in wenigen Minuten oder wenigen Sekunden, und nicht nach mehreren Stunden oder Minuten abgeschlossen werden. Durch diese revolutionäre Leistung können Ihre Unternehmensanalysten schneller umfangreichere Ergebnisse liefern und ganz leicht Ad-hoc-Abfragen durchführen oder ausführlicher nachforschen. So kann Ihr Unternehmen schneller bessere Entscheidungen treffen.  
  
PDW ermöglicht nicht nur eine noch nie da gewesene Abfrageleistung, sondern auch Folgendes:  
  
-   Ihr Data Warehouse kann beliebig groß sein, von einigen Terrabyte bis hin zu über sechs Petabyte an Daten in einer einzelnen Appliance. Dazu können Sie Ihrem System sogenannte Skalierungseinheiten hinzufügen.  
  
-   Sie können immer auf Ihre Daten zugreifen, egal wann Sie sie benötigen. Dies wird durch die integrierte hohe Redundanz und Hochverfügbarkeit gewährleistet.  
  
-   Sie können Probleme beim Laden und Konsolidieren von Daten lösen.  
  
-   Sie können Hadoop-Daten mit relationalen Daten integrieren. So ist es möglich, schnelle Analysen mit der hochgradig parallelisierten PolyBase-Technologie von PDW durchzuführen.  
  
-   Sie können umfangreiche End-to-End-Lösungen mit Business Intelligence-Tools entwickeln.  

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den Vorteilen von Parallel Data Warehouse finden Sie im Whitepaper [A Breakthrough Platform for Next-Generation Data Warehousing and Big Data Solutions (Eine revolutionäre Plattform für Data Warehousing und Big Data-Lösungen der nächsten Generation)](https://msdn.microsoft.com/library/dn520808.aspx) auf MSDN.  
  

