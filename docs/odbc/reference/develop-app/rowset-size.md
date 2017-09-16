---
title: "Rowsetgröße | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rowset size [ODBC]
- cursors [ODBC], block
- result sets [ODBC], rowset size
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 60366ae8-175c-456a-ae5e-bdd860786911
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b7d3abee6c42fe95205bbb74edc671d8dc02bf87
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="rowset-size"></a>Rowsetgröße
Welche Rowsetgröße verwendet, hängt von der Anwendung ab. Bildschirmbasierte Anwendungen führen Sie häufig eine der zwei Strategien. Die erste ist die Rowsetgröße festzulegen, der die Anzahl der Zeilen, die auf dem Bildschirm angezeigt. Wenn der Benutzer den Bildschirm Größe verkleinert wird, wechselt die Anwendung die Rowsetgröße. Das zweite ist, die Rowsetgröße auf einen höheren Wert ein, z. B. 100, festzulegen, die reduziert die Anzahl der Aufrufe an die Datenquelle. Die Anwendung lokal innerhalb des Rowsets möglichst verschiebt und neue Zeilen abruft, nur verwendet werden, wenn es außerhalb des Rowsets ein Bildlauf durchgeführt.  
  
 Andere Anwendungen, z. B. Berichte, die Rowsetgröße auf die Höchstanzahl der Zeilen festgelegt, kann die Anwendung verarbeiten, tendenziell – mit einem größeren Rowset, das Netzwerk Mehraufwand pro Zeile wird manchmal reduziert. Genau wie groß ein Rowset sein kann, hängt von der Größe des jede Zeile und die Menge des verfügbaren Arbeitsspeichers ab.  
  
 Rowsetgröße wird durch einen Aufruf von **SQLSetStmtAttr** mit einem *Attribut* SQL_ATTR_ROW_ARRAY_SIZE-Argument. Die Anwendung die Rowsetgröße ändern, neue Rowset Puffer zu binden können (durch Aufrufen von **SQLBindCol** oder das Angeben eines Bindung Offsets) auch nach Zeilen abgerufen wurden, oder beides. Welche Konsequenzen eine Änderung der Rowsetgröße hängen von der Funktion:  
  
-   **SQLFetch** und **SQLFetchScroll** die Rowsetgröße zum Zeitpunkt des Aufrufs verwenden, um zu bestimmen, wie viele Zeilen abgerufen werden. Allerdings **SQLFetchScroll** mit einem *FetchOrientation* der SQL_FETCH_NEXT inkrementiert der Cursor basierend auf das Rowset der vorhergehenden Abrufvorgang und klicken Sie dann Abrufvorgänge Rowset basierend auf die aktuelle Größe des Rowsets.  
  
-   **SQLSetPos** verwendet die Rowsetgröße, die zum Zeitpunkt der vorherigen Aufruf von eingerichtet wurde, **SQLFetch** oder **SQLFetchScroll**, da **SQLSetPos** arbeitet mit einer Rowset, das bereits festgelegt wurde. **SQLSetPos** auch übernimmt die neue Rowsetgröße Wenn **SQLBulkOperations** wurde aufgerufen, nachdem die Rowsetgröße geändert wurde.  
  
-   **SQLBulkOperations** wird verwendet, die Rowsetgröße faktisch zum Zeitpunkt des Aufrufs, da sie die Vorgänge in einer Tabelle, die unabhängig von der alle abgerufenen Rowsets ausführt.