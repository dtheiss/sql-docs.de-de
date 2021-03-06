---
title: Hinzufügen einer Gruppe (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1ac283320d94cc77b26c09baf8e75ed7f19e6be4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52777232"
---
# <a name="add-a-group-master-data-services"></a>Hinzufügen einer Gruppe (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Fügen Sie der Liste **Gruppen** in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] eine Gruppe hinzu, um damit zu beginnen, Berechtigungen für die Webanwendung zuzuweisen. Bevor ein Benutzer in der Gruppe auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]zugreifen kann, müssen Sie einem oder mehr Funktionsbereichen und Modellobjekten die Gruppenberechtigung geben.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Benutzer- und Gruppenberechtigungen** zuzugreifen.  
  
### <a name="to-add-a-group"></a>So fügen Sie eine Gruppe hinzu  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Benutzer- und Gruppenberechtigungen**.  
  
2.  Klicken Sie auf der Seite **Benutzer** auf der Menüleiste auf **Gruppen verwalten**.  
  
3.  Klicken Sie auf **Gruppen hinzufügen**.  
  
4.  Geben Sie den Namen der Gruppe ein, und stellen Sie diesem den Active Directory-Domänennamen oder den Namen des Servercomputers voran, z.B. *Domäne\Gruppenname* oder *Computer\Gruppenname*.  
  
5.  Klicken Sie optional auf **Namen überprüfen**.  
  
6.  Klicken Sie auf **OK**.  
  
    > [!NOTE]  
    >  Wenn der Benutzer zum ersten Mal auf den [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]zugreift, wird der Name des Benutzers zur Benutzerliste des [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] hinzugefügt.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Zuweisen von Berechtigungen für Funktionsbereiche &#40;Master Data Services&#41;](../master-data-services/assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  
