---
title: DECRYPTBYASYMKEY (Transact-SQL) | Documents Microsoft
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
- DECRYPTBYASYMKEY
- DECRYPTBYASYMKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], DECRYPTBYASYMKEY function
- DECRYPTBYASYMKEY function
- decryption [SQL Server], asymmetric keys
ms.assetid: d9ebcd30-f01c-4cfe-b95e-ffe6ea13788b
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7196e7eedf5d1a808853df55259fcee1891c345
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="decryptbyasymkey-transact-sql"></a>DECRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Déchiffre les données à l'aide d'une clé asymétrique.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DecryptByAsymKey (Asym_Key_ID , { 'ciphertext' | @ciphertext }   
    [ , 'Asym_Key_Password' ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Asym_Key_ID*  
 ID d'une clé asymétrique dans la base de données. *Asym_Key_ID* est **int**.  
  
 *texte chiffré*  
 Chaîne de données chiffrée avec la clé asymétrique.  
  
 @ciphertext  
 Est une variable de type **varbinary** qui contient les données qui ont été chiffrées avec la clé asymétrique.  
  
 *Asym_Key_Password*  
 Mot de passe utilisé pour chiffrer la clé asymétrique dans la base de données.  
  
## <a name="return-types"></a>Types de retour  
 **varbinary** avec une taille maximale de 8 000 octets.  
  
## <a name="remarks"></a>Notes  
 Le chiffrement et le déchiffrement avec une clé asymétrique sont coûteux par rapport au chiffrement et au déchiffrement avec une clé symétrique. Il n'est pas recommandé d'utiliser une clé asymétrique avec des ensembles de données volumineux par exemple, avec des données utilisateur issues de tables.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation CONTROL sur la clé asymétrique.  
  
## <a name="examples"></a>Exemples  
 Le code exemple suivant déchiffre le texte chiffré avec la clé asymétrique `JanainaAsymKey02`, stockée dans `AdventureWorks2012.ProtectedData04`. Les données renvoyées sont déchiffrées à l'aide de la clé asymétrique `JanainaAsymKey02`, qui a été déchiffrée avec le mot de passe `pGFD4bb925DGvbd2439587y`. Le texte en clair est converti en type **nvarchar**.  
  
```  
SELECT CONVERT(nvarchar(max),  
    DecryptByAsymKey( AsymKey_Id('JanainaAsymKey02'),   
    ProtectedData, N'pGFD4bb925DGvbd2439587y' ))   
AS DecryptedData   
FROM [AdventureWorks2012].[Sales].[ProtectedData04]   
WHERE Description = N'encrypted by asym key''JanainaAsymKey02''';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ENCRYPTBYASYMKEY &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [Choisir un algorithme de chiffrement](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

