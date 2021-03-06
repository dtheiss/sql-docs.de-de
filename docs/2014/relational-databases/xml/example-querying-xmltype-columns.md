---
title: 'Beispiel: Abfragen von Spalten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, querying XML example
ms.assetid: d9f3710d-7a2e-4abe-9c02-3e3c0df4d620
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0457f9eddad9130e5b486cd09e754c2059a586a5
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53373852"
---
# <a name="example-querying-xmltype-columns"></a>Beispiel: Abfragen von Spalten
  Die folgende Abfrage schließt Spalten vom Typ `xml` ein. Die Abfrage ruft die Produktmodell-ID, den Namen und die Produktionsschritte am ersten Standort aus der `Instructions`-Spalte vom Typ `xml` ab.  
  
## <a name="example"></a>Beispiel  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
')   
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
GO  
```  
  
 Im Folgenden wird das Ergebnis gezeigt. Beachten Sie, dass die Tabelle nur für einige Produktmodelle Fertigungsanweisungen speichert. Die Fertigungsschritte werden als Unterelemente des <`ProductModelData`>-Elements im Ergebnis zurückgegeben.  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
    <MI:step> ... </MI:step>  
    <MI:step> ... </MI:step>  
 </ProductModelData>  
```  
  
 Wenn in der Abfrage ein Spaltenname für die durch die XQuery-Abfrage zurückgegebenen XML-Daten angegeben wird (wie in der folgenden `SELECT`-Anweisung angegeben), werden die Produktionsschritte von dem Element umschlossen, das den angegebenen Namen aufweist.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
go  
```  
  
 Dies ist das Ergebnis:  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
  <ManuSteps>  
    <MI:step ... </MI:step>  
    <MI:step ... </MI:step>  
  </ManuSteps>  
</ProductModelData>  
```  
  
 In der folgenden Abfrage wird die `ELEMENTS` -Direktive angegeben. Deshalb ist das zurückgegebene Ergebnis elementzentriert. Die Option `XSINIL`, die zusammen mit der `ELEMENTS`-Direktive angegeben wird, gibt selbst dann <`ManuSteps`>-Elemente zurück, wenn die entsprechende Spalte im Rowset NULL ist.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData'), root('MyRoot'), ELEMENTS XSINIL  
go  
```  
  
 Dies ist das Ergebnis:  
  
```  
<MyRoot xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   ...  
  <ProductModelData>  
    <ProductModelID>6</ProductModelID>  
    <Name>HL Road Frame</Name>  
    <ManuSteps xsi:nil="true" />  
  </ProductModelData>  
  <ProductModelData>  
    <ProductModelID>7</ProductModelID>  
    <Name>HL Touring Frame</Name>  
    <ManuSteps>  
      <MI:step ... </MI:step>  
      <MI:step ...</MI:step>  
       ...  
    </ManuSteps>  
  </ProductModelData>  
</MyRoot>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md)  
  
  
