---
title: Anzeigen von QuickInfos für eine Reihe (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 4c9606ff-e1c3-4cf7-a4e7-bb16f1a9e8ab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e9e02af6adf0e674d6af2775cb427440b4471c9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029651"
---
# <a name="show-tooltips-on-a-series-report-builder-and-ssrs"></a>Anzeigen von QuickInfos für eine Reihe (Berichts-Generator und SSRS)
  Sie können den einzelnen Datenpunkten in einem Diagramm QuickInfos hinzufügen, um Informationen zum Datenpunkt anzuzeigen, beispielsweise den Gruppennamen, den Wert des Datenpunkts oder den Prozentsatz des Datenpunkts in Bezug auf die Gesamtreihe, wenn Benutzer mit dem Cursor auf den Datenpunkt in einem gerenderten Bericht zeigen.  
  
 Einer berechneten Reihe können keine QuickInfos hinzugefügt werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-tooltip-on-each-data-point"></a>So geben Sie eine QuickInfo für die Datenpunkte an  
  
1.  Klicken Sie mit der rechten Maustaste auf die Reihe, oder klicken Sie mit der rechten Maustaste auf das Feld im Bereich **Werte** , und klicken Sie auf **Reiheneigenschaften**.  
  
2.  Klicken Sie auf **Reihendaten** , und geben Sie für die **ToolTip** -Eigenschaft eine Zeichenfolge oder einen Ausdruck ein. Sie können alle diagrammspezifischen Schlüsselwörter zur Darstellung anderer Elemente im Diagramm verwenden. Weitere Informationen finden Sie unter [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Ändern des Texts eines Legendenelements (Berichts-Generator und SSRS)](chart-legend-change-item-text-report-builder.md)   
 [Formatieren von Reihenfarben in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Hinzufügen einer Drillthroughaktion für einen Bericht &#40;Berichts-Generator und SSRS&#41;](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
