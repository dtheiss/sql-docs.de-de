---
title: Data Sources and Connection Methods | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- connections [Reporting Services], data sources
- reports [Reporting Services], data
- data sources [Reporting Services], methods
ms.assetid: 50999b52-fc7c-4333-9fb0-d04c37a4c90f
caps.latest.revision: 38
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 36f0d0867baea5aa6b13c2513c080a0502de496c
ms.contentlocale: de-de
ms.lasthandoff: 06/13/2017

---
# <a name="data-sources-and-connection-methods"></a>Datenquellen- und Verbindungsmethoden
  Mit diesen Methoden können Sie Datenquellenverbindungen und Anmeldeinformationen festlegen und verwalten.  
  
|Methode|Aktion|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataSource%2A>|Erstellt eine neue Datenquelle in der Berichtsserver-Datenbank oder SharePoint-Bibliothek.|  
|<xref:ReportService2010.ReportingService2010.DisableDataSource%2A>|Deaktiviert eine Datenquelle, die aktiviert ist.|  
|<xref:ReportService2010.ReportingService2010.EnableDataSource%2A>|Aktiviert eine Datenquelle, die deaktiviert ist.|  
|<xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A>|Gibt den Inhalt einer Datenquelle zurück.|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSourcePrompts%2A>|Ruft die Datenquellenaufforderungen für ein angegebenes Element ab.|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSources%2A>|Gibt die Datenquellen für ein Element im Katalog zurück.|  
|<xref:ReportService2010.ReportingService2010.ListDependentItems%2A>|Gibt eine Liste von Katalogelementen zurück, die auf ein angegebenes Katalogelement verweisen.|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptionsUsingDataSource%2A>|Gibt eine Liste von Abonnements zurück, die einer angegebenen Datenquelle zugeordnet sind.|  
|<xref:ReportService2010.ReportingService2010.SetDataSourceContents%2A>|Legt die Verbindungseigenschaften fest, die einer Datenquelle zugeordnet sind.|  
|<xref:ReportService2010.ReportingService2010.SetItemDataSources%2A>|Legt die Datenquellen für ein Element in einer Berichtsserver-Datenbank oder SharePoint-Bibliothek fest.|  
|<xref:ReportService2010.ReportingService2010.TestConnectForDataSourceDefinition%2A>|Testet die Verbindung für eine Datenquelle. Diese Methode unterstützt direkte Datenquellentests.|  
|<xref:ReportService2010.ReportingService2010.TestConnectForItemDataSource%2A>|Testet die Verbindung für eine Datenquelle. Diese Methode unterstützt Tests von veröffentlichten Datenquellen, die von Berichten oder Modellen und freigegebenen Datenquellen verwendet werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Berichtsserver-Webdienst](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Webdienstmethoden für Berichtsserver](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Technische Referenz &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  