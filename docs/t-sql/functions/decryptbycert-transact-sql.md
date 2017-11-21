---
title: DECRYPTBYCERT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DecryptByCert_TSQL
- DECRYPTBYCERT
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], decryption
- decryption [SQL Server], certificates
- DECRYPTBYCERT function
ms.assetid: 4950d787-40fa-4e26-bce8-2cb2ceca12fb
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ebdc328e49635af823cd64e8539ee5b7cfa95c76
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="decryptbycert-transact-sql"></a>DECRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Déchiffre les données à l'aide de la clé privée d'un certificat.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DecryptByCert ( certificate_ID , { 'ciphertext' | @ciphertext }   
    [ , { 'cert_password' | @cert_password } ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *id_certificat*  
 Identificateur d'un certificat dans la base de données. *certificat*_ID est **int**.  
  
 *texte chiffré*  
 Chaîne de données chiffrée à l'aide de la clé publique du certificat.  
  
 @ciphertext  
 Est une variable de type **varbinary** qui contient les données qui ont été chiffrées avec le certificat.  
  
 *cert_password*  
 Mot de passe utilisé pour chiffrer la clé privée du certificat. Il doit s'agir d'une chaîne Unicode.  
  
 @cert_password  
 Est une variable de type **nchar** ou **nvarchar** qui contient le mot de passe utilisé pour chiffrer la clé privée du certificat. Il doit s'agir d'une chaîne Unicode.  
  
## <a name="return-types"></a>Types de retour  
 **varbinary** avec une taille maximale de 8 000 octets.  
  
## <a name="remarks"></a>Notes  
 Cette fonction déchiffre les données à l'aide de la clé privée d'un certificat. Les opérations de chiffrement/déchiffrement qui utilisent des clés asymétriques consomment une grande quantité de ressources. C'est pourquoi EncryptByCert et DecryptByCert ne conviennent pas pour le chiffrement régulier des données utilisateur.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation CONTROL sur le certificat.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant sélectionne des lignes de `[AdventureWorks2012].[ProtectedData04]` qui sont marquées en tant que `data encrypted by certificate JanainaCert02`. L'exemple déchiffre le texte chiffré à l'aide de la clé privée du certificat `JanainaCert02`, laquelle est préalablement déchiffrée à l'aide du mot de passe du certificat, `pGFD4bb925DGvbd2439587y`. Les données déchiffrées sont converties à partir de **varbinary** à **nvarchar**.  
  
```  
SELECT convert(nvarchar(max), DecryptByCert(Cert_Id('JanainaCert02'),  
    ProtectedData, N'pGFD4bb925DGvbd2439587y'))  
FROM [AdventureWorks2012].[ProtectedData04]   
WHERE Description   
    = N'data encrypted by certificate '' JanainaCert02''';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ENCRYPTBYCERT &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

