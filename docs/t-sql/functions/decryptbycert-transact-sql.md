---
title: DECRYPTBYCERT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ff7cd9e82f2e70e39b02f10726acbae657ad670c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741197"
---
# <a name="decryptbycert-transact-sql"></a>DECRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Cette fonction utilise la clé privée d’un certificat pour déchiffrer les données chiffrées.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DecryptByCert ( certificate_ID , { 'ciphertext' | @ciphertext }   
    [ , { 'cert_password' | @cert_password } ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *certificate_ID*  
ID d'un certificat de la base de données. *certificate_ID* a le type de données **int**.  
  
 *ciphertext*  
Chaîne de données chiffrée avec la clé publique du certificat.  
  
 @ciphertext  
Variable de type **varbinary** contenant des données chiffrées avec le certificat.  
  
 *cert_password*  
Mot de passe utilisé pour chiffrer la clé privée du certificat. *cert_password* doit avoir un format de données Unicode.  
  
 @cert_password  
Variable de type **nchar** ou **nvarchar** contenant le mot de passe utilisé pour chiffrer la clé privée du certificat. *@cert_password* doit avoir un format de données Unicode.  

## <a name="return-types"></a>Types de retour  
**varbinary** d’une taille maximale de 8 000 octets.  
  
## <a name="remarks"></a>Notes   
Cette fonction déchiffre les données à l'aide de la clé privée d'un certificat. Les opérations de chiffrement/déchiffrement qui utilisent des clés asymétriques consomment une grande quantité de ressources. Nous recommandons donc aux développeurs d’éviter d’utiliser [ENCRYPTBYCERT](./encryptbycert-transact-sql.md) et DECRYPTBYCERT pour les opérations de chiffrement/déchiffrement de routine des données utilisateur.  

## <a name="permissions"></a>Permissions  
`DECRYPTBYCERT` nécessite l’autorisation CONTROL sur le certificat.  
  
## <a name="examples"></a>Exemples  
Cet exemple sélectionne des lignes de `[AdventureWorks2012].[ProtectedData04]` marquées comme données chiffrées à l’origine par le certificat `JanainaCert02`. L’exemple déchiffre tout d’abord la clé privée du certificat `JanainaCert02` avec le mot de passe du certificat `pGFD4bb925DGvbd2439587y`. L’exemple déchiffre ensuite le texte chiffré avec cette clé privée. L’exemple convertit les données déchiffrées du type **varbinary** en type **nvarchar**.  

```  
SELECT convert(nvarchar(max), DecryptByCert(Cert_Id('JanainaCert02'),  
    ProtectedData, N'pGFD4bb925DGvbd2439587y'))  
FROM [AdventureWorks2012].[ProtectedData04]   
WHERE Description   
    = N'data encrypted by certificate '' JanainaCert02''';  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [ENCRYPTBYCERT &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
