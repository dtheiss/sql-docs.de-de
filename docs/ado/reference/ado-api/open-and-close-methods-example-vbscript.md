---
title: Öffnen und schließen Sie die Methode – Beispiel (VBScript) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Close method [ADO], VBScript example
- Open method [ADO], VBScript example
ms.assetid: 66eca011-e258-4d8f-bd67-e017bcf0871b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 375ebc025368551ccf9fda9dfba299027e6225ab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47709208"
---
# <a name="open-and-close-methods-example-vbscript"></a>Open- und Close-Methode – Beispiel (VBScript)
Dieses Beispiel verwendet die [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) und [schließen](../../../ado/reference/ado-api/close-method-ado.md) Methoden auf beiden [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) und [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekte, die geöffnet wurden.  
  
 Verwenden Sie das folgende Beispiel in einer Active Server Page (ASP). Verwenden Sie **finden** suchen Sie die Datei Adovbs.inc, und fügen ihn in das Verzeichnis, das Sie verwenden möchten. Ausschneiden und fügen Sie den folgenden Code in Editor oder einem anderen Texteditor und speichern Sie ihn als **OpenVBS.asp**. Sie können das Ergebnis in einem beliebigen Browser anzeigen.  
  
```  
<!-- BeginOpenVBS -->  
<%@ Language=VBScript %>  
<%' use this meta tag instead of adovbs.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
<HTML>  
<HEAD>  
<META name="VI60_DefaultClientScript"  content=VBScript>  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<title>ADO Open Method</title>  
<STYLE>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</STYLE>  
</HEAD>  
  
<BODY>  
<H3>ADO Open Method</H3>  
  
<TABLE WIDTH=600 BORDER=0>  
<TR>  
<TD VALIGN=TOP COLSPAN=3>  
<FONT SIZE=2>  
<% ' to integrate/test this code replace the   
   ' Data Source value in the Connection string%>  
<%   
    ' connection and recordset variables  
    Dim Cnxn, strCnxn  
    Dim rsCustomers, strSQLCustomers  
    Dim rsProducts, strSQLProducts  
  
    ' open connection  
    Set Cnxn = Server.CreateObject("ADODB.Connection")  
    strCnxn = "Provider='sqloledb';Data Source=" & _  
            Request.ServerVariables("SERVER_NAME") & ";" & _  
            "Integrated Security='SSPI';Initial Catalog='Northwind';"  
  
    Cnxn.Open strCnxn  
  
    ' create and open first Recordset using Connection - execute  
    Set rsCustomers = Server.CreateObject("ADODB.Recordset")  
    strSQLCustomers = "SELECT CompanyName, ContactName, City FROM Customers"  
    Set rsCustomers = Cnxn.Execute(strSQLCustomers)   
  
    ' create and open second Recordset using recordset - open  
    Set rsProducts = Server.CreateObject("ADODB.Recordset")  
    strSQLProducts = "SELECT ProductName, UnitPrice FROM Products"  
    rsProducts.Open strSQLProducts, Cnxn, adOpenDynamic, adLockPessimistic, adCmdText  
    %>  
  
    <TABLE COLSPAN=8 CELLPADDING=5 BORDER=0>  
    <!-- BEGIN column header row for Customer Table-->  
    <TR CLASS=thead>  
       <TD>Company Name</TD>  
       <TD>Contact Name</TD>  
       <TD>City</TD>  
    </TR>  
  
    <!--Display ADO Data from Customer Table-->  
    <% Do Until rsCustomers.EOF %>  
    <TR CLASS=tbody>  
      <TD> <%=rsCustomers("CompanyName")%> </TD>  
      <TD> <%=rsCustomers("ContactName")%></TD>  
      <TD> <%=rsCustomers("City")%> </TD>  
    </TR>   
    <%rsCustomers.MoveNext   
    Loop   
    %>  
    </TABLE>  
  
    <HR>  
  
    <TABLE COLSPAN=8 CELLPADDING=5 BORDER=0>  
    <!-- BEGIN column header row for Product List Table-->  
  
    <TR CLASS=thead2>  
       <TD>Product Name</TD>  
       <TD>Unit Price</TD>  
    </TR>  
    <!-- Display ADO Data Product List-->  
    <% Do Until rsProducts.EOF %>  
      <TR CLASS=tbody>    
      <TD> <%=rsProducts("ProductName")%> </TD>  
      <TD> <%=rsProducts("UnitPrice")%> </TD>  
      </TR>  
      <!--  Next Row = Record -->  
    <%rsProducts.MoveNext   
    Loop   
  
    ' clean up  
    If rsProducts.State = adStateOpen then  
        rsProducts.Close  
    End If  
    If rsCustomers.State = adStateOpen then  
        rsCustomers.Close  
    End If  
    If Cnxn.State = adStateOpen then  
        Cnxn.Close  
    End If  
    Set rsProducts = Nothing  
    Set rsCustomers = Nothing  
    Set Cnxn = Nothing  
  
    %>  
    </TABLE>  
  
</BODY>  
</HTML>  
<!-- EndOpenVBS -->  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Close-Methode (ADO)](../../../ado/reference/ado-api/close-method-ado.md)   
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Open Sie-Methode (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open Sie-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
