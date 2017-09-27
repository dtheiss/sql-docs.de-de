---
title: "Schritt 3: Ändern der Flat File Connection Manager | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 525557f034199c5e6823c18ab9fdb7c3b505a434
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-2-3---modifying-the-flat-file-connection-manager"></a>Lektion 2 – 3 – ändern die Flat File Connection Manager
In dieser Aufgabe ändern Sie den in Lektion 1 konfigurierten und erstellten Flatfile-Verbindungs-Manager. Bei der ursprünglichen Erstellung wurde der Flatfile-Verbindungs-Manager so konfiguriert, dass eine einzelne Datei statisch geladen wird. Damit der Flatfile-Verbindungs-Manager Dateien iterativ laden kann, müssen Sie die ConnectionString-Eigenschaft des Verbindungs-Managers so ändern, dass die benutzerdefinierte Variable `User:varFileName`, die den Pfad der zur Laufzeit zu ladenden Datei enthält, akzeptiert wird.  
  
Indem Sie den Verbindungs-Manager so ändern, dass er den Wert der benutzerdefinierten Variable `User::varFileName`verwendet, um die ConnectionString-Eigenschaft des Verbindungs-Managers aufzufüllen, kann der Verbindungs-Manager eine Verbindung mit verschiedenen Flatfiles herstellen. Zur Laufzeit aktualisiert dann jede Iteration des Foreach-Schleifencontainers die `User::varFileName` -Variable. Durch das Aktualisieren der Variable stellt der Verbindungs-Manager wiederum eine Verbindung zu einer anderen Flatfile her, und der Datenflusstask verarbeitet andere Daten.  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a>So konfigurieren Sie den Flatfile-Verbindungs-Manager auf die Verwendung einer Variable für die Verbindungszeichenfolge  
  
1.  Klicken Sie im Bereich **Verbindungs-Manager** mit der rechten Maustaste auf **Sample Flat File Source Data**(Beispielquelldaten von Flatfiles), und wählen Sie **Eigenschaften**aus.  
  
2.  Klicken Sie im Eigenschaftenfenster für **Ausdrücke**in die leere Zelle, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**.  
  
3.  Geben Sie im Dialogfeld **Eigenschaftsausdrucks-Editor** in der Spalte **Eigenschaft** die Option **ConnectionString**ein, oder wählen Sie sie aus.  
  
4.  Klicken Sie in der Spalte **Ausdruck** auf die Schaltfläche mit den Auslassungspunkten **(…)** , um das Dialogfeld **Ausdrucks-Generator** zu öffnen.  
  
5.  Erweitern Sie im Dialogfeld **Ausdrucks-Generator** den Knoten **Variablen** .  
  
6.  Ziehen Sie die Variable **User::varFileName**, in das Feld **Ausdruck** .  
  
7.  Klicken Sie auf **OK** , um das Dialogfeld **Ausdrucks-Generator** zu schließen.  
  
8.  Klicken Sie auf **OK** , um das Dialogfeld **Eigenschaftsausdrucks-Editor** zu schließen.  
  
## <a name="next-lesson-task"></a>Aufgabe in der nächsten Lektion  
[Schritt 4: Testen des Lektion 2-Tutorialpakets](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
  
