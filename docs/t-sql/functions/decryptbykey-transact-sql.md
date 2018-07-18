---
title: DECRYPTBYKEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DecryptByKey_TSQL
- DECRYPTBYKEY
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], DecryptByKey function
- decryption [SQL Server], keys
- decryption [SQL Server], symmetric keys
- DECRYPTBYKEY function
ms.assetid: 6edf121f-ac62-4dae-90e6-6938f32603c9
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 61e984a45f2f5a7b2d675ec574fda255c4747642
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37783060"
---
# <a name="decryptbykey-transact-sql"></a>DECRYPTBYKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Cette fonction utilise une clé symétrique pour déchiffrer les données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DecryptByKey ( { 'ciphertext' | @ciphertext }   
    [ , add_authenticator, { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Arguments  
*ciphertext*  
Variable de type **varbinary** contenant des données chiffrées avec la clé.  
  
**@ciphertext**  
Variable de type **varbinary** contenant des données chiffrées avec la clé.  
  
 *add_authenticator*  
Indique si le processus de chiffrement d’origine comprend et chiffre un authentificateur avec le texte en clair. Doit correspondre à la valeur passée à [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) durant le processus de chiffrement des données. *add_authenticator* a le type de données **int**.  
  
 *authenticator*  
Données utilisées comme base pour la génération de l’authentificateur. Doit correspondre à la valeur fournie à [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *authenticator* a le type de données **sysname**.  

**@authenticator**  
Variable contenant des données à partir desquelles un authentificateur est généré. Doit correspondre à la valeur fournie à [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *@authenticator* a le type de données **sysname**.  

## <a name="return-types"></a>Types de retour  
**varbinary** d’une taille maximale de 8 000 octets. `DECRYPTBYKEY` retourne NULL si la clé symétrique utilisée pour chiffrer les données n’est pas ouverte ou si *ciphertext* est NULL.  
  
## <a name="remarks"></a>Notes   
`DECRYPTBYKEY` utilise une clé symétrique. Cette clé symétrique doit déjà être ouverte dans la base de données. `DECRYPTBYKEY` autorise l’ouverture de plusieurs clés en même temps. Vous n’avez pas besoin d’ouvrir la clé tout de suite avant de déchiffrer le texte chiffré.  
  
Le chiffrement et le déchiffrement symétriques fonctionnent assez rapidement, et donnent de bons résultats pour les opérations impliquant de gros volumes de données.  
  
## <a name="permissions"></a>Autorisations  
La clé symétrique doit déjà être ouverte dans la session active. Pour plus d’informations, consultez [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-decrypting-by-using-a-symmetric-key"></a>A. Déchiffrement à l'aide d'une clé symétrique  
Cet exemple déchiffre le texte chiffré avec une clé symétrique.  
  
```  
-- First, open the symmetric key with which to decrypt the data.  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
GO  
  
-- Now list the original ID, the encrypted ID, and the   
-- decrypted ciphertext. If the decryption worked, the original  
-- and the decrypted ID will match.  
SELECT NationalIDNumber, EncryptedNationalID   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalID))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-decrypting-by-using-a-symmetric-key-and-an-authenticating-hash"></a>B. Déchiffrement à l'aide d'une clé symétrique et d'un hachage d'authentification  
Cet exemple déchiffre les données chiffrées à l’origine avec un authentificateur.  
  
```  
-- First, open the symmetric key with which to decrypt the data  
OPEN SYMMETRIC KEY CreditCards_Key11  
   DECRYPTION BY CERTIFICATE Sales09;  
GO  
  
-- Now list the original card number, the encrypted card number,  
-- and the decrypted ciphertext. If the decryption worked,   
-- the original number will match the decrypted number.  
SELECT CardNumber, CardNumber_Encrypted   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByKey(CardNumber_Encrypted, 1 ,   
    HashBytes('SHA1', CONVERT(varbinary, CreditCardID))))   
    AS 'Decrypted card number' FROM Sales.CreditCard;  
GO  
  
```  
  
## <a name="see-also"></a> Voir aussi  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Choisir un algorithme de chiffrement](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
  
