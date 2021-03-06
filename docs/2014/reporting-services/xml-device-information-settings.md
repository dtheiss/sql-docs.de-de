---
title: XML-Geräteinformationseinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- XML [Reporting Services], rendering
- device information settings [Reporting Services], PDF rendering
ms.assetid: a32e83fe-c10e-4ebd-8975-5be7dcc422e7
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7aa0f6e28dae59d7559dbb009ce4441dd4a2119d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013141"
---
# <a name="xml-device-information-settings"></a>XML-Geräteinformationseinstellungen
  In der folgenden Tabelle werden die Geräteinformationseinstellungen zum Rendern in das XML-Format aufgeführt.  
  
|Einstellung|Wert|  
|-------------|-----------|  
|`XSLT`|Der Pfad zum Berichtsserver-Namespace von XSLT, der auf die XML-Datei, z. B. `/Transforms/myxslt`, angewendet werden soll. Die XSL-Datei muss eine veröffentlichte Ressource auf einem Berichtsserver sein, und Sie müssen über einen Berichtsserver-Elementpfad darauf zugreifen. Der Wert dieser Einstellung wird nach jedem XSLT übernommen, das im Bericht angegeben wird. Wird die `XSLT`-Einstellung angewendet, wird die `OmitSchema`-Einstellung nicht beachtet.|  
|**MIMEType**|MIME-Typ (Multipurpose Internet Mail Extensions) der XML-Datei|  
|**UseFormattedValues**|Gibt an, ob der formatierte Wert eines Textfelds beim Generieren der XML-Daten gerendert werden soll. Ein false-Wert gibt an, dass der zugrundeliegende Wert des Textfelds verwendet wird.|  
|**Indented**|Gibt an, ob XML-Dateien mit Einzug generiert werden sollen. Der Standardwert `false` generiert komprimierte XML-Dateien ohne Einzug.|  
|`OmitNamespace`|Gibt an, ob der Standardnamespace in der XML-Datei weggelassen werden soll.<br /><br /> Bei "true" wird kein Standardnamespace in der XML-Datei angegeben.<br /><br /> Bei FALSE gibt die XML-Datei einen Standardnamespace mit dem Wert der DataSchema-Eigenschaft des Berichts an. Die DataSchema-Eigenschaft verwendet standardmäßig den Berichtsnamen.<br /><br /> Der Standardwert ist `false`.|  
|`OmitSchema`|Gibt an, ob der Schemaspeicherort in der XML-Datei weggelassen werden soll. Der Speicherort ist das SchemaLocation-Attribut. Der Standardwert von OmitSchema hängt vom OmitNamespace-Wert ab:<br /><br /> Wenn OmitNamespace = False, gilt standardmäßig OmitSchema = `False`. Der Benutzer kann den Standardwert überschreiben, indem OmitSchema = True festgelegt wird.<br /><br /> Wenn OmitNamespace = True, gilt für OmitSchema `True` – unabhängig vom explizit für OmitShema konfigurierten Wert.|  
|**Codierung**|Der Internet Assigned Numbers Authority (IANA)-Name einer Zeichencodierung, die von .NET Framework unterstützt wird. Der Standardwert ist `UTF-8`. Beispiele für andere Werte: ASCII, UTF-7 und UTF-16.|  
|**FileExtension**|Die Dateierweiterung für die generierte Datei.|  
|**Schema**|Gibt an, ob die XML-Schemadefinition (XSD) gerendert wird oder ob die tatsächlichen XML-Daten gerendert werden. Der Wert `true` gibt an, dass ein XML-Schema gerendert wird. Der Standardwert ist `false`.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei RSReportServer.config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
