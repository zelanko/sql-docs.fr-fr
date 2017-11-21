---
title: "Type d’octroi des autorisations (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], types
- granting permissions [SQL Server], types
- GRANT statement, types
- type permissions [SQL Server]
ms.assetid: 14bd2fb3-1446-49c0-be87-c6a670317ed0
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1e29ede5580418d1cbcb55d5a877196c3cabab92
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="grant-type-permissions-transact-sql"></a>GRANT – octroi d'autorisations de type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Permet d'accorder des autorisations sur un type.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GRANT permission  [ ,...n ] ON TYPE :: [ schema_name . ] type_name  
    TO <database_principal> [ ,...n ]  
    [ WITH GRANT OPTION ]  
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
 Spécifie une autorisation qui peut être accordée sur un type. Pour obtenir la liste des autorisations, consultez la section Notes plus loin dans cette rubrique.  
  
 SUR le TYPE **::** [ *nom_schéma***.** ] *type_name*  
 Spécifie le type sur lequel l'autorisation doit être accordée. Le qualificateur d’étendue (**::**) est requis. Si *nom_schéma* n’est pas spécifié, le schéma par défaut est utilisé. Si *nom_schéma* est spécifié, le qualificateur d’étendue de schéma (**.**) est requis.  
  
 POUR \<principal_base_de_données > Spécifie le principal auquel l’autorisation est accordée.  
  
 WITH GRANT OPTION  
 Indique que le principal a également la possibilité d'accorder l'autorisation spécifiée à d'autres principaux.  
  
 En tant que \<principal_base_de_données > Spécifie un principal à partir duquel le principal qui exécute cette requête dérive son droit d’accorder l’autorisation.  
  
 *Database_user*  
 Spécifie un utilisateur de base de données.  
  
 *Database_role*  
 Spécifie un rôle de base de données.  
  
 *Application_role*  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 Spécifie un rôle d'application.  
  
 *Database_user_mapped_to_Windows_User*  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Spécifie un utilisateur de base de données mappé sur un utilisateur Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Spécifie un utilisateur de base de données mappé à un groupe Windows.  
  
 *Database_user_mapped_to_certificate*  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Spécifie un utilisateur de base de données mappé sur un certificat.  
  
 *Database_user_mapped_to_asymmetric_key*  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Spécifie un utilisateur de base de données mappé à une clé asymétrique.  
  
 *Database_user_with_no_login*  
 Spécifie un utilisateur de base de données sans principal au niveau serveur correspondant.  
  
## <a name="remarks"></a>Notes  
 Un type est un élément sécurisable de niveau schéma inclus dans le schéma qui est son parent dans la hiérarchie des autorisations.  
  
> [!IMPORTANT]  
>  **GRANT**, **DENY,** et **RÉVOQUER** autorisations ne s’appliquent pas aux types système. Des autorisations peuvent être accordées aux types définis par l'utilisateur. Pour plus d’informations sur les types définis par l’utilisateur, consultez [utilisation des Types définis par l’utilisateur dans SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md).  
  
 Les autorisations les plus spécifiques et limitées qu'il est possible d'accorder sur un type sont répertoriées dans le tableau ci-dessous, avec les autorisations plus générales qui les incluent de manière implicite.  
  
|Autorisation de type|Déduite d'une autorisation de type|Déduite d'une autorisation de schéma|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|Exécutez|CONTROL|Exécutez|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Le fournisseur d'autorisations (ou le principal spécifié avec l'option AS) doit posséder l'autorisation elle-même avec l'option GRANT OPTION ou une autorisation plus élevée qui implique l'autorisation accordée.  
  
 Si vous utilisez l'option AS, les conditions supplémentaires ci-dessous s'appliquent.  
  
|AS|Autres autorisations nécessaires|  
|--------|------------------------------------|  
|Utilisateur de base de données|L’autorisation IMPERSONATE sur l’utilisateur, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à une connexion Windows|L’autorisation IMPERSONATE sur l’utilisateur, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à un groupe Windows|L’appartenance au groupe Windows, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à un certificat|L’appartenance au **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance à la **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à une clé asymétrique|L’appartenance au **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance à la **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données qui n'est mappé sur aucun principal d'un serveur|L’autorisation IMPERSONATE sur l’utilisateur, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Rôle de base de données|L’autorisation ALTER sur le rôle, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Rôle d'application|L’autorisation ALTER sur le rôle, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant accorde l'autorisation `VIEW DEFINITION` avec `GRANT OPTION` sur le type défini par l'utilisateur `PhoneNumber` à l'utilisateur `KhalidR`. `PhoneNumber`se trouve dans le schéma `Telemarketing`.  
  
```  
GRANT VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    TO KhalidR WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [REFUSER des autorisations de Type &#40; Transact-SQL &#41;](../../t-sql/statements/deny-type-permissions-transact-sql.md)   
 [RÉVOQUER les autorisations de Type &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-type-permissions-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


