---
title: DTAXML-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0682c6100a96fbfb3016dec4bead4c385190192f
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53356855"
---
# <a name="dtaxml-element-dta"></a>DTAXML-Element (DTA)
  Das Stammelement einer XML-Eingabe- oder -Ausgabedatei des Datenbankoptimierungsratgebers. **DTAXML** enthält alle Elemente, die die vom Datenbankoptimierungsratgeber generierte Optimierungseingabe und -ausgabe beschreiben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|Attribut|Description|  
|---------------|-----------------|  
|`xmlns:xsi`|Erforderlich. Identifiziert den XML-Schemainstanzennamespace. Attribute aus diesem Namespace dienen zum Verweisen auf das Schema, das zum Überprüfen der XML-Datei des Datenbankoptimierungsratgebers verwendet wird.<br /><br /> Erforderlicher Wert: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|`xmlns`|Erforderlich. Identifiziert den Namespace des Datenbankoptimierungsratgebers.<br /><br /> Wenn Sie die XML-Datei des Datenbankoptimierungsratgebers mit dem XML-Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]bearbeiten, wird dieser Wert von der F1-Hilfe und der dynamischen Hilfe verwendet, um mögliche Referenzthemen in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation zu ermitteln.<br /><br /> Erforderlicher Wert:<br /><br /> für das[XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?LinkId=43100)|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmal pro DTA XML-Datei erforderlich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|None|  
|**Untergeordnete Elemente**|[DTAInput-Element &#40;DTA&#41;](dtainput-element-dta.md)<br /><br /> `DTAOutput` -Element (finden Sie unter [-Datenbank-Engine Tuning Advisor XML-Schema](https://schemas.microsoft.com/sqlserver/) Informationen)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu XML-Namespaces finden Sie unter [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) (in Englisch) in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="example"></a>Beispiel  
 Beispiele für typische **DTAXML**-Elemente finden Sie unter [Beispiele für XML-Eingabedateien &#40;DTA&#41;](xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)   
 [Starten und Verwenden des Datenbankoptimierungsratgebers](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
