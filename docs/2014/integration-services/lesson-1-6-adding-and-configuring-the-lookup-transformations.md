---
title: 'Schritt 6: Hinzufügen und Konfigurieren von Suchtransformationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c59f723-9707-4407-80ae-f05f483cf65f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 756c6ce9c57b314ddd9f9e821df7c391af5fa84a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52805796"
---
# <a name="step-6-adding-and-configuring-the-lookup-transformations"></a>Schritt 6: Hinzufügen und Konfigurieren der Transformationen zum Suchen
  Nach dem Konfigurieren der Flatfilequelle zum Extrahieren von Daten aus der Quelldatei besteht die nächste Aufgabe darin, die Suchtransformationen zu definieren, die zum Abrufen der Werte für **CurrencyKey** und **DateKey**erforderlich sind. Von einer Transformation zum Suchen wird eine Suche durchgeführt, indem Daten in der angegebenen Eingabespalte mit einer Spalte in einem referenzierten Dataset verknüpft werden. Bei dem Verweisdataset kann es sich um eine vorhandene Tabelle oder Sicht, eine neue Tabelle oder das Ergebnis einer SQL-Anweisung handeln. In diesem Lernprogramm stellt die Transformation für Suche stellt mithilfe eines OLE DB-Verbindungs-Managers eine Verbindung mit der Datenbank her, die die Daten enthält, die als Quelle des Verweisdatasets dienen.  
  
> [!NOTE]  
>  Sie können die Transformation für Suche auch so konfigurieren, dass sie eine Verbindung mit einem Cache herstellt, der das Verweisdataset enthält. Weitere Informationen finden Sie unter [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
 Für dieses Lernprogramm fügen Sie die folgenden zwei Transformationskomponenten zum Suchen zu dem Paket hinzu und konfigurieren sie:  
  
-   Eine Transformation zum Ausführen einer Suche nach Werten aus der **CurrencyKey** -Spalte der **DimCurrency** -Dimensionstabelle basierend auf übereinstimmenden **CurrencyID** -Spaltenwerten aus der Flatfile.  
  
-   Eine Transformation zum Ausführen einer Suche nach Werten in der **DateKey** -Spalte der **DimDate** -Dimensionstabelle basierend auf übereinstimmenden **CurrencyDate** -Spaltenwerten aus der Flatfile.  
  
 In beiden Fällen verwendet die Suchtransformation den OLE DB-Verbindungs-Manager, den Sie zuvor erstellt haben.  
  
### <a name="to-add-and-configure-the-lookup-currency-key-transformation"></a>So fügen Sie die Lookup Currency Key-Transformation hinzu und konfigurieren sie  
  
1.  Erweitern Sie in der **SSIS-Toolbox**die Option **Allgemein**, und ziehen Sie anschließend **Suche** auf die Entwurfsoberfläche der Registerkarte **Datenfluss** . Legen Sie „Suche“ direkt unterhalb der **Extract Sample Currency Data** -Quelle ab.  
  
2.  Klicken Sie auf die **Extract Sample Currency Data** -Flatfilequelle, und ziehen Sie den grünen Pfeil auf die neu hinzugefügte Transformation **Suche** , um die zwei Komponenten zu verbinden.  
  
3.  Klicken Sie auf der **Datenfluss** -Entwurfsoberfläche auf **Suche** in der Transformation **Suche** , und ändern Sie den Namen in **Lookup Currency Key**.  
  
4.  Doppelklicken Sie auf die Transformation **Lookup Currency Key** , um den Transformations-Editor für Suche anzuzeigen.  
  
5.  Wählen Sie auf der Seite **Allgemein** die folgenden Optionen aus:  
  
    1.  Wählen Sie **Vollcache**aus.  
  
    2.  Wählen Sie im Bereich **Verbindungstyp** **OLE DB-Verbindungs-Manager**aus.  
  
6.  Wählen Sie auf der Seite **Verbindung** die folgenden Optionen aus:  
  
    1.  Stellen Sie im **OLE DB-Verbindungs-Manager** sicher, dass **localhost.AdventureWorksDW2012** angezeigt wird.  
  
    2.  Wählen Sie **Ergebnisse einer SQL-Abfrage verwenden**aus, und geben Sie anschließend die folgende SQL-Anweisung ein, oder kopieren Sie diese:  
  
        ```  
        select * from (select * from [dbo].[DimCurrency]) as refTable  
        where [refTable].[CurrencyAlternateKey] = 'ARS'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'AUD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'BRL'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CAD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CNY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'DEM'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'EUR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'FRF'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'GBP'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'JPY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'MXN'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'SAR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'USD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'VEB'  
        ```  
  
7.  Wählen Sie auf der Seite **Spalten** die folgenden Optionen aus:  
  
    1.  Ziehen Sie aus dem Bereich **Verfügbare Eingabespalten** den Spaltennamen **CurrencyID** in den Bereich **Verfügbare Suchspalten** auf **CurrencyAlternateKey**.  
  
    2.  Aktivieren Sie in der Liste **Verfügbare Suchspalten** das Kontrollkästchen links neben **CurrencyKey**.  
  
8.  Klicken Sie auf **OK** , um zur Entwurfsoberfläche **Datenfluss** zurückzukehren.  
  
9. Klicken Sie mit der rechten Maustaste auf die Lookup Currency Key-Transformation, und klicken Sie auf **Eigenschaften**.  
  
10. Überprüfen Sie im Eigenschaftenfenster, ob die `LocaleID` -Eigenschaftensatz auf **Englisch (Vereinigte Staaten)** und **DefaultCodePage** -Eigenschaftensatz auf **1252**.  
  
### <a name="to-add-and-configure-the--lookup-datekey-transformation"></a>So fügen Sie die Lookup DateKey-Transformation hinzu und konfigurieren sie  
  
1.  Ziehen Sie in der **SSIS-Toolbox**die Option **Suche** auf die **Datenfluss** -Entwurfsoberfläche. Legen Sie „Suche“ direkt unterhalb der Transformation **Lookup Currency Key** ab.  
  
2.  Klicken Sie auf die **Lookup Currency Key** -Transformation, und ziehen Sie den grünen Pfeil auf die neu hinzugefügte **Suche** -Transformation, um die zwei Komponenten zu verbinden.  
  
3.  Klicken Sie im Dialogfeld **Eingabe-/Ausgabe-Auswahl** im Listenfeld **Ausgabe** auf **Ausgabe der Suchübereinstimmungen** , und klicken Sie anschließend auf **OK**.  
  
4.  Klicken Sie auf der Entwurfsoberfläche **Datenfluss** in der neu hinzugefügten Transformation **Suche** auf **Suche** , und ändern Sie den Namen in **Lookup Date Key**.  
  
5.  Doppelklicken Sie auf die Transformation **Lookup Date Key** .  
  
6.  Wählen Sie auf der Seite **Allgemein** die Option **Teilcache**aus.  
  
7.  Wählen Sie auf der Seite **Verbindung** die folgenden Optionen aus:  
  
    1.  Stellen Sie im **OLE DB-Verbindungs-Manager** sicher, dass **localhost.AdventureWorksDW2012** angezeigt wird.rd.  
  
    2.  Geben Sie im Feld **Tabelle oder Sicht verwenden** den Eintrag **[dbo].[DimDate]** ein, oder wählen Sie diesen Eintrag aus.  
  
8.  Wählen Sie auf der Seite **Spalten** die folgenden Optionen aus:  
  
    1.  Ziehen Sie aus dem Bereich **Verfügbare Eingabespalten** den Spaltennamen **CurrencyDate** in den Bereich **Verfügbare Suchspalten** auf **FullDateAlternateKey**.  
  
    2.  Aktivieren Sie in der Liste **Verfügbare Suchspalten** das Kontrollkästchen links neben **DateKey**.  
  
9. Überprüfen Sie auf der Seite **Erweitert** die Optionen für die Zwischenspeicherung.  
  
10. Klicken Sie auf **OK**, um zur Entwurfsoberfläche **Datenfluss** zurückzukehren.  
  
11. Klicken Sie mit der rechten Maustaste auf die Lookup Date Key-Transformation, und klicken Sie auf **Eigenschaften**.  
  
12. Überprüfen Sie im Eigenschaftenfenster, ob die `LocaleID` -Eigenschaftensatz auf **Englisch (Vereinigte Staaten)** und **DefaultCodePage** -Eigenschaftensatz auf **1252**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Schritt 7: Hinzufügen und Konfigurieren des OLE DB-Ziels](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)  
  
  
