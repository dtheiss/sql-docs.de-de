---
title: 'Beispiel: Angeben der ELEMENT-Direktive und Entitätscodierung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0e943e6dfb83d21d4a0e0beac0c6acd0d62881f1
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51667359"
---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a>Beispiel: Angeben der ELEMENT-Direktive und Entitätscodierung
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Dieses Beispiel veranschaulicht den Unterschied zwischen der **ELEMENT** - und der **XML** -Direktive. Bei der **ELEMENT** -Direktive werden die Daten in Entitäten geändert, während dies bei der **XML** -Direktive nicht der Fall ist. Dem Summary>\<-Element wird in der Abfrage XML zugewiesen: `<Summary>This is summary description</Summary>`.  
  
 Angenommen, die folgende Abfrage wird ausgeführt:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription!ELEMENT]  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        NULL,  
       '<Summary>This is summary description</Summary>'  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 Dies ist das Ergebnis. Die Zusammenfassungsbeschreibung wird im Ergebnis in eine Entität geändert.  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription><Summary>This is summary description</Summary></SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Wenn Sie nun im Spaltennamen die **XML** -Direktive angeben, also `Summary!2!SummaryDescription!XML`statt der **ELEMENT** -Direktive, erhalten Sie eine zusammenfassende Beschreibung, ohne dass die Daten in Entitäten geändert werden.  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <Summary>This is summary description</Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Die folgende Abfrage weist keinen statischen XML-Wert zu, sondern verwendet die **query()** -Methode vom **XML** -Typ, um die Produktmodell-Zusammenfassungsbeschreibung aus der CatalogDescription-Spalte vom **XML** -Typ abzurufen. Da bekannt ist, dass das Ergebnis vom Typ **xml** ist, werden die Daten nicht in Entitäten geändert.  
  
```  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
       (SELECT CatalogDescription.query('  
            declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
          /pd:ProductDescription/pd:Summary'))  
FROM     Production.ProductModel  
WHERE    CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],Tag  
FOR XML EXPLICIT  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden des EXPLICIT-Modus mit FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
