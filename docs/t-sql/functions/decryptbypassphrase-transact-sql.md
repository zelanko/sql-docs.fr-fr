---
title: DECRYPTBYPASSPHRASE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
manager: craigg
ms.openlocfilehash: b9aecb41372915f28eaf0e3b41a0fa405faccfc0
ms.sourcegitcommit: 6e55a0a7b7eb6d455006916bc63f93ed2218eae1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239059"
---
# <a name="decryptbypassphrase-transact-sql"></a>DECRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Cette fonction déchiffre les données chiffrées à l’origine avec une phrase secrète.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DecryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *passphrase*  
Phrase secrète utilisée pour générer la clé de déchiffrement.  
  
 @passphrase  
Variable de type

+ **char**
+ **nchar**
+ **nvarchar**

ou

+ **varchar**

contenant la phrase secrète utilisée pour générer la clé de déchiffrement.  
  
'*ciphertext*'  
Chaîne de données chiffrées avec la clé. *ciphertext* a le type de données **varbinary**.  
 
@ciphertext  
Variable de type **varbinary** contenant des données chiffrées avec la clé. La variable*@ciphertext* a une taille maximale de 8 000 octets.  
  
*add_authenticator*  
Indique si le processus de chiffrement d’origine comprend et chiffre un authentificateur avec le texte en clair. *add_authenticator* a la valeur 1 si le processus de chiffrement utilise un authentificateur. *add_authenticator* a le type de données **int**.  
  
@add_authenticator  
Variable indiquant si le processus de chiffrement d’origine comprend et chiffre un authentificateur avec le texte en clair. *@add_authenticator* a la valeur 1 si le processus de chiffrement utilise un authentificateur. *@add_authenticator* a le type de données **int**.  

*authenticator*  
Données utilisées comme base pour la génération de l’authentificateur. *authenticator* a le type de données **sysname**.  
  
@authenticator  
Variable contenant les données utilisées comme base pour la génération des authentificateurs. *@authenticator* a le type de données **sysname**.  
  
## <a name="return-types"></a>Types de retour  
**varbinary** d’une taille maximale de 8 000 octets.  
  
## <a name="remarks"></a>Notes   
`DECRYPTBYPASSPHRASE` ne nécessite pas d’autorisations pour son exécution. `DECRYPTBYPASSPHRASE` retourne NULL si elle reçoit la phrase secrète ou les informations de l’authentificateur incorrectes.  
  
`DECRYPTBYPASSPHRASE` utilise la phrase secrète pour générer une clé de déchiffrement. Cette clé de déchiffrement n’est pas conservée.  
  
Si un authentificateur a été inclus au moment du chiffrement du texte chiffré, `DECRYPTBYPASSPHRASE` doit recevoir ce même authentificateur pour le processus de déchiffrement. Si la valeur de l’authentificateur fournie pour le processus de déchiffrement ne correspond pas à celle initialement utilisée pour chiffrer les données, l’opération `DECRYPTBYPASSPHRASE` échoue.  
  
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
  
## <a name="see-also"></a> Voir aussi  
 [Choisir un algorithme de chiffrement](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
  
  
