---
title: Editor zum Auflösen von Spaltenverweisen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.resolvereferences.mapper.F1
- sql12.dts.designer.resolvereferences.preview.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d007e9bd3b4822cb09bdae8f3736bbd76f26009e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52771202"
---
# <a name="resolve-column-reference-editor"></a>Editor zum Auflösen von Spaltenverweisen
  Wenn ein Eingabepfad getrennt wurde, oder nicht zugeordnete Spalten im Pfad vorhanden sind, wird neben dem entsprechenden Datenpfad ein Fehlersymbol angezeigt. Der neue Editor zum Auflösen von Verweisen ermöglicht es, für alle Pfade in der Ausführungsstruktur nicht zugeordnete Eingabespalten mit zugeordneten Ausgabespalten zu verknüpfen, und vereinfacht dadurch die Lösung von Spaltenverweisfehlern. Der Editor zum Auflösen von Verweisen markiert auch die Pfade, um zu kennzeichnen, welche Pfade aufgelöst werden.  
  
> [!NOTE]  
>  Es ist nun möglich, eine Komponente zu bearbeiten, selbst wenn deren Eingabepfad getrennt ist.  
  
 Nachdem alle Spaltenverweise aufgelöst wurden und keine weiteren Datenpfadfehler auftreten, werden neben den Datenpfaden keine Fehlersymbole angezeigt.  
  
## <a name="options"></a>Optionen  
 Nicht zugeordnete Ausgabespalten (Quelle):  
 Spalten vom Upstreampfad, die derzeit nicht zugeordnet sind.  
  
 Zugeordnete Spalten (Quelle):  
 Spalten vom Upstreampfad, die Spalten vom Downstreampfad zugeordnet sind.  
  
 Zugeordnete Spalten (Ziel):  
 Spalten vom Upstreampfad, die Spalten vom Downstreampfad zugeordnet sind.  
  
 Nicht zugeordnete Eingabespalten (Ziel):  
 Spalten vom Downstreampfad, die derzeit nicht zugeordnet sind.  
  
 Nicht zugeordnete Eingabespalten löschen  
 Aktivieren Sie "Nicht zugeordnete Eingabespalten löschen", um nicht zugeordnete Spalten am Ziel des Datenpfads zu ignorieren. Die Schaltfläche "Vorschau der Änderungen" zeigt eine Liste der Änderungen an, die auftreten, wenn Sie auf die Schaltfläche "OK" klicken.  
  
  
