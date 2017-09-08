---
title: DECRYPTBYKEYAUTOCERT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/09/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECRYPTBYKEYAUTOCERT
- DECRYPTBYKEYAUTOCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DECRYPTBYKEYAUTOCERT function
ms.assetid: 6b45fa2e-ffaa-46f7-86ff-5624596eda4a
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0842000cd08e3ca82dab181f32ae96f4a0280d5d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# DECRYPTBYKEYAUTOCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet le déchiffrement à l'aide d'une clé symétrique qui est automatiquement déchiffrée avec un certificat.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntaxe  
  
```  
  
DecryptByKeyAutoCert ( cert_ID , cert_password   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }   
  [ , { authenticator | @authenticator } ] ] )  
```  
  
## Arguments  
 *cert_ID*  
 ID du certificat servant à protéger la clé symétrique. *cert_ID* est **int**.  
  
 *cert_password*  
 Mot de passe qui protège la clé privée du certificat. Peut être NULL si la clé privée est protégée par la clé principale de la base de données. *cert_password* est **nvarchar**.  
  
 '*texte chiffré*'  
 Données chiffrées avec la clé. *texte chiffré* est **varbinary**.  
  
 @ciphertext  
 Est une variable de type **varbinary** qui contient les données chiffrées avec la clé.  
  
 *add_authenticator*  
 Indique si un authentificateur a été chiffré en même temps que le texte en clair. Doit être la même valeur transmise à EncryptByKey lors du chiffrement des données. Est **1** si un authentificateur a été utilisé. *add_authenticator* est **int**.  
  
 @add_authenticator  
 Indique si un authentificateur a été chiffré en même temps que le texte en clair. Il doit s'agir de la valeur transmise à EncryptByKey lors du chiffrement des données.  
  
 *authentificateur*  
 Données à partir desquelles un authentificateur peut être généré. Doit correspondre à la valeur qui a été fournie à EncryptByKey. *l’authentificateur* est **sysname**.  
  
 @authenticator  
 Variable contenant les données à partir desquelles l'authentificateur sera généré. Doit correspondre à la valeur qui a été fournie à EncryptByKey.  
  
## Types de retour  
 **varbinary** avec une taille maximale de 8 000 octets.  
  
## Notes  
 DecryptByKeyAutoCert combine les fonctionnalités de OPEN SYMMETRIC KEY et de DecryptByKey. Dans une même opération, il déchiffre une clé symétrique et l'utilise pour déchiffrer le texte chiffré.  
  
## Permissions  
 Requiert l'autorisation VIEW DEFINITION sur la clé symétrique et CONTROL sur le certificat.  
  
## Exemples  
 L'exemple suivant montre comment utiliser `DecryptByKeyAutoCert` pour simplifier le code qui effectue le déchiffrement. Ce code doit être exécuté sur une base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] qui n'a pas encore de clé principale de base de données.  
  
```  
--Create the keys and certificate.  
USE AdventureWorks2012;  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'mzkvdlk979438teag$$ds987yghn)(*&4fdg^';  
OPEN MASTER KEY DECRYPTION BY PASSWORD = 'mzkvdlk979438teag$$ds987yghn)(*&4fdg^';  
CREATE CERTIFICATE HumanResources037   
   WITH SUBJECT = 'Sammamish HR',   
   EXPIRY_DATE = '10/31/2009';  
CREATE SYMMETRIC KEY SSN_Key_01 WITH ALGORITHM = DES  
    ENCRYPTION BY CERTIFICATE HumanResources037;  
GO  
----Add a column of encrypted data.  
ALTER TABLE HumanResources.Employee  
    ADD EncryptedNationalIDNumber varbinary(128);   
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037 ;  
UPDATE HumanResources.Employee  
SET EncryptedNationalIDNumber  
    = EncryptByKey(Key_GUID('SSN_Key_01'), NationalIDNumber);  
GO  
--  
--Close the key used to encrypt the data.  
CLOSE SYMMETRIC KEY SSN_Key_01;  
--  
--There are two ways to decrypt the stored data.  
--  
--OPTION ONE, using DecryptByKey()  
--1. Open the symmetric key  
--2. Decrypt the data  
--3. Close the symmetric key  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
SELECT NationalIDNumber, EncryptedNationalIDNumber    
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalIDNumber))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
CLOSE SYMMETRIC KEY SSN_Key_01;  
--  
--OPTION TWO, using DecryptByKeyAutoCert()  
SELECT NationalIDNumber, EncryptedNationalIDNumber   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKeyAutoCert ( cert_ID('HumanResources037') , NULL ,EncryptedNationalIDNumber))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
```  
  
## Voir aussi  
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [ENCRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

