---
title: Tutorial für datenbankinterne Python-Analyse für SQL-Entwickler – SQL Server-Machine Learning
description: Informationen Sie zum Einbetten von Python-Code in SQL Server gespeicherte Prozeduren und T-SQL-Funktionen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ab28dafe062d7a8d492e702aa5570881ef77f1e0
ms.sourcegitcommit: 2e8783e6bedd9597207180941be978f65c2c2a2d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2019
ms.locfileid: "54405620"
---
# <a name="tutorial-python-data-analytics-for-sql-developers"></a>Lernprogramm: Python-Data-Analysen für SQL-Entwickler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Tutorial für die SQL-Programmierer erfahren Sie mehr über Python-Integration durch Erstellen und Bereitstellen einer Python-basiertes-Machine learning-Lösung mit einem [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) Datenbank auf SQL Server. Verwenden Sie T-SQL und SQL Server Management Studio eine Datenbank-Engine-Instanz mit [Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) und Python-sprachunterstützung.

Dieses Tutorial führt Sie in Python-Funktionen, die in einem Workflow der Modellierung verwendet. Schritte schließen das Durchsuchen von Daten, erstellen und Trainieren ein binärklassifizierungsmodell für und Bereitstellung eines Modells. Verwenden Sie Beispieldaten aus der New York City Taxi und Limosine Kommission und das Modell, das Sie erstellen vorhersagt, ob eine Fahrt wahrscheinlich zu einer QuickInfo, die basierend auf dem der Tag, Wegstrecke und einstiegsort ist. 

Alle von der Python-Code in diesem Tutorial verwendete wird in gespeicherten Prozeduren, die Sie erstellen, und führen Sie in Management Studio eingebunden.

> [!NOTE]
> Dieses Tutorial ist in R und Python verfügbar. Für die R-Version finden Sie unter [datenbankinterne Analysen für R-Entwicklern](sqldev-in-database-r-for-sql-developers.md).

## <a name="overview"></a>Übersicht

Der Prozess der Erstellung einer Machine Learning-Lösung ist ein komplexes, die mehrere Tools und die Koordination von Experten in mehreren Phasen umfassen können:

+ Abrufen und Bereinigen von Daten
+ Untersuchen der Daten und Erstellen von Features, die für die Modellierung hilfreich.
+ Trainieren und Optimieren des Modells
+ Bereitstellung in der Produktion

Entwickeln und Testen von den tatsächlichen Code, wird am besten mit einer dedizierten Umgebung ausgeführt. Allerdings nachdem das Skript vollständig getestet ist, können Sie ganz einfach bereitstellen damit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren in der vertrauten Umgebung von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Externen Code in gespeicherten Prozeduren Wrapping ist der primäre Mechanismus zum operationalisieren von Code in SQL Server.

Ob Sie eine SQL-Programmierer noch nicht mit Python oder ein Python-Entwickler, die noch nicht mit SQL sind, wird diesem mehrteiligen Tutorial einen typischen Workflow für die Durchführung von Analysen mit Python und SQL Server eingeführt. 

+ [Lektion 1: Untersuchen und Visualisieren von Daten mithilfe von Python](sqldev-py3-explore-and-visualize-the-data.md)

+ [Lektion 2: Erstellen von Datenfunktionen mit benutzerdefinierten SQL-Funktionen](sqldev-py4-create-data-features-using-t-sql.md)

+ [Lektion 3: Trainieren und Speichern eines Python-Modells mit T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [Lektion 4: Vorhersagen von möglichen Ergebnissen, die mit einem Python-Modell in einer gespeicherten Prozedur](sqldev-py6-operationalize-the-model.md)

Nachdem das Modell in der Datenbank gespeichert wurde, können Sie das Modell für Vorhersagen Aufrufen [!INCLUDE[tsql](../../includes/tsql-md.md)] mit gespeicherten Prozeduren.

## <a name="prerequisites"></a>Erforderliche Komponenten

+ [SQL Server 2017-Machine-Learning-Dienste mit Python](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Berechtigungen](../security/user-permission.md)

+ [NYC Taxi-Demo-Datenbank](demo-data-nyctaxi-in-sql.md)

Alle Vorgänge erfolgen mit [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

In diesem Tutorial wird davon ausgegangen, Vertrautheit mit grundlegender Datenbankvorgänge wie das Erstellen von Datenbanken und Tabellen, Importieren von Daten und SQL-Abfragen schreiben. Es wird nicht davon ausgegangen, dass Sie Python kennen. Daher wird allen Python-Code bereitgestellt. 

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Untersuchen und Visualisieren von Daten mithilfe von Python](sqldev-py3-explore-and-visualize-the-data.md)
