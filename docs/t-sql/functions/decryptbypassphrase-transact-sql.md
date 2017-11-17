---
title: DECRYPTBYPASSPHRASE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- DECRYPTBYPASSPHRASE
- DECRYPTBYPASSPHRASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- decryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], DECRYPTBYPASSPHRASE function
- DECRYPTBYPASSPHRASE function
ms.assetid: ca34b5cd-07b3-4dca-b66a-ed8c6a826c95
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0af2f19acced57d722427c8f341db62dbdb34198
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="decryptbypassphrase-transact-sql"></a>DECRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Déchiffre des données chiffrées par une expression relative au mot de passe.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DecryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *phrase secrète*  
 Expression relative au mot de passe utilisée pour générer la clé de déchiffrement.  
  
 @passphrase  
 Est une variable de type **nvarchar**, **char**, **varchar**, ou **nchar** qui contient la phrase secrète qui permet de générer la clé de déchiffrement.  
  
 '*texte chiffré*'  
 Texte à déchiffrer.  
  
 @ciphertext  
 Est une variable de type **varbinary** qui contient le texte chiffré. La taille maximale est de 8 000 octets.  
  
 *add_authenticator*  
 Indique si un authentificateur a été chiffré en même temps que le texte en clair. La valeur est 1 si un authentificateur a été utilisé. **int**.  
  
 @add_authenticator  
 Indique si un authentificateur a été chiffré en même temps que le texte en clair. La valeur est 1 si un authentificateur a été utilisé. **int**.  
  
 *authentificateur*  
 Données de l'authentificateur. **sysname**.  
  
 @authenticator  
 Variable contenant les données à partir desquelles l'authentificateur sera dérivé.  
  
## <a name="return-types"></a>Types de retour  
 **varbinary** avec une taille maximale de 8 000 octets.  
  
## <a name="remarks"></a>Notes  
 Aucune autorisation n'est requise pour cette fonction.  
  
 Renvoie NULL si les informations de l'authentificateur ou de l'expression relative au mot de passe sont incorrectes.  
  
 L'expression relative au mot de passe est utilisée pour générer une clé de déchiffrement qui n'est pas persistante.  
  
 Si un authentificateur est inclus lorsque le texte est chiffré, il doit être fourni au moment du déchiffrement. Si la valeur de l'authentificateur fournie au moment du déchiffrement ne correspond pas à la valeur de l'authentificateur chiffrée avec les données, le déchiffrement échoue.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant déchiffre l’enregistrement mis à jour dans [EncryptByPassPhrase](../../t-sql/functions/encryptbypassphrase-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
-- Get the pass phrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
= 'A little learning is a dangerous thing!';  
  
-- Decrypt the encrypted record.  
SELECT CardNumber, CardNumber_EncryptedbyPassphrase   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByPassphrase(@PassphraseEnteredByUser, CardNumber_EncryptedbyPassphrase, 1   
    , CONVERT(varbinary, CreditCardID)))  
    AS 'Decrypted card number' FROM Sales.CreditCard   
    WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Choisir un algorithme de chiffrement](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
  
  

