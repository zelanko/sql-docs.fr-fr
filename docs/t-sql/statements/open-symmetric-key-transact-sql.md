---
title: "OUVRIR la clé symétrique (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPEN SYMMETRIC KEY
- OPEN_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], opening
- OPEN SYMMETRIC KEY statement
ms.assetid: ff019a7c-c373-46c7-ac43-ffb7e2ee60b3
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd8302417e09eeef6e8052db6ced58c47cd25158
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="open-symmetric-key-transact-sql"></a>OPEN SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Déchiffre une clé symétrique et la met à disposition pour l'utiliser.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
OPEN SYMMETRIC KEY Key_name DECRYPTION BY <decryption_mechanism>  
  
<decryption_mechanism> ::=  
    CERTIFICATE certificate_name [ WITH PASSWORD = 'password' ]  
    |  
    ASYMMETRIC KEY asym_key_name [ WITH PASSWORD = 'password' ]  
    |  
    SYMMETRIC KEY decrypting_Key_name  
    |  
    PASSWORD = 'decryption_password'  
```  
  
## <a name="arguments"></a>Arguments  
 *Key_name*  
 Nom de la clé symétrique à ouvrir.  
  
 CERTIFICAT *nom_certificat*  
 Nom du certificat dont la clé privée sera utilisée pour déchiffrer la clé symétrique.  
  
 CLÉ asymétrique *asym_key_name*  
 Nom de la clé asymétrique dont la clé privée sera utilisée pour déchiffrer la clé symétrique.  
  
 AVEC le mot de passe ='*mot de passe*'  
 Mot de passe utilisé pour chiffrer la clé privée du certificat ou la clé asymétrique.  
  
 CLÉ symétrique *decrypting_key_name*  
 Nom de la clé symétrique qui sera utilisée pour déchiffrer la clé symétrique en cours d'ouverture.  
  
 Mot de passe ='*mot de passe*'  
 Mot de passe utilisé pour protéger la clé symétrique.  
  
## <a name="remarks"></a>Notes  
 Les clés symétriques ouvertes sont liées à la session et non au contexte de sécurité. Une clé ouverte est disponible tant qu'elle n'a pas été explicitement fermée ou que la session n'a pas été arrêtée. Si vous ouvrez une clé symétrique puis vous changez de contexte, la clé reste ouverte et disponible dans le contexte de substitution. Informations relatives aux clés symétriques ouvertes sont visibles dans le [sys.openkeys &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md) affichage catalogue.  
  
 Si la clé symétrique a été chiffrée avec une autre clé, celle-ci doit être ouverte d'abord.  
  
 Si la clé symétrique est déjà ouverte, la requête est un **NO_OP**.  
  
 Si le mot de passe, le certificat ou la clé fournie pour déchiffrer la clé symétrique est incorrecte, la requête échoue.  
  
 Les clés symétriques créées à partir d'un fournisseur de chiffrement ne peuvent pas être ouvertes. Les opérations de chiffrement et le déchiffrement à l’aide de ce type de clé symétrique réussissent sans le **ouvrir** instruction, car le fournisseur de chiffrement est ouverture et fermeture de la clé.  
  
## <a name="permissions"></a>Permissions  
 L'appelant doit disposer d'une autorisation sur la clé, et l'autorisation VIEW DEFINITION ne doit pas lui avoir été refusée sur la clé. D'autres conditions existent qui dépendent du mode de déchiffrement :  
  
-   DECRYPTION BY CERTIFICATE : autorisation CONTROL sur le certificat et connaissance du mot de passe qui chiffre la clé privée.  
  
-   DECRYPTION BY ASYMMETRIC KEY : autorisation CONTROL sur la clé asymétrique et connaissance du mot de passe qui chiffre la clé privée.  
  
-   DECRYPTION BY PASSWORD : connaissance de l'un des mots de passe utilisés pour chiffrer la clé symétrique.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-opening-a-symmetric-key-by-using-a-certificate"></a>A. Ouverture d'une clé symétrique à l'aide d'un certificat  
 L'exemple suivant ouvre la clé symétrique `SymKeyMarketing3` et la déchiffre à l'aide de la clé privée du certificat `MarketingCert9`.  
  
```  
USE AdventureWorks2012;  
OPEN SYMMETRIC KEY SymKeyMarketing3   
    DECRYPTION BY CERTIFICATE MarketingCert9;  
GO  
```  
  
### <a name="b-opening-a-symmetric-key-by-using-another-symmetric-key"></a>B. Ouverture d'une clé symétrique à l'aide d'une autre clé symétrique  
 L'exemple suivant ouvre la clé symétrique `MarketingKey11` et la déchiffre à l'aide de la clé symétrique `HarnpadoungsatayaSE3`.  
  
```  
USE AdventureWorks2012;  
-- First open the symmetric key that you want for decryption.  
OPEN SYMMETRIC KEY HarnpadoungsatayaSE3   
    DECRYPTION BY CERTIFICATE sariyaCert01;  
-- Use the key that is already open to decrypt MarketingKey11.  
OPEN SYMMETRIC KEY MarketingKey11   
    DECRYPTION BY SYMMETRIC KEY HarnpadoungsatayaSE3;  
GO   
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [CLOSE SYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/close-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Gestion de clés extensible &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  

