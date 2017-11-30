---
title: Erste Schritte mit SQL Server-2017 in der Cloud | Microsoft Docs
description: "Dieser Schnellstart-Lernprogramm zeigt, wie der SQL Server-2017 unter Linux in der Cloud Ihrer Wahl ausführen."
author: annashres
ms.author: annashres
manager: jhubbard
ms.date: 10/25/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.openlocfilehash: 0bc304b50930f8c8de5d244ea0b606add5f24d2f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="run-the-sql-server-2017-in-the-cloud"></a>Führen Sie die SQL Server-2017 in der cloud

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In diesem Schnellstart-Lernprogramm installieren Sie SQL Server-2017 unter Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) oder Ubuntu in der Cloud Ihrer Wahl. Wechseln Sie zu [Bereitstellen eines Linux SQL Server-virtuellen Computers im Azure-Portal](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json) zu SQL Server unter Linux in Azure ausgeführt wird.

    > [!NOTE]
    > If you choose to run a paid edition of SQL Server then you need to bring your own license (BYOL)

## <a name="amazon-web-services"></a>Amazon Web Services
1.  Erstellen Sie eine Linux AMI mit mindestens 3,25 GB Arbeitsspeicher vom marketplace 
    * [RHEL 7.3 +](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES v12 SP2](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  Herstellen einer Verbindung mit der AMI mit ssh
1.  Führen Sie den Schnellstart für die Linux-Distrbution, die Sie ausgewählt haben: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Für Remoteverbindungen zu konfigurieren: 
    * Öffnen der [EC2 Amazon-Konsole]( https://console.aws.amazon.com/ec2/)
    * Wählen Sie im Navigationsbereich **Sicherheitsgruppen**. 
    * Wählen Sie **eingehend, bearbeiten, Regel hinzufügen**
    * Fügen Sie eine eingehende Regel zum Zulassen von Datenverkehr an den Port auf dem SQL Server (standardmäßig TCP-Port 1433) lauscht hinzu

    
## <a name="digital-ocean"></a>Digitale "Ozean"
1. Melden Sie sich die [Systemsteuerung](https://cloud.digitalocean.com/login) und klicken Sie auf ein Droplet erstellen
1. Wählen Sie eine Ubuntu 16.04 Droplet mit mindestens 3,25 GB Arbeitsspeicher
1. Herstellen einer Verbindung mit der Droplet mit ssh
1. Führen Sie die [Ubuntu-Schnellstart](quickstart-install-connect-ubuntu.md)
1. Für Remoteverbindungen zu konfigurieren:
    * Am oberen Rand der Systemsteuerung, befolgen Sie die **Networking** verknüpfen, und wählen Sie dann **Firewalls**
    * Fügen Sie eine eingehende Regel zum Zulassen von Datenverkehr an den Port auf dem SQL Server (standardmäßig TCP-Port 1433) lauscht hinzu
    
## <a name="google-cloud-platform"></a>Google Cloud-Plattform
1.  Erstellen Sie eine Linux-Image mit mindestens 3,25 GB Arbeitsspeicher aus dem Cloud-Startprogramm 
    * [RHEL 7.3 +](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES v12 SP2](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  Herstellen einer Verbindung mit dem Image mit ssh
1.  Führen Sie den Schnellstart für die Linux-Distrbution, die Sie ausgewählt haben: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Für Remoteverbindungen zu konfigurieren: 
    * Wechseln Sie zu der [Firewall-Regeln](https://console.cloud.google.com/networking/firewalls)
    * Fügen Sie eine eingehende Regel zum Zulassen von Datenverkehr an den Port auf dem SQL Server (standardmäßig TCP: 1433) lauscht hinzu