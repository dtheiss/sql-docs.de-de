---
title: Zusammenführen von Konflikten (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 797219ad-5109-4666-94d3-dd1d59440a33
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 927990916440cc33c56a362b17b77adbb726620e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52779562"
---
# <a name="merge-conflicts-master-data-services"></a>Konflikte zusammenführen [Master Data Services]

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Wenn in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]Daten, die Sie veröffentlichen möchten, von einem anderen Benutzer geändert wurden, schlägt das Veröffentlichen mit einem Konfliktfehler fehl. Um diesen Fehler zu beheben, können Sie die Konflikte zusammenführen und die Änderungen erneut veröffentlichen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
-   Sie müssen mindestens die Berechtigung "Aktualisieren" für das Blattmodellobjekt für die Entität besitzen, die Sie aktualisieren.  
  
### <a name="to-merge-conflicts"></a>So führen Sie Konflikte zusammen  
  
1.  Aktualisieren Sie auf der Seite **Explorer** das Elementattribut.  
  
2.  Wenn das gleiche Elementattribut von einem anderen Benutzer geändert wurde, wird das Dialogfeld **Konflikte zusammenführen** angezeigt.  
  
3.  Im Dialogfeld **Konflikte zusammenführen** haben Sie folgende Möglichkeiten:  
  
    -   Sie können **Neueste** auswählen und auf **Anwenden** klicken, um die ausstehenden Änderungen rückgängig zu machen und die neueste Version vom Server herunterzuladen.  
  
    -   Sie können **Ursprüngliche** auswählen und auf **Anwenden** klicken, um die ursprüngliche Version auf das Arbeitsblatt anzuwenden.  
  
    -   Sie können **Ihre** auswählen und auf **Anwenden** klicken, um die vorhandenen lokalen Änderungen beizubehalten.  
  
4.  Nachdem Sie auf **Anwenden**geklickt haben, können Sie zusätzliche Änderungen vornehmen und erneut veröffentlichen. Sie können auch auf **Abbrechen** klicken, um die Aktualisierung abzubrechen und die neueste Version erneut vom Server herunterzuladen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Elemente &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)  
  
  
