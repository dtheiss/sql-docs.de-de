---
title: Aktivieren der Data Quality Services-Integration in Master Data Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 51cefe654fa35284a2bab851d39ed560a362356b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687908"
---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a>Aktivieren der Data Quality Services-Integration in Master Data Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Im [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]wird über die Data Quality Services (DQS) eine Abgleichfunktion bereitgestellt. Diese Funktion muss aktiviert werden, damit sie verwendet werden kann.  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
-   Es müssen eine [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Webanwendung und eine Datenbank vorhanden sein.  
  
-   Die Data Quality Services-Funktion und der Data Quality-Client müssen auf der gleichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz installiert sein, auf der die MDS-Datenbank gehostet wird. Weitere Informationen finden Sie unter [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
### <a name="to-enable-data-quality-services-integration"></a>So aktivieren Sie die Data Quality Services-Integration  
  
1.  Öffnen Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  Klicken Sie im linken Bereich auf **Webkonfiguration**.  
  
3.  Wählen Sie auf der Seite **Webkonfiguration** die Website und die Webanwendung aus.  
  
4.  Klicken Sie im Abschnitt **DQS-Integration aktivieren** auf **Integration in Data Quality Services aktivieren**.  
  
5.  Klicken Sie im Bestätigungsdialogfeld auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Data Quality-Abgleich im MDS-Add-In für Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Master Data Services-Add-In für Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [Installieren von Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
