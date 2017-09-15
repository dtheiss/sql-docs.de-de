---
title: CERTENCODED (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CERTENCODED
- CERTENCODED_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTENCODED
ms.assetid: 677a0719-7b9a-4f0b-bc61-41634563f924
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7596187fc97c0afd1df49f9de1e7ed168de5bcb
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="certencoded-transact-sql"></a>CERTENCODED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Gibt den öffentlichen Teil eines Zertifikats im Binärformat zurück. Diese Funktion akzeptiert eine Zertifikat-ID und gibt das codierte Zertifikat zurück. Das binäre Ergebnis kann an **CREATE CERTIFICATE … WITH BINARY** übergeben werden, um ein neues Zertifikat zu erstellen.
  
## <a name="syntax"></a>Syntax  
  
```sql
CERTENCODED ( cert_id )  
```  
  
## <a name="arguments"></a>Argumente  
*cert_id*  
Die **certificate_id** des Zertifikats. Diese Option ist verfügbar, über sys.certificates oder mithilfe der [CERT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/cert-id-transact-sql.md) Funktion. *cert_id* ist vom Typ **int**
  
## <a name="return-types"></a>Rückgabetypen
**varbinary**
  
## <a name="remarks"></a>Hinweise  
**CERTENCODED** und **CERTPRIVATEKEY** werden zusammen verwendet, um andere Teile eines Zertifikats in binärer Form zurückzugeben.
  
## <a name="permissions"></a>Berechtigungen  
**CERTENCODED** ist Öffentlichkeit zur Verfügung.
  
## <a name="examples"></a>Beispiele  
  
### <a name="simple-example"></a>Einfaches Beispiel  
Im folgenden Beispiel wird ein Zertifikat mit dem Namen `Shipping04` erstellt. Dann wird die **CERTENCODED** -Funktion verwendet, um die binäre Codierung des Zertifikats zurückzugeben.
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE CERTIFICATE Shipping04   
ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20161031';  
GO  
SELECT CERTENCODED(CERT_ID('Shipping04'));  
  
```  
  
### <a name="b-copying-a-certificate-to-another-database"></a>B. Kopieren eines Zertifikats in eine andere Datenbank  
Im folgenden etwas komplizierteren Beispiel werden zwei Datenbanken, `SOURCE_DB` und `TARGET_DB`, erstellt. Das Ziel ist, in der Datenbank `SOURCE_DB`ein Zertifikat zu erstellen und das Zertifikat in die Datenbank `TARGET_DB`zu kopieren. Dann wird veranschaulicht, dass in `SOURCE_DB` verschlüsselte Daten mithilfe der Kopie des Zertifikats in `TARGET_DB` entschlüsselt werden können.
  
Erstellen Sie die Datenbanken `SOURCE_DB` und `TARGET_DB` und einen Hauptschlüssel in jeder Datenbank, um die Beispielumgebung zu erzeugen. Erstellen Sie dann in `SOURCE_DB`ein Zertifikat.
  
```sql
USE master;  
GO  
CREATE DATABASE SOURCE_DB;  
GO  
USE SOURCE_DB;  
GO  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0URCE_DB KEY Pa$$W0rd';  
GO  
CREATE DATABASE TARGET_DB;  
GO  
USE TARGET_DB  
GO  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Pa$$W0rd in TARGET_DB';  
GO  
  
-- Create a certificate in SOURCE_DB  
USE SOURCE_DB;  
GO  
CREATE CERTIFICATE SOURCE_CERT WITH SUBJECT = 'SOURCE_CERTIFICATE';  
GO  
```  
  
Extrahieren Sie jetzt die binäre Beschreibung des Zertifikats.
  
```sql
DECLARE @CERTENC VARBINARY(MAX);  
DECLARE @CERTPVK VARBINARY(MAX);  
SELECT @CERTENC = CERTENCODED(CERT_ID('SOURCE_CERT'));  
SELECT @CERTPVK = CERTPRIVATEKEY(CERT_ID('SOURCE_CERT'),  
       'CertEncryptionPa$$word');  
SELECT @CERTENC AS BinaryCertificate;  
SELECT @CERTPVK AS EncryptedBinaryCertificate;  
GO  
```  
  
Erstellen Sie das doppelte Zertifikat in der Datenbank `TARGET_DB` . Sie müssen den folgenden Code ändern, indem Sie die beiden im vorherigen Schritt zurückgegebenen Binärwerte einfügen.
  
```sql
-- Create the duplicate certificate in the TARGET_DB database  
USE TARGET_DB  
GO  
CREATE CERTIFICATE TARGET_CERT  
FROM BINARY = <insert the binary value of the @CERTENC variable>  
WITH PRIVATE KEY (  
BINARY = <insert the binary value of the @CERTPVK variable>  
, DECRYPTION BY PASSWORD = 'CertEncryptionPa$$word');  
-- Compare the certificates in the two databases  
-- The two certificates should be the same   
-- except for name and (possibly) the certificate_id  
SELECT * FROM SOURCE_DB.sys.certificates  
UNION  
SELECT * FROM TARGET_DB.sys.certificates;  
```  
  
Mit dem folgenden Code, der wie ein einzelner Stapel ausgeführt wird, wird veranschaulicht, dass in `SOURCE_DB` verschlüsselte Daten in `TARGET_DB`entschlüsselt werden können.
  
```sql
USE SOURCE_DB;  
  
DECLARE @CLEARTEXT nvarchar(100);  
DECLARE @CIPHERTEXT varbinary(8000);  
DECLARE @UNCIPHEREDTEXT_Source nvarchar(100);  
SET @CLEARTEXT = N'Hello World';  
SET @CIPHERTEXT = ENCRYPTBYCERT(CERT_ID('SOURCE_CERT'), @CLEARTEXT);  
SET @UNCIPHEREDTEXT_Source =   
    DECRYPTBYCERT(CERT_ID('SOURCE_CERT'), @CIPHERTEXT)  
-- Encryption and decryption result in SOURCE_DB  
SELECT @CLEARTEXT AS SourceClearText, @CIPHERTEXT AS SourceCipherText,   
       @UNCIPHEREDTEXT_Source AS SourceDecryptedText;  
  
-- SWITCH DATABASE  
USE TARGET_DB;  
  
DECLARE @UNCIPHEREDTEXT_Target nvarchar(100);  
SET @UNCIPHEREDTEXT_Target = DECRYPTBYCERT(CERT_ID('TARGET_CERT'), @CIPHERTEXT);  
-- Encryption and decryption result in TARGET_DB  
SELECT @CLEARTEXT AS ClearTextInTarget, @CIPHERTEXT AS CipherTextInTarget, @UNCIPHEREDTEXT_Target AS DecriptedTextInTarget;   
GO  
```  
  
## <a name="see-also"></a>Siehe auch
[Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[CERTPRIVATEKEY &#40; Transact-SQL &#41;](../../t-sql/functions/certprivatekey-transact-sql.md)  
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  
