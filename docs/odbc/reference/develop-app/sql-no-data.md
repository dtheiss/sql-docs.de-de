---
title: SQL_NO_DATA | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 749351694a41764b9b5cc8bf3421340d62626aaf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47739888"
---
# <a name="sqlnodata"></a>SQL_NO_DATA
Wenn eine ODBC-3. *x* Anwendungsaufrufe **SQLExecDirect**, **SQLExecute**, oder **SQLParamData** in einer ODBC 2. *X* Treiber, führen Sie ein gesuchtes Update oder delete-Anweisung, die keine Zeilen in der Datenquelle, die der Treiber auswirkt, sollte SQL_SUCCESS, nicht SQL_NO_DATA zurückgegeben. Wenn eine ODBC-2. *x* oder ODBC-3. *X* Anwendung mit einer ODBC 3. *X* Treiber ruft **SQLExecDirect**, **SQLExecute**, oder **SQLParamData** dasselbe Ergebnis erzielt, die ODBC 3. *X* Treiber sollte SQL_NO_DATA zurückgegeben werden.
