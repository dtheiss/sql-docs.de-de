---
title: Cancel-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Cancel method [RDS]
ms.assetid: 560b5b3d-fba9-4275-8920-9c3e186134f7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 391287674153beffc82716995fa5f49443f77239
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51605960"
---
# <a name="cancel-method-rds"></a>Cancel-Methode (RDS)
Bricht die Ausführung einer ausstehenden asynchronen Methodenaufrufs aufgerufen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RDS.DataControl.Cancel  
```  
  
## <a name="remarks"></a>Hinweise  
 Beim Aufruf **Abbrechen**, [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) wird automatisch festgelegt, um **AdcReadyStateLoaded**, und die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) leer.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Cancel – Methodenbeispiel (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Cancel-Methode (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate-Methode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate-Methode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [ExecuteOptions-Eigenschaft (RDS)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


