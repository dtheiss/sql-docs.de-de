---
title: Erteilen von Datenbankberechtigungen (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Analysis Services], full control
- full control permissions [Analysis Services]
ms.assetid: be7e5f64-af43-47d6-84a5-c5c1c277d644
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6bac9958c7b906a52b5b0d9d28a37c31d280b836
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149010"
---
# <a name="grant-database-permissions-analysis-services"></a>Erteilen von Datenbankberechtigungen (Analysis Services)
  Wenn Sie Datenbanken mit Analysis Services verwalten und bereits über Kenntnisse zu relationalen Datenbanken verfügen, müssen Sie zuerst verstehen, dass in Bezug auf Datenzugriff die Datenbank nicht das primäre sicherungsfähige Objekt in Analysis Services ist.  
  
 Die primäre Abfragestruktur in Analysis Services ist ein Cube (oder ein tabellarisches Modell), mit Benutzerberechtigungen, die für diese bestimmten Objekte festgelegt sind. Im Gegensatz zur relationalen Datenbank-Engine, bei dem Datenbankanmeldenamen und Benutzerberechtigungen (oft `db_datareader`) für die Datenbank selbst festgelegt sind, ist eine Analysis Services-Datenbank hauptsächlich ein Container für die Hauptabfrageobjekte in einem Datenmodell. Wenn Sie hauptsächlich den Datenzugriff für einen Cube oder ein tabellarisches Modell aktivieren möchten, können Sie zunächst die Datenbankberechtigungen umgehen und sich direkt diesem Thema zuwenden: [Erteilen von Cube- oder Modellberechtigungen &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md).  
  
 Datenbankberechtigungen in Analysis Services ermöglichen administrative Funktionen. Weitgefasst gilt dies, wie es der Fall bei der Datenbankberechtigung Vollzugriff ist, oder granularer, wenn Sie die Verarbeitung von Vorgängen delegieren. Berechtigungsebenen für eine Analysis Services-Datenbank können Sie im Bereich **Allgemein** mit dem Dialogfeld **Rolle erstellen** festlegen. Dies wird in der folgenden Grafik gezeigt und nachstehend beschrieben.  
  
 Es gibt in Analysis Services keine Anmeldenamen. Sie erstellen einfach Rollen und weisen im Bereich **Mitgliedschaft** Windows-Konten zu. Alle Benutzer, einschließlich der Administratoren, stellen die Verbindung zu Analysis Services über ein Windows-Konto her.  
  
 ![Erstellen der Rolle Berechtigungen für die Datenbank von Dialogfeld zeigt](../media/ssas-permsdbrole.png "Rolle Berechtigungen für Dialogfeld zeigt die Datenbank erstellen.")  
  
 Auf Datenbankebene gibt es drei Berechtigungstypen.  
  
 **Vollzugriff (Administrator)** ─ Vollzugriff ist eine globale Berechtigung, die viele Zugriffsmöglichkeiten in einer Analysis Services-Datenbank mit sich bringt, z.B. die Fähigkeit, jedes Objekt in der Datenbank abzufragen oder zu verarbeiten und die Rollensicherheit zu verwalten. Vollzugriff entspricht dem Datenbankadministratorstatus. Wenn Sie `Full Control` auswählen, werden die Berechtigungen `Process Database` und `Read Definition` ebenfalls ausgewählt und können nicht entfernt werden.  
  
> [!NOTE]  
>  Serveradministratoren (Mitglieder der Serveradministratorrolle) besitzen ebenfalls impliziten Vollzugriff auf jede Datenbank auf dem Server.  
  
 `Process Database` Lautet diese Berechtigung wird verwendet, um die Verarbeitung auf Datenbankebene zu delegieren. Als Administrator können Sie diesen Task auslagern, indem Sie eine Rolle erstellen, mit der eine andere Person oder ein Dienst Verarbeitungsvorgänge für ein beliebiges Objekt in der Datenbank aufrufen kann. Alternativ können Sie auch Rollen für die Verarbeitung bestimmter Objekte erstellen. Weitere Informationen finden Sie unter [Grant process permissions &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md) .  
  
 `Read Definition` Lautet, die diese Berechtigung, die Möglichkeit zum Lesen der Metadaten des Objekts gewährt, die Fähigkeit zum Anzeigen der zugehörigen Daten. Meist wird diese Berechtigung für Rollen verwendet, die für die dedizierte Verarbeitung erstellt wurden. Dadurch können dann Tools wie [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] oder [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] für die interaktive Verarbeitung einer Datenbank verwendet werden. Ohne `Read Definition` ist die Berechtigung `Process Database` nur in Skriptszenarios effektiv. Wenn Sie planen, Verarbeitung, vielleicht durch SSIS oder ein anderes Zeitplanungsmodul automatisieren, Sie wahrscheinlich eine Rolle erstellen möchten, die `Process Database` ohne `Read Definition`. Erwägen Sie andernfalls, die beiden Eigenschaften in derselben Rolle zu kombinieren, um unbeaufsichtigte und interaktive Verarbeitung mit SQL Server-Tools zu unterstützen, die das Datenmodell auf einer Benutzeroberfläche grafisch darstellen.  
  
## <a name="full-control-administrator-permissions"></a>Berechtigung Vollzugriff (Administrator)  
 In [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ist jede Windows-Benutzeridentität, die einer Rolle mit Berechtigung Vollzugriff (Administrator) zugewiesen ist, ein Datenbankadministrator. Ein Datenbankadministrator kann jeden Task innerhalb der Datenbank ausführen, einschließlich:  
  
-   Verarbeiten von Objekten  
  
-   Lesen von Daten und Metadaten für alle Objekte in der Datenbank, einschließlich Cubes, Dimensionen, Measure-Gruppen, Perspektiven und Data Mining-Modelle  
  
-   Erstellen oder Anpassen von Datenbankrollen durch Hinzufügen von Benutzern oder Berechtigungen, einschließlich Hinzufügen von Benutzern zu Rollen mit der Berechtigung Vollzugriff  
  
-   Löschen von Datenbankrollen oder Rollenmitgliedschaften  
  
-   Registrieren von Assemblys (oder gespeicherten Prozeduren) für die Datenbank  
  
 Beachten Sie, dass Datenbankadministratoren keine Datenbanken auf dem Server hinzufügen oder löschen und für andere Datenbanken auf demselben Server auch keine Administratorrechte gewähren können. Diese Berechtigung besitzen nur Serveradministratoren. Finden Sie unter [Erteilen von Serveradministratorberechtigungen &#40;Analysis Services&#41; ](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) für Weitere Informationen zu dieser Berechtigungsebene.  
  
 Da alle Rollen über den Benutzer definiert werden, wird empfohlen, dass Sie für diesen Zweck eine Rolle erstellen (zum Beispiel mit dem Namen "dbadmin") und dann Windows-Konten von Benutzern und Gruppen entsprechend zuweisen.  
  
#### <a name="create-roles-in-ssms"></a>Erstellen von Rollen in SSMS  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]eine Verbindung mit der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz her, öffnen Sie den Ordner **Datenbanken** , wählen Sie eine Datenbank aus, klicken Sie mit der rechten Maustaste auf **Rollen** | **Neue Rolle**.  
  
2.  Geben Sie im Bereich **Allgemein** einen Namen ein, zum Beispiel DBAdmin.  
  
3.  Aktivieren Sie das Kontrollkästchen **Vollzugriff (Administrator)** für den Cube. Beachten Sie, dass `Process Database` und `Read Definition` automatisch ausgewählt werden. Diese beiden Berechtigungen sind immer in Rollen enthalten enthalten `Full Control`.  
  
4.  Geben Sie im **Mitgliedschaft** sbereich die Windows-Konten von Benutzern und Gruppen ein, die mit dieser Rolle eine Verbindung zu Analysis Services herstellen.  
  
5.  Klicken Sie auf **OK** , um die Erstellung der Rolle zu abzuschließen.  
  
## <a name="process-database"></a>Process Database  
 Wenn eine Rolle definieren, die Datenbankberechtigungen gewährt, können Sie überspringen `Full Control` , und wählen Sie einfach `Process Database`. Diese Berechtigung ermöglicht auf Datenbankebene die Verarbeitung aller Objekte innerhalb der Datenbank. Weitere Informationen finden Sie unter [Grant process permissions &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
## <a name="read-definition"></a>Read Definition  
 Wie `Process Database`, wobei `Read Definition` Berechtigungen auf Datenbankebene hat einen kaskadierenden Effekt auf andere Objekte innerhalb der Datenbank. Wenn Sie Berechtigungen für das Lesen von Definitionen mit feinerer Granularität festlegen möchten, müssen Sie Im Bereich "Allgemein" "Definition lesen" als Datenbankeigenschaft entfernen. Weitere Informationen finden Sie unter [Erteilen von Berechtigungen zum Lesen von Definitionen für Objektmetadaten &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erteilen von Serveradministratorberechtigungen &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [Erteilen von verarbeitungsberechtigungen &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
  
