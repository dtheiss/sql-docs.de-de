---
title: Melden Sie im Dialogfeld Eigenschaften von Verweise (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10082"
ms.assetid: 3414c857-8ea6-4fc4-a6d5-b4883c039efa
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 4acfe27815dc8eeb2f15a685937d5870fd74368b
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56040991"
---
# <a name="report-properties-dialog-box-references-report-builder"></a>Berichtseigenschaften (Dialogfeld), Verweise (Berichts-Generator)
  Wählen Sie die Registerkarte **Verweise** im Dialogfeld **Berichtseigenschaften** , um Verweise auf benutzerdefinierte oder andere externe Assemblys sowie benutzerdefinierte Klasseninstanzen hinzuzufügen oder zu entfernen, die von Ausdrücken in der Berichtsdefinition verwendet werden. Benutzerdefinierte Assemblys werden im lokalen Modus in Berichts-Generator nicht unterstützt. Um Berichte zu erstellen, die benutzerdefinierte Assemblys verwenden, verwenden Sie Berichts-Designer in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="options"></a>Optionen  
 **Assemblys hinzufügen oder entfernen**  
 Führt die Assemblys auf, auf die der Bericht verweist. Die Assembly muss auf dem Computer, auf dem das Tool zum Entwerfen des Berichts installiert ist, und auf dem Berichtsserver verfügbar sein. Der Name des Verweises muss mit dem Inhalt der  **\<CodeModule >** -Tags in der Berichtsdefinitionssprache (RDL)-Datei übereinstimmen.  
  
 **Hinzufügen**  
 Klicken Sie auf diese Option, um eine Assembly hinzuzufügen. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...), zum Öffnen der **öffnen** Dialogfeld und die für die berichtsverarbeitung und ausdrucksauswertung erforderlichen Assemblys auszuwählen.  
  
 **Entfernen**  
 Um einen Assemblyverweis aus der Liste zu entfernen, wählen Sie den Assemblynamen aus, und klicken Sie auf die Schaltfläche **Entfernen** .  
  
 **Klassen hinzufügen oder entfernen**  
 Führt die vom Bericht verwendeten Klasseninstanzen auf. Die Klassenliste wird nur von instanzbasierten Elementen, nicht von statischen Elementen, verwendet.  
  
 **Hinzufügen**  
 Klicken Sie auf diese Schaltfläche, um einen Klassenverweis hinzuzufügen. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...), zum Öffnen der **öffnen** Dialogfeld und die für die berichtsverarbeitung und ausdrucksauswertung erforderlichen Klassen auszuwählen.  
  
 **Entfernen**  
 Um die Klasseninstanz zu löschen, wählen Sie sie aus, und klicken Sie auf die Schaltfläche **Entfernen** .  
  
 **Nach oben**  
 Für Klassen mit Abhängigkeiten können Sie diesen Verweis in der Liste nach oben verschieben.  
  
 **Nach unten**  
 Für Klassen mit Abhängigkeiten können Sie diesen Verweis in der Liste nach unten verschieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)  
  
  
