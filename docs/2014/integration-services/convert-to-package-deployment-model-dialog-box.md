---
title: Konvertieren zu Package Deployment Model (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 17b3dae4dd2087fcae152718b9333d1b3afb52c8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140140"
---
# <a name="convert-to-package-deployment-model-dialog-box"></a>In Paketbereitstellungsmodell konvertieren (Dialogfeld)
  Mit dem Befehl **In Paketbereitstellungsmodell konvertieren** können Sie ein Paket auf dem Paketbereitstellungsmodell konvertieren, nachdem das Projekt und jedes Paket im Projekt auf Kompatibilität mit dem Modell überprüft wurden. Wenn ein Paket für ein Projektbereitstellungsmodell eindeutige Funktionen verwendet, z. B. Parameter, dann kann das Paket nicht konvertiert werden.  
  
## <a name="task-list"></a>Aufgabenliste  
 Für das Konvertieren eines Pakets auf ein Paketbereitstellungsmodell sind zwei Schritte erforderlich.  
  
1.  Wenn Sie den Befehl **In Paketbereitstellungsmodell konvertieren** aus dem Menü **Projekt** auswählen, werden das Projekt und jedes Paket auf Kompatibilität mit diesem Modell überprüft. Die Ergebnisse werden in der Tabelle **Ergebnisse** angezeigt.  
  
     Wenn das Projekt oder ein Paket den Kompatibilitätstest nicht besteht, klicken Sie in der Spalte **Ergebnis** auf **Fehler** , um weitere Informationen zu erhalten. Klicken Sie auf **Bericht speichern** , um eine Kopie dieser Informationen in einer Textdatei zu speichern.  
  
2.  Wenn das Projekt und alle Pakete den Kompatibilitätstest bestehen, klicken Sie auf **OK** , um das Paket zu konvertieren.  
  
> [!NOTE]  
>  Verwenden Sie den **Assistenten für die Konvertierung von Integration Services-Projekten**, um ein Projekt ins Projektbereitstellungsmodell zu konvertieren. Weitere Informationen finden Sie unter [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellung von Projekten und Paketen](packages/deploy-integration-services-ssis-projects-and-packages.md)   
 [Paketbereitstellung &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)   
 [Assistent für die Konvertierung von Integration Services-Projekten](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  
