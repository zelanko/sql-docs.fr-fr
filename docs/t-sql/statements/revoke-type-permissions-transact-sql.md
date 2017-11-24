---
title: "RÉVOQUER des autorisations de Type (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- REVOKE statement, types
- permissions [SQL Server], types
- type permissions [SQL Server]
ms.assetid: 3969c7e9-ca10-4c67-971b-25d2dfccf650
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3de9121b53223ed03a2c3858fe7279cfb52af89
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="revoke-type-permissions-transact-sql"></a>REVOKE – révocation d'autorisations de type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Permet de révoquer des autorisations sur un type.  
  
  ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ]   
    ON TYPE :: [ schema_name ]. type_name   
    { FROM | TO } <database_principal> [ ,...n ]   
    [ CASCADE ]  
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
 Spécifie une autorisation qui peut être révoquée sur un type. Pour obtenir la liste des autorisations, consultez la section Notes plus loin dans cette rubrique.  
  
 SUR le TYPE **::** [ *nom_schéma* ] **.** *TYPE_NAME*  
 Spécifie le type sur lequel l'autorisation doit être révoquée. Le qualificateur d’étendue (**::**) est requis. Si *nom_schéma* n’est pas spécifié, le schéma par défaut est utilisé. Si *nom_schéma* est spécifié, le qualificateur d’étendue de schéma (**.**) est requis.  
  
 {À PARTIR DE | À} \<principal_base_de_données > Spécifie le principal à partir de laquelle l’autorisation est révoquée.  
  
 GRANT OPTION  
 Indique que le droit d'accorder l'autorisation spécifiée à d'autres principaux sera révoqué. L'autorisation elle-même ne sera pas révoquée.  
  
> [!IMPORTANT]  
>  Si le principal possède l'autorisation spécifiée sans l'option GRANT, l'autorisation elle-même sera révoquée.  
  
 CASCADE  
 Indique que l'autorisation en cours de révocation est également révoquée sur les principaux auxquels cette autorisation a été accordée ou révoquée par ce principal.  
  
> [!CAUTION]  
>  Une révocation en cascade d'une autorisation accordée avec l'option WITH GRANT OPTION entraîne la révocation des deux options GRANT et DENY de cette autorisation.  
  
 En tant que \<principal_base_de_données > Spécifie un principal à partir duquel le principal qui exécute cette requête dérive son droit de révoquer l’autorisation.  
  
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
  
 Les autorisations les plus spécifiques et limitées qu'il est possible de révoquer sur un type sont répertoriées dans le tableau ci-dessous, avec les autorisations plus générales qui les incluent de manière implicite.  
  
|Autorisation de type|Déduite d'une autorisation de type|Déduite d'une autorisation de schéma|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|Exécutez|CONTROL|Exécutez|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL sur le type. Si vous utilisez la clause AS, le principal spécifié doit être propriétaire du type.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple ci-dessous, l'autorisation `VIEW DEFINITION` sur le type défini par l'utilisateur `PhoneNumber` est révoquée pour l'utilisateur `KhalidR`. L'option `CASCADE` indique que l'autorisation `VIEW DEFINITION` sera également révoquée pour les principaux auxquels `KhalidR` a accordé cette autorisation. `PhoneNumber` se trouve dans le schéma `Telemarketing`.  
  
```  
REVOKE VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    FROM KhalidR CASCADE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Type d’octroi des autorisations &#40; Transact-SQL &#41;](../../t-sql/statements/grant-type-permissions-transact-sql.md)   
 [REFUSER des autorisations de Type &#40; Transact-SQL &#41;](../../t-sql/statements/deny-type-permissions-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Éléments sécurisables](../../relational-databases/security/securables.md)  
  
  

