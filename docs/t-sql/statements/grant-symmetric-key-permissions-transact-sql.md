---
title: "ACCORDER des autorisations Clées symétriques (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
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
- symmetric keys [SQL Server], permissions
- permissions [SQL Server], symmetric keys
- encryption [SQL Server], symmetric keys
- GRANT statement, symmetric keys
- cryptography [SQL Server], symmetric keys
- granting permissions [SQL Server], symmetric keys
ms.assetid: 5c61557f-67ae-4e55-b86d-713575b27cea
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ecf72664248aa1d153fa14b632729190dc7dd660
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="grant-symmetric-key-permissions-transact-sql"></a>GRANT – octroi d'autorisations de clé symétrique (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Permet d'accorder des autorisations sur une clé symétrique. 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GRANT permission [ ,...n ]    
    ON SYMMETRIC KEY :: symmetric_key_name   
    TO <database_principal> [ ,...n ] [ WITH GRANT OPTION ]  
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
 Spécifie une autorisation qui peut être accordée sur une clé symétrique. Pour obtenir la liste des autorisations, consultez la section Notes plus loin dans cette rubrique.  
  
 CLÉ symétrique de ON ::*asymmetric_key_name*  
 Spécifie la clé symétrique sur laquelle l'autorisation doit être accordée. L'identificateur d'étendue (::) est requis.  
  
 POUR \< *principal_base_de_données*>  
 Spécifie le principal auquel l'autorisation est accordée.  
  
 WITH GRANT OPTION  
 Indique que le principal a également la possibilité d'accorder l'autorisation spécifiée à d'autres principaux.  
  
 En tant que \<principal_base_de_données > Spécifie un principal à partir duquel le principal qui exécute cette requête dérive son droit d’accorder l’autorisation.  
  
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
  
 Une clé symétrique est un élément sécurisable au niveau base de données inclus dans la base de données qui est son parent dans la hiérarchie des autorisations. Les autorisations les plus spécifiques et limitées qu'il est possible d'accorder sur une clé symétrique sont répertoriées dans le tableau ci-dessous, avec les autorisations plus générales qui les incluent de manière implicite.  
  
|Autorisation de clé symétrique|Déduite d'une autorisation de clé symétrique|Impliquée par une autorisation de base de données|  
|------------------------------|-----------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SYMMETRIC KEY|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Le fournisseur d'autorisations (ou le principal spécifié avec l'option AS) doit posséder l'autorisation elle-même avec l'option GRANT OPTION ou une autorisation plus élevée qui implique l'autorisation accordée.  
  
 Si vous utilisez l'option AS, les conditions supplémentaires ci-dessous s'appliquent.  
  
|En tant que *granting_principal*|Autres autorisations nécessaires|  
|------------------------------|------------------------------------|  
|Utilisateur de base de données|Autorisation IMPERSONATE sur l'utilisateur, appartenance au rôle de base de données fixe db_securityadmin, appartenance au rôle de base de données fixe db_owner ou appartenance au rôle serveur fixe sysadmin.|  
|Utilisateur de base de données mappé à une connexion Windows|Autorisation IMPERSONATE sur l'utilisateur, appartenance au rôle de base de données fixe db_securityadmin, appartenance au rôle de base de données fixe db_owner ou appartenance au rôle serveur fixe sysadmin.|  
|Utilisateur de base de données mappé à un groupe Windows|Appartenance au groupe Windows, appartenance aux rôles de base de données fixe db_securityadmin ou db_owner ou appartenance au rôle serveur fixe sysadmin.|  
|Utilisateur de base de données mappé à un certificat|Appartenance aux rôles de base de données fixe db_securityadmin ou db_owner ou appartenance au rôle serveur fixe sysadmin.|  
|Utilisateur de base de données mappé à une clé asymétrique|Appartenance aux rôles de base de données fixe db_securityadmin ou db_owner ou appartenance au rôle serveur fixe sysadmin.|  
|Utilisateur de base de données qui n'est mappé sur aucun principal d'un serveur|Autorisation IMPERSONATE sur l'utilisateur, appartenance au rôle de base de données fixe db_securityadmin, appartenance au rôle de base de données fixe db_owner ou appartenance au rôle serveur fixe sysadmin.|  
|Rôle de base de données|Autorisation ALTER sur le rôle, appartenance au rôle de base de données fixe db_securityadmin, appartenance au rôle de base de données fixe db_owner ou appartenance au rôle serveur fixe sysadmin.|  
|Rôle d'application|Autorisation ALTER sur le rôle, appartenance au rôle de base de données fixe db_securityadmin, appartenance au rôle de base de données fixe db_owner ou appartenance au rôle serveur fixe sysadmin.|  
  
 Les principaux ayant l'autorisation CONTROL sur un élément sécurisable peuvent accorder une autorisation sur cet élément.  
  
 Les détenteurs de l'autorisation CONTROL SERVER, tels que les membres du rôle serveur fixe sysadmin, peuvent accorder une autorisation sur n'importe quel élément sécurisable du serveur. Les bénéficiaires de l'autorisation CONTROL sur une base de données, tels que les membres du rôle de base de données fixe db_owner, peuvent accorder une autorisation quelconque sur tout élément sécurisable inclus dans la base de données.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple ci-dessous, l'autorisation `ALTER` sur la clé symétrique `SamInventory42` est accordée à l'utilisateur de base de données `HamidS`.  
  
```  
USE AdventureWorks2012;  
GRANT ALTER ON SYMMETRIC KEY::SamInventory42 TO HamidS;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.symmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [REFUSER des autorisations de clé symétrique &#40; Transact-SQL &#41;](../../t-sql/statements/deny-symmetric-key-permissions-transact-sql.md)   
 [RÉVOQUER les autorisations de clé symétrique &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-symmetric-key-permissions-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  


