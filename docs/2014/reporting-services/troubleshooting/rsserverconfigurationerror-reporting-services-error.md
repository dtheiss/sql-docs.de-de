---
title: 'rsServerConfigurationError: Reporting Services-Fehler | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a0017be7f7ac6117c1512cbaf3e46b662f0a06f0
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56021679"
---
# <a name="rsserverconfigurationerror---reporting-services-error"></a>rsServerConfigurationError – Reporting Services-Fehler
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|rsServerConfiguration|  
|Ereignisquelle|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Komponente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Meldungstext|Konfigurationsfehler beim Berichtsserver.|  
  
## <a name="explanation"></a>Erklärung  
 Dies ist ein allgemeiner Fehler, der auftritt, wenn der Berichtsserver oder ein Berichterstellungstool fehlerhaft konfiguriert wurde. Der Fehler wird normalerweise mit einer zweiten Meldung ausgegeben, die die tatsächliche Ursache des Fehlers enthält.  
  
 Die folgende Liste enthält die möglichen Ursachen:  
  
-   Die RSReportServer.config-Datei oder die RSReportDesigner.config-Datei kann nicht gefunden oder gelesen werden.  
  
-   XML-Elemente in einer der beiden Konfigurationsdateien fehlen oder sind ungültig.  
  
-   Werte für einen oder mehrere XML-Elemente fehlen oder sind ungültig.  
  
-   Registrierungseinstellungen sind ungültig.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn dieser Fehler auftritt, nachdem Sie manuell eine Konfigurationsdatei bearbeitet haben, machen Sie die Änderungen rückgängig, indem Sie den ursprünglichen Wert wieder eingeben, oder stellen Sie eine vorherige Version wieder her, wenn eine Sicherung existiert.  
  
 Um zusätzliche Fehlermeldungsinformationen zu überprüfen, die `rsServerConfiguration` Fehler, überprüfen Sie die Report Server Ablaufverfolgungs-Protokolldateien, die sich an \Microsoft SQL Server\MSRS12 befinden.\< Instancename > \reporting. Weitere Informationen finden Sie unter [Reporting Services-Protokolldateien und Quellen](../report-server/reporting-services-log-files-and-sources.md).  
  
## <a name="internal-only"></a>Nur intern  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurationsdateien](../report-server/reporting-services-configuration-files.md)   
 [Ändern einer Reporting Services-Konfigurationsdatei &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
