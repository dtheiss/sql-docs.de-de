---
title: Prozeduren aktualisiert Methodenbeispiel (VB) | Microsoft Docs
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Refresh method [ADOX], Visual Basic example
ms.assetid: 499679bd-287b-487d-bdfb-3803abffec1c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d0a9122b1adaa6d5a070bb568605b20a04199d95
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="procedures-refresh-method-example-vb"></a>Prozeduren aktualisiert Methodenbeispiel (VB)
Der folgende Code zeigt die Vorgehensweise beim Aktualisieren der [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md) Auflistung von einem [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md). Dies ist erforderlich, bevor Sie [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md) Objekte aus der **Katalog** zugegriffen werden kann.  
  
```  
' BeginProceduresRefreshVB  
Sub Main()  
    On Error GoTo ProcedureRefreshError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Catalog  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Refresh the Procedures collection  
    cat.Procedures.Refresh  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
ProcedureRefreshError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndProceduresRefreshVB  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Prozeduren-Auflistung (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Refresh-Methode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)