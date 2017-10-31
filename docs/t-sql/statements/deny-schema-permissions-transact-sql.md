---
title: "REFUSER des autorisations de schéma (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- denying permissions [SQL Server], schemas
- schemas [SQL Server], permissions
- permissions [SQL Server], schemas
- DENY statement, schemas
ms.assetid: 300a67c4-d226-4653-9e9f-7ae4d53fcf33
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7d4d3e3709ff4ad38d8b033afe1569d9c234bfa2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="deny-schema-permissions-transact-sql"></a>DENY (Autorisations de schéma) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Refuse l'octroi d'autorisations sur un schéma.  
  

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DENY permission  [ ,...n ] } ON SCHEMA :: schema_name  
    TO database_principal [ ,...n ]   
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Arguments  
 *autorisation*  
 Spécifie une autorisation qui peut être refusée sur un schéma. Pour obtenir la liste de ces autorisations, consultez la section Remarques plus loin dans cette rubrique.  
  
 ON SCHEMA **::** schéma*_ordinateur*  
 Spécifie le schéma sur lequel l'autorisation est refusée. Le qualificateur d’étendue **::** est requis.  
  
 *principal_base_de_données*  
 Spécifie le principal auquel l'autorisation est refusée. *principal_base_de_données* peut prendre l’une des opérations suivantes :  
  
-   Utilisateur de base de données  
-   Rôle de base de données  
-   Rôle d'application  
-   Utilisateur de base de données mappé à une connexion Windows  
-   Utilisateur de base de données mappé à un groupe Windows  
-   Utilisateur de base de données mappé à un certificat  
-   Utilisateur de base de données mappé à une clé asymétrique  
-   Utilisateur de base de données mappé à un principal de serveur  
  
CASCADE  
 Indique que l'autorisation à refuser est également refusée pour les autres principaux auxquels elle a été accordée par ce principal.  
  
*denying_principal*  
 Spécifie un principal dont le principal qui exécute cette requête dérive son droit de refuser l'autorisation. *denying_principal* peut prendre l’une des opérations suivantes :  
  
-   Utilisateur de base de données  
-   Rôle de base de données  
-   Rôle d'application  
-   Utilisateur de base de données mappé à une connexion Windows  
-   Utilisateur de base de données mappé à un groupe Windows  
-   Utilisateur de base de données mappé à un certificat  
-   Utilisateur de base de données mappé à une clé asymétrique  
-   Utilisateur de base de données mappé à un principal de serveur  
  
## <a name="remarks"></a>Notes  
 Un schéma est un élément sécurisable du niveau base de données, contenu par la base de données qui est son parent dans la hiérarchie des autorisations. Les autorisations les plus spécifiques et limitées qu'il est possible de refuser sur un schéma sont répertoriées dans le tableau ci-dessous, accompagnées des autorisations plus générales qui les incluent de manière implicite.  
  
|Autorisation de schéma|Déduite d'une autorisation de schéma|Impliquée par une autorisation de base de données|  
|-----------------------|----------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SCHEMA|  
|CONTROL|CONTROL|CONTROL|  
|CREATE SEQUENCE|ALTER|ALTER ANY SCHEMA|  
|DELETE|CONTROL|DELETE|  
|Exécutez|CONTROL|Exécutez|  
|INSERT|CONTROL|INSERT|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|CONTROL|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL pour le schéma. Si vous utilisez l'option AS, le principal spécifié doit être propriétaire du schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER des schémas &#40; Transact-SQL &#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [Sys.fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  

