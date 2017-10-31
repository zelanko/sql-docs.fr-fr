---
title: CERTPRIVATEKEY (Transact-SQL) | Documents Microsoft
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
- CERTPRIVATEKEY
- CERTPRIVATEKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTPRIVATEKEY
ms.assetid: 33e0f01e-39ac-46da-94ff-fe53b1116df4
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 11a44f9203f9242a8f90ce3ca667bc1fea479dc2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="certprivatekey-transact-sql"></a>CERTPRIVATEKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Retourne la clé privée d'un certificat au format binaire. Cette fonction accepte trois arguments.
-   Un ID de certificat.  
-   Un mot de passe de chiffrement utilisé pour chiffrer les bits de clé privée lorsqu'ils sont retournés par la fonction, afin que les clés ne soient pas exposées en texte clair aux utilisateurs.  
-   Un mot de passe de déchiffrement qui est facultatif. Si un mot de passe de déchiffrement est spécifié, il est utilisé pour déchiffrer la clé privée du certificat, sinon la clé principale de la base de données est utilisée.  
  
Seuls les utilisateurs qui ont accès à la clé privée du certificat peuvent utiliser cette fonction. Cette fonction retourne la clé privée au format PVK.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CERTPRIVATEKEY   
    (  
          cert_ID   
        , ' encryption_password '   
      [ , ' decryption_password ' ]  
    )  
```  
  
## <a name="arguments"></a>Arguments  
*id_certificat*  
Est la **id_certificat** du certificat. Cette option est disponible à partir de sys.certificates ou à l’aide de la [CERT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/cert-id-transact-sql.md) (fonction). *cert_id* est de type **int**
  
*encryption_password*  
Mot de passe utilisé pour chiffrer la valeur binaire retournée.
  
*decryption_password*  
Mot de passe utilisé pour déchiffrer la valeur binaire retournée.
  
## <a name="return-types"></a>Types de retour
**varbinary**
  
## <a name="remarks"></a>Notes  
**CERTENCODED** et **CERTPRIVATEKEY** sont utilisés ensemble pour retourner les différentes parties d’un certificat sous forme binaire.
  
## <a name="permissions"></a>Permissions  
**CERTPRIVATEKEY** est disponible au public.
  
## <a name="examples"></a>Exemples  
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Use 5tr0ng P^55Words'  
GO  
CREATE CERTIFICATE Shipping04   
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20141031';  
GO  
SELECT CERTPRIVATEKEY(CERT_ID('Shipping04'), 'jklalkaa/; uia3dd');  
```  
  
Pour obtenir un exemple plus complexe qui utilise **CERTPRIVATEKEY** et **CERTENCODED** pour copier un certificat à une autre base de données, consultez l’exemple B dans la rubrique [CERTENCODED &#40; Transact-SQL &#41; ](../../t-sql/functions/certencoded-transact-sql.md).
  
## <a name="see-also"></a>Voir aussi
[Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[CRÉER un certificat &#40; Transact-SQL &#41; ](../../t-sql/statements/create-certificate-transact-sql.md) 
 [Fonctions de sécurité &#40; Transact-SQL &#41; ](../../t-sql/functions/security-functions-transact-sql.md) 
 [sys.certificates &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  

