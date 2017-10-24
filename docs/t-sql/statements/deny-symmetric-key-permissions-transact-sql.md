---
title: "REFUSER des autorisations de clé symétrique (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], symmetric keys
- symmetric keys [SQL Server], permissions
- permissions [SQL Server], symmetric keys
- DENY statement, symmetric keys
- encryption [SQL Server], symmetric keys
- cryptography [SQL Server], symmetric keys
ms.assetid: 52d4b12d-17be-4cbd-aa78-65332a4883b0
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d6497a6bcf298736b3ad6c497ea26088e9fdf0a1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="deny-symmetric-key-permissions-transact-sql"></a>DENY – refus d'autorisations de clé symétrique (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Permet de refuser des autorisations sur une clé symétrique.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DENY permission [ ,...n ]    
    ON SYMMETRIC KEY :: symmetric_key_name   
        TO <database_principal> [ ,...n ] [ CASCADE ]  
    [ AS <database_principal> ]   
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login   
```  
  
## <a name="arguments"></a>Arguments  
 *autorisation*  
 Spécifie une autorisation qui peut être refusée sur une clé symétrique. Pour obtenir la liste des autorisations, consultez la section Notes plus loin dans cette rubrique.  
  
 CLÉ symétrique de ON ::*asymmetric_key_name*  
 Spécifie la clé symétrique sur laquelle l'autorisation doit être refusée. L'identificateur d'étendue (::) est requis.  
  
 POUR \< *principal_base_de_données*>  
 Spécifie le principal pour lequel l'autorisation est révoquée.  
  
 CASCADE  
 Indique que l'autorisation à refuser est également refusée pour les autres principaux auxquels elle a été accordée par ce principal.  
  
 En tant que \<principal_base_de_données >  
 Spécifie un principal dont le principal qui exécute cette requête dérive son droit de refuser l'autorisation.  
  
 *Database_user*  
 Spécifie un utilisateur de base de données.  
  
 *Database_role*  
 Spécifie un rôle de base de données.  
  
 *Application_role*  
 Spécifie un rôle d'application.  
  
 *Database_user_mapped_to_Windows_User*  
 Spécifie un utilisateur de base de données mappé sur un utilisateur Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
 Spécifie un utilisateur de base de données mappé à un groupe Windows.  
  
 *Database_user_mapped_to_certificate*  
 Spécifie un utilisateur de base de données mappé sur un certificat.  
  
 *Database_user_mapped_to_asymmetric_key*  
 Spécifie un utilisateur de base de données mappé à une clé asymétrique.  
  
 *Database_user_with_no_login*  
 Spécifie un utilisateur de base de données sans principal au niveau serveur correspondant.  
  
## <a name="remarks"></a>Notes  
 Informations sur les clés symétriques sont consultables dans le [sys.symmetric_keys](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md) affichage catalogue.  
  
 Une clé symétrique est un élément sécurisable au niveau base de données inclus dans la base de données qui est son parent dans la hiérarchie des autorisations. Les autorisations les plus spécifiques et limitées qu'il est possible de refuser sur une clé symétrique sont répertoriées dans le tableau ci-dessous, avec les autorisations plus générales qui les incluent de manière implicite.  
  
|Autorisation de clé symétrique|Déduite d'une autorisation de clé symétrique|Impliquée par une autorisation de base de données|  
|------------------------------|-----------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SYMMETRIC KEY|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL sur la clé symétrique ou l'autorisation ALTER ANY SYMMETRIC KEY sur la base de données. Si vous utilisez l'option AS, le principal spécifié doit posséder la clé symétrique.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple ci-dessous, l'autorisation `ALTER` sur la clé symétrique `SamInventory42` est refusée à l'utilisateur de base de données `HamidS`.  
  
```  
USE AdventureWorks2012;  
DENY ALTER ON SYMMETRIC KEY::SamInventory42 TO HamidS;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.symmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [ACCORDER des autorisations de clé symétrique &#40; Transact-SQL &#41;](../../t-sql/statements/grant-symmetric-key-permissions-transact-sql.md)   
 [RÉVOQUER les autorisations de clé symétrique &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-symmetric-key-permissions-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

