---
title: "Weglassen von Werten für optionale Webdienstobjekte | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 890b0d174e5277f45db91db23725ae203edf4e2f
ms.contentlocale: de-de
ms.lasthandoff: 06/13/2017

---
# <a name="omitting-values-for-optional-web-service-objects"></a>Weglassen von Werten für optionale Webdienstobjekte
  Eigenschaften von mehreren der Report Server Web Service komplexen Typen haben eine zugehörige Eigenschaft, die als die angegebene Eigenschaft bezeichnet. Der Name der Eigenschaft setzt sich aus dem ursprünglichen Eigenschaftennamen und dem daran angefügten Wort "Specified" zusammen. Wenn diese Eigenschaft vorhanden ist, bedeutet dies, dass ein Wert für die ursprüngliche Eigenschaft unter Umständen manchmal weggelassen wird. Das ist das direkte Ergebnis der Übersetzung aus WSDL (Web Service Description Language) in eine [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Proxyklasse. Beispiel: Die Webdiensteigenschaft <xref:ReportService2010.DataSourceDefinition.Enabled%2A> des komplexen Typs <xref:ReportService2010.DataSourceDefinition> besitzt eine zugehörige Eigenschaft mit dem Namen <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>. Wenn Sie eine Anwendung erstellen und nicht für einen Wert festlegen möchten die <xref:ReportService2010.DataSourceDefinition.Enabled%2A> -Eigenschaft, Sie müssen keine Bereitstellung eines Werts für <xref:ReportService2010.DataSourceDefinition.Enabled%2A>; der Standardwert von **"true"** verwendet wird. Müssen Sie jedoch immer noch festlegen <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> auf **"false"**. Wenn Sie angeben, dass einen Wert für die <xref:ReportService2010.DataSourceDefinition.Enabled%2A> -Eigenschaft, die Sie festlegen müssen <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> gleich **"true"**. Das ist bei schreibbaren Eigenschaften der Fall. Für schreibgeschützte Eigenschaften müssen Sie keine Aktion durchführen.  
  
> [!IMPORTANT]  
>  Wird keine Eigenschaft mit den oben genannten Vorgehensweisen festgelegt, kann dies zu unvorgesehenem Verhalten des Webdiensts führen.  
  
 Die Datentypen, die in der Regel benötigen Sie die zusätzliche angegebene Eigenschaft zu behandeln sind **booleschen**, **"DateTime"**, und **Enumeration**.  
  
 Ein Beispiel hierzu finden Sie unter <xref:ReportService2010.ReportingService2010.CreateDataSource%2A>-Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Technische Referenz &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  