---
title: Microsoft Connector für SAP BW | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5281f080-53d5-4679-aa26-f4cd4ac7a2df
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a06dcac3487220a84d8a22f6c92e02859e91a6f8
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52510062"
---
# <a name="microsoft-connector-for-sap-bw"></a>Microsoft Connector for SAP BW
  Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW besteht aus drei Komponenten, mit denen Sie Daten aus einem SAP NetWeaver BW-System, Version 7, extrahieren oder in ein solches System laden können.  
  
 Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW für SQL Server 2016 ist eine Komponente des SQL Server 2016 Feature Pack. Zum Installieren des Connector für SAP BW und der zugehörigen Dokumentation laden Sie das Installationsprogramm von der [SQL Server 2016 Feature Pack-Webseite](https://go.microsoft.com/fwlink/?LinkId=746297)herunter, und führen Sie es aus.  

> [!IMPORTANT]
> Microsoft hat keine Einsicht in die Updatebereitstellung für die SAP BW-Connectors. Der Quellcode der SAP BW-Komponenten ist kein Eigentum von Microsoft, da diese von einem Drittanbieter entwickelt wurden. Aus diesem Grund kann Microsoft selbst keine Updates bereitstellen. Die neuesten SAP-Konnektivitätskomponenten können Sie bei Microsoft-ISV-Partnern wie [Theobald Software](https://theobald-software.com/en/xtract-is-productinfo.html) erwerben. Die ISV-Partner von Microsoft haben ihre SAP-Konnektivitätskomponenten für SSIS hinsichtlich einer Installation in Azure angepasst.
 
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector für SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
> [!IMPORTANT]  
>  Das Extrahieren von Daten aus SAP NetWeaver BW erfordert zusätzliche SAP-Lizenzen. Stimmen Sie diese Anforderungen mit SAP ab.  
  
## <a name="components"></a>Components  
 Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW weist folgende Komponenten auf:  
  
-   **SAP BW-Quelle:** Die SAP BW-Quelle ist eine Datenflussquellkomponente, mit der Sie Daten aus einem SAP NetWeaver BW 7-System extrahieren können.  
  
-   **SAP BW-Ziel:** Das SAP BW-Ziel ist eine Datenflusszielkomponente, mit der Sie Daten in ein SAP NetWeaver BW 7-System laden können.  
  
-   **SAP BW-Verbindungs-Manager:** Der SAP BW-Verbindungs-Manager verbindet eine SAP BW-Quelle oder ein SAP BW-Ziel mit einem SAP NetWeaver BW 7-System.  
  
 Eine exemplarische Vorgehensweise, die zeigt, wie der SAP BW-Verbindungs-Manager sowie die zugehörige Quelle und das zugehörige Ziel konfiguriert und verwendet werden, finden Sie im Whitepaper [Using SQL Server Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkId=301897)(Verwenden von SQL Server Integration Services und SAP BI 7.0). In diesem Whitepaper wird auch erläutert, wie die erforderlichen Objekte in SAP BW konfiguriert werden.  
  
## <a name="documentation"></a>Dokumentation  
 Diese Hilfedatei für den [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW enthält die folgenden Themen und die Abschnitte:  
  
 [Installieren von Microsoft Connector für SAP BW](../integration-services/installing-the-microsoft-connector-for-sap-bw.md)  
 Beschreibt die Installationsanforderungen für den [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW.  
  
 [Microsoft Connector for SAP BW Components](../integration-services/microsoft-connector-for-sap-bw-components.md)  
 Beschreibt die einzelnen Komponenten im [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW.  
  
 [F1-Hilfe zum Microsoft Connector for SAP BW](../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
 Beschreibt die Benutzeroberfläche der einzelnen Komponenten im [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW.  
  
  
