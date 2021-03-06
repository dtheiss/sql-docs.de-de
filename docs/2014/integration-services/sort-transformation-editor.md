---
title: Transformations-Editor für Sortierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttransformation.f1
helpviewer_keywords:
- Sort Transformation Editor
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d57129a0997093aa351b83b09f87ee7d38bb2a25
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178310"
---
# <a name="sort-transformation-editor"></a>Transformations-Editor für Sortierung
  Mithilfe des Dialogfelds **Transformations-Editor für Sortierung** können Sie die zu sortierenden Spalten auswählen, die Sortierreihenfolge festlegen und angeben, ob Duplikate entfernt werden.  
  
 Weitere Informationen zur Transformation zum Sortieren finden Sie unter [Sort Transformation](data-flow/transformations/sort-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Verfügbare Eingabespalten**  
 Geben Sie mithilfe der Kontrollkästchen die zu sortierenden Spalten an.  
  
 **Name**  
 Zeigen Sie den Namen jeder verfügbaren Eingabespalte an.  
  
 **Passthrough**  
 Geben Sie an, ob die Spalte in der sortierten Ausgabe eingeschlossen werden soll.  
  
 **Eingabespalte**  
 Wählen Sie für jede Zeile eine Spalte aus der Liste der verfügbaren Eingabespalten aus. Ihre Auswahl wird entsprechend in der Auswahl der Kontrollkästchen in der **Verfügbare Eingabespalten** -Tabelle deutlich.  
  
 **Ausgabealias**  
 Geben Sie einen Alias für jede Spalte ein. Standardmäßig wird der Name der Eingabespalte verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist.  
  
 **Sortiertyp**  
 Geben Sie an, ob in aufsteigender oder absteigender Reihenfolge sortiert wird.  
  
 **Sortierreihenfolge**  
 Geben Sie die Reihenfolge an, in der die Spalten sortiert werden. Diese Einstellung muss manuell für jede Spalte vorgenommen werden.  
  
 **Vergleichsflags**  
 Weitere Informationen zu den Optionen für das Vergleichen von Zeichenfolgen finden Sie unter [Vergleichen von Zeichenfolgendaten](data-flow/comparing-string-data.md).  
  
 **Zeilen mit doppelten Sortierwerten entfernen**  
 Geben Sie an, ob die Transformation doppelte Zeilen in die Transformationsausgabe kopiert oder einen einzelnen Eintrag für alle Duplikate erstellt, basierend auf den angegebenen Optionen für den Zeichenfolgenvergleich.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
