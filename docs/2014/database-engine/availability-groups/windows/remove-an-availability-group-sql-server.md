---
title: Entfernen einer Verfügbarkeitsgruppe (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.deleteag.f1
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], dropping
ms.assetid: 4b7f7f62-43a3-49db-a72e-22d4d7c2ddbb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0d3ed68462736058ae386d8b5b6ad874f6fde8c0
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53362682"
---
# <a name="remove-an-availability-group-sql-server"></a>Entfernen einer Verfügbarkeitsgruppe (SQL Server)
  In diesem Thema wird beschrieben, wie eine AlwaysOn-Verfügbarkeitsgruppe mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]gelöscht wird. Wenn eine Serverinstanz, auf der eines der Verfügbarkeitsreplikate gehostet wird, offline ist, wenn Sie eine Verfügbarkeitsgruppe löschen, so wird das lokale Verfügbarkeitsreplikat von der Serverinstanz gelöscht, nachdem diese online geschaltet wurde. Beim Löschen einer Verfügbarkeitsgruppe werden sämtliche zugeordneten Verfügbarkeitsgruppenlistener gelöscht.  
  
 Beachten Sie, dass eine Verfügbarkeitsgruppe ggf. aus einem WSFC (Windows Server Failover Clustering)-Knoten gelöscht werden kann, der über die richtigen Sicherheitsanmeldeinformationen für die Verfügbarkeitsgruppe verfügt. Auf diese Weise können Sie eine Verfügbarkeitsgruppe löschen, wenn keine ihrer Verfügbarkeitsreplikate mehr vorhanden ist.  
  
> [!IMPORTANT]  
>  Entfernen Sie die Verfügbarkeitsgruppe wenn möglich nur, während eine Verbindung mit der Serverinstanz besteht, die das primäre Replikat hostet. Wenn die Verfügbarkeitsgruppe aus dem primären Replikat gelöscht wird, sind Änderungen in den früheren primären Datenbanken (ohne Hochverfügbarkeitsschutz) zulässig. Durch Löschen einer Verfügbarkeitsgruppe aus einem sekundären Replikat erhält das primäre Replikat den Status RESTORING und Änderungen an den Datenbanken sind nicht zulässig.  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen und Empfehlungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So löschen Sie eine Verfügbarkeitsgruppe mithilfe von:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   [Verwandte Inhalte](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen und Empfehlungen  
  
-   Wenn die Verfügbarkeitsgruppe online ist, bewirkt das Löschen aus einem sekundären Replikat den Übergang des primären Replikats in den Status RESTORING. Daher sollten Sie die Verfügbarkeitsgruppe möglichst nur aus der Serverinstanz entfernen, die das primäre Replikat hostet.  
  
-   Wenn Sie eine Verfügbarkeitsgruppe von einem Computer löschen, der aus dem WSFC-Failovercluster entfernt wurde, wird die Verfügbarkeitsgruppe nur lokal gelöscht.  
  
-   Löschen Sie eine Verfügbarkeitsgruppe nicht, wenn der WSFC-Cluster (Windows Server Failover Clustering) kein Quorum hat. Wenn Sie eine Verfügbarkeitsgruppe löschen müssen, solange der Cluster über kein Quorum verfügt, wird die Metadaten-Verfügbarkeitsgruppe, die im Cluster gespeichert ist, nicht entfernt. Nachdem der Cluster das Quorum wiedererlangt hat, müssen Sie die Verfügbarkeitsgruppe erneut löschen, um diese aus dem WSFC-Cluster zu entfernen.  
  
-   Auf einem sekundären Replikat sollte DROP AVAILABILITY GROUP nur im Notfall verwendet werden. Das liegt daran, dass durch Löschen einer Verfügbarkeitsgruppe die Verfügbarkeitsgruppe offline geschaltet wird. Wenn Sie die Verfügbarkeitsgruppe aus einem sekundären Replikat löschen, kann das primäre Replikat nicht bestimmen, ob der OFFLINE-Status aufgrund des Quorumverlusts, eines erzwungenen Failovers oder eines DROP AVAILABILITY GROUP-Befehls aufgetreten ist. Das primäre Replikat geht in den Status RESTORING über, um eine mögliche Split Brain-Situation zu verhindern. Weitere Informationen finden Sie unter [How It Works: DROP AVAILABILITY GROUP-Verhaltensweisen](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (Blog des CSS SQL Server-Ingenieuren).  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung. Um eine Verfügbarkeitsgruppe zu löschen, die nicht von der lokalen Serverinstanz gehostet wird, benötigen Sie die CONTROL SERVER-Berechtigung oder die CONTROL-Berechtigung für diese Verfügbarkeitsgruppe.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 **So löschen Sie eine Verfügbarkeitsgruppe**  
  
1.  Wenn möglich, stellen Sie in Objekt-Explorer eine Verbindung mit der Serverinstanz her, die das primäre Replikat hostet, oder stellen Sie eine Verbindung zu einer anderen Serverinstanz her, die für AlwaysOn-Verfügbarkeitsgruppen in einem WSFC-Knoten aktiviert ist, der die richtigen Sicherheitsanmeldeinformationen für die Verfügbarkeitsgruppe besitzt. Erweitern Sie die Serverstruktur.  
  
2.  Erweitern Sie den Knoten **Hohe Verfügbarkeit (immer aktiviert)** und den Knoten **Verfügbarkeitsgruppen** .  
  
3.  Dieser Schritt hängt davon ab, ob Sie mehrere Verfügbarkeitsgruppen oder nur eine Verfügbarkeitsgruppe löschen möchten:  
  
    -   Zum Löschen mehrerer Verfügbarkeitsgruppen, deren primären Replikate sich auf der verbundenen Serverinstanz befinden, verwenden Sie den Bereich **Details zum Objekt-Explorer**, um alle Verfügbarkeitsgruppen, die Sie löschen möchten, anzuzeigen und auszuwählen. Weitere Informationen finden Sie unter [Verwenden der Details zum Objekt-Explorer zum Überwachen von Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Zum Löschen einer einzelnen Verfügbarkeitsgruppe wählen Sie sie entweder im Bereich **Objekt-Explorer** oder im Bereich **Details zum Objekt-Explorer** aus.  
  
4.  Klicken Sie mit der rechten Maustaste auf die ausgewählte Verfügbarkeitsgruppe oder die Gruppen, und wählen Sie den Befehl **Löschen** aus.  
  
5.  Um im Dialogfeld **Verfügbarkeitsgruppe entfernen** alle aufgelisteten Verfügbarkeitsgruppen zu löschen, klicken Sie auf **OK**. Wenn Sie nicht alle aufgelisteten Verfügbarkeitsgruppen entfernen möchten, klicken Sie auf **Abbrechen**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So löschen Sie eine Verfügbarkeitsgruppe**  
  
1.  Wenn möglich, stellen Sie eine Verbindung mit der Serverinstanz her, die das primäre Replikat hostet, oder stellen Sie eine Verbindung zu einer anderen Serverinstanz her, die für AlwaysOn-Verfügbarkeitsgruppen in einem WSFC-Knoten aktiviert ist, der die richtigen Sicherheitsanmeldeinformationen für die Verfügbarkeitsgruppe besitzt.  
  
2.  Verwenden Sie die [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) -Anweisung wie folgt:  
  
     DROP AVAILABILITY GROUP *group_name*  
  
     Dabei ist *group_name* der Name der Verfügbarkeitsgruppe die gelöscht werden soll.  
  
     Im folgenden Beispiel wird die `MyAG` -Verfügbarkeitsgruppe gelöscht.  
  
    ```  
    DROP AVAILABILITY GROUP MyAG;  
    ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
 **So löschen Sie eine Verfügbarkeitsgruppe**  
  
 Im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Anbieter:  
  
1.  Wenn möglich, ändern sie das Verzeichnis (`cd`) zu der Serverinstanz, die das primäre Replikat hostet, oder stellen Sie eine Verbindung zu einer anderen Serverinstanz her, die für AlwaysOn-Verfügbarkeitsgruppen in einem WSFC-Knoten aktiviert ist, der die richtigen Sicherheitsanmeldeinformationen für die Verfügbarkeitsgruppe besitzt.  
  
2.  Verwenden Sie das **Remove-SqlAvailabilityGroup** -Cmdlet.  
  
     Beispielsweise wird die Verfügbarkeitsgruppe namens `MyAg`mit dem folgenden Befehl entfernt. Dieser Befehl kann auf jeder Serverinstanz ausgeführt werden, von der ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe gehostet wird.  
  
    ```  
    Remove-SqlAvailabilityGroup `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg  
    ```  
  
    > [!NOTE]  
    >  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [How It Works: DROP AVAILABILITY GROUP-Verhaltensweisen](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (Blog des CSS SQL Server-Ingenieuren)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Erstellung und Konfiguration von Verfügbarkeitsgruppen &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)  
  
  
