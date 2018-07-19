---
title: Abrufen von Daten aus einem Data Mining-Modell (DMX) (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- retrieving report data
- datasets [Reporting Services], with DMX queries
- datasets [Reporting Services], Analysis Services
- queries [Reporting Services], data mining prediction
ms.assetid: d9cd3624-1594-4707-8887-55437dd7e07c
caps.latest.revision: 17
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7755e5026dc99e13f27de9619bb619e5f9e22db7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152241"
---
# <a name="retrieve-data-from-a-data-mining-model-dmx-ssrs"></a>Abrufen von Daten aus einem Data Mining-Modell (DMX) (SSRS)
  Zur Verwendung von Daten aus einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Data Mining-Modell in Ihrem Bericht müssen Sie eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenquelle und mindestens ein Berichtsdataset definieren. Sie müssen beim Erstellen der Datenquellendefinition eine Verbindungszeichenfolge sowie Anmeldeinformationen angeben, damit Sie von Ihrem Clientcomputer auf die Datenquelle zugreifen können.  
  
 Sie können eine eingebettete Datenquellendefinition für die Verwendung in einem Bericht oder eine freigegebene Datenquellendefinition für die Verwendung durch mehrere Berichte erstellen. Die Verfahren in diesem Thema beschreiben, wie eine eingebettete Datenquelle erstellt wird. Weitere Informationen zu freigegebenen Datenquellen finden Sie unter [Eingebettete und freigegebene Datenverbindungen oder Datenquellen (Berichts-Generator und SSRS)](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) und [Erstellen, Ändern und Löschen von freigegebenen Datenquellen (SSRS)](create-modify-and-delete-shared-data-sources-ssrs.md).  
  
 Nach der Erstellung einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenquelle können Sie ein oder mehrere Datasets erstellen. Für jedes Dataset verwenden Sie einen DMX-Abfrage-Designer (Data Mining-Vorhersageabfrage) zur Erstellung einer DMX-Abfrage, die die Feldauflistung angibt. Weitere Informationen finden Sie unter [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).  
  
 Nachdem Sie ein Dataset erstellt haben, wird der Name des Datasets im Berichtsdatenbereich als Knoten unter seiner Datenquelle angezeigt.  
  
 Nachdem Sie den Bericht veröffentlicht haben, müssen Sie eventuell die Anmeldeinformationen für die Datenquelle ändern, sodass die Berechtigungen zum Abrufen der Daten beim Ausführen des Berichts auf dem Berichtsserver gültig sind.  
  
### <a name="to-create-an-embedded-microsoft-sql-server-analysis-services-data-source"></a>So erstellen Sie eine eingebettete Microsoft SQL Server Analysis Services-Datenquelle  
  
1.  Klicken Sie im Berichtsdatenbereich auf der Symbolleiste auf **Neu**und anschließend auf **Datenquelle**.  
  
2.  Geben Sie im Dialogfeld **Datenquelleneigenschaften** im Textfeld **Name** einen Namen ein, oder übernehmen Sie den Standardnamen.  
  
3.  Überprüfen Sie, ob **Eingebettete Verbindung** aktiviert ist.  
  
4.  Wählen Sie in der Dropdownliste **Typ** die Option **Microsoft SQL Server Analysis Services**aus.  
  
5.  Geben Sie eine Verbindungszeichenfolge an, die für Ihre [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Datenquelle verwendet werden kann.  
  
     Erfragen Sie bei Ihrem Datenbankadministrator die Verbindungsinformationen und die Anmeldeinformationen, die verwendet werden sollen, um eine Verbindung mit der Datenquelle herzustellen. Die Verbindungszeichenfolge im folgenden Beispiel gibt die [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] -Beispieldatenbank auf dem lokalen Client an.  
  
    ```  
    Data Source=localhost;Initial Catalog=AdventureWorksDW2012  
    ```  
  
6.  Klicken Sie auf **Anmeldeinformationen**.  
  
     Legen Sie die Anmeldeinformationen fest, die für eine Verbindung mit der Datenquelle verwendet werden sollen. Weitere Informationen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](../../integration-services/connection-manager/data-sources.md).  
  
    > [!NOTE]  
    >  Um die Datenquellenverbindung zu testen, klicken Sie auf **Bearbeiten**. Klicken Sie im Dialogfeld **Verbindungseigenschaften** auf **Verbindung testen**. Wenn der Test erfolgreich ist, sehen Sie die Informationsmeldung "Der Verbindungstest war erfolgreich". Wenn der Test fehlschlägt, wird eine Warnmeldung mit weiteren Informationen darüber angezeigt, warum der Test nicht erfolgreich war.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Die Datenquelle wird im Berichtsdatenbereich angezeigt.  
  
### <a name="to-create-a-dataset-for-a-microsoft-sql-server-analysis-services"></a>So erstellen Sie ein Dataset für eine Microsoft SQL Server Analysis Services-Datenquelle  
  
1.  In der **Berichtsdaten** Bereich mit der rechten Maustaste in des Namens der Datenquelle, die Verbindung mit einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenquelle, und klicken Sie dann auf **Dataset hinzufügen**.  
  
2.  Geben Sie im Dialogfeld **Dataseteigenschaften** im Textfeld **Name** einen Namen ein.  
  
3.  In der **das Datenquelle**, stellen Sie sicher, dass der Name der Name einer Datenquelle, die Verbindung mit einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenquelle.  
  
4.  Klicken Sie auf **Abfrage-Designer** , um den grafischen Abfrage-Designer zu öffnen und interaktiv eine Abfrage zu erstellen. Wenn der Abfrage-Designer im MDX-Modus geöffnet wird, klicken Sie auf der Symbolleiste auf **DMX-Befehlstyp** (![Ansicht: Zur DMX-Abfragesprache wechseln](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")), um zum Data Mining-Abfrage-Designer zu wechseln. Weitere Informationen finden Sie unter [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).  
  
     Um eine vorhandene DMX-Abfrage aus einem anderen Bericht zu importieren, können Sie auch auf **Importieren**klicken und dann zur RDL-Datei mit der DMX-Abfrage navigieren. Das Importieren einer Abfrage aus einer DMX-Datei wird nicht unterstützt.  
  
5.  Nachdem Sie die Abfrage erstellt und ausgeführt haben, um Beispielergebnisse zu sehen, klicken Sie auf **OK**.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Das Dataset und seine Feldauflistung werden im Berichtsdatenbereich unter dem Datenquellenknoten angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Verbindungstyp für DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)   
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  