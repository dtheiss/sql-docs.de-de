---
title: Berichts-Manager, um die Übergabe von benutzerdefinierten Authentifizierungscookies konfigurieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6787ec73d91b32e0bdb90f8a5f25499f0ac35620
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56034490"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a>Konfigurieren des Berichts-Managers für die Übergabe von benutzerdefinierten Authentifizierungscookies
  Falls Sie eine benutzerdefinierte Authentifizierungserweiterung verwenden, sollten Sie den Berichts-Manager für die Übertragung von benutzerdefinierten Authentifizierungscookies konfigurieren. Andernfalls überträgt der Berichts-Manager Cookies nur über HTTP-Anforderungen, die auf den Berichtsserver beschränkt sind. Sollen zusätzliche Cookies übertragen werden, müssen Sie Änderungen an der Datei RSReportServer.Config vornehmen.  
  
## <a name="modifying-the-rsreportserverconfig-file"></a>Ändern der Datei RSReportServer.Config  
 Sie können den Berichts-Manager für die Übertragung zusätzlicher Cookies über den Berichtsserver aktivieren, indem Sie den Konfigurationseinstellungen des Berichts-Managers in der Datei "RSReportServer.config" ein <`PassThroughCookies`>-Element hinzufügen. Die Übertragung zusätzlicher Cookies ist vor allem bei Verwendung einer Authentifizierungslösung mit einmaliger Anmeldung nützlich, die nicht nur die Authentifizierungscookies des Berichtsservers, sondern auch Cookies der Authentifizierungssysteme von Drittanbietern benötigt.  
  
 Um zusätzliche Cookies zu aktivieren, die über HTTP-Anforderungen übertragen werden sollen, wenn der Berichts-Manager verwendet wird, legen Sie in der Datei RSReportServer.config die folgenden Elemente fest:  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Authentifizierung mit dem Berichtsserver](authentication-with-the-report-server.md)   
 [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md)   
 [Übersicht über Sicherheitserweiterungen](../extensions/security-extension/security-extensions-overview.md)   
 [Konfigurieren und Verwalten eines Berichtsservers &#40;einheitlicher SSRS-Modus&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
