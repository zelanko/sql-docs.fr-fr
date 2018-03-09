---
title: "RÉVOQUER des autorisations de schéma (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 06/10/2016
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
- REVOKE statement, schema
- schemas [SQL Server], permissions
- permissions [SQL Server], schemas
ms.assetid: a1fabf35-1f42-48db-b0b8-7181f413ba3a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 09bf03fc40529e2975727ae1e7068a18c35b6002
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="revoke-schema-permissions-transact-sql"></a>REVOKE - Révoquer les autorisations sur un schéma (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Révoque les autorisations sur un schéma.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission  [ ,...n ]   
    ON SCHEMA :: schema_name   
    { TO | FROM } database_principal [ ,...n ]  
    [ CASCADE ]  
    [ AS revoking_principal ]  
```  
  
## <a name="arguments"></a>Arguments  
 *autorisation*  
 Spécifie une autorisation qu'il est possible de révoquer sur un schéma. Les autorisations qui peuvent être révoquées sur un schéma sont listées dans la section Remarques, plus loin dans cette rubrique.  
  
 GRANT OPTION FOR  
 Indique que le droit d'accorder le droit spécifié à d'autres principaux sera révoqué. L'autorisation elle-même ne sera pas révoquée.  
  
> [!IMPORTANT]  
>  Si le principal possède l'autorisation spécifiée sans l'option GRANT, l'autorisation elle-même sera révoquée.  
  
 ON SCHEMA **::** schéma*_ordinateur*  
 Indique le schéma sur lequel l'autorisation est révoquée. Le qualificateur d’étendue **::** est requis.  
  
 *principal_base_de_données*  
 Spécifie le principal pour lequel l'autorisation est révoquée. Il peut s'agir :  
  
-   d'un utilisateur de base de données ;  
  
-   d'un rôle de base de données ;  
  
-   d'un rôle d'application ;  
  
-   d'un utilisateur de base de données mappé sur une connexion Windows ;  
  
-   d'un utilisateur de base de données mappé sur un groupe Windows ;  
  
-   d'un utilisateur de base de données mappé sur un certificat ;  
  
-   d'un utilisateur de base de données mappé à une clé asymétrique ;  
  
-   d'un utilisateur de base de données qui n'est pas mappé sur le principal d'un serveur.  
  
 CASCADE  
 Indique que l'autorisation en cours de révocation est également révoquée sur les principaux auxquels elle a été accordée par ce principal.  
  
> [!CAUTION]  
>  Indique que l'autorisation en cours de révocation est également révoquée sur les principaux auxquels cette autorisation a été accordée ou révoquée par ce principal.  
  
 En tant que *revoking_principal*  
 Spécifie un principal dont le principal qui exécute cette requête dérive son droit de révoquer l'autorisation. Il peut s'agir :  
  
-   d'un utilisateur de base de données ;  
  
-   d'un rôle de base de données ;  
  
-   d'un rôle d'application ;  
  
-   d'un utilisateur de base de données mappé sur une connexion Windows ;  
  
-   d'un utilisateur de base de données mappé sur un groupe Windows ;  
  
-   d'un utilisateur de base de données mappé sur un certificat ;  
  
-   d'un utilisateur de base de données mappé à une clé asymétrique ;  
  
-   d'un utilisateur de base de données qui n'est pas mappé sur le principal d'un serveur.  
  
## <a name="remarks"></a>Notes  
 Un schéma est un élément sécurisable au niveau base de données contenu dans la base de données parente dans la hiérarchie des autorisations. Les autorisations les plus spécifiques et limitées qu'il est possible de révoquer pour un schéma sont répertoriées dans le tableau ci-dessous, accompagnées des autorisations plus générales qui les incluent de manière implicite.  
  
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
 Requiert l'autorisation CONTROL pour le schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER des schémas &#40; Transact-SQL &#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [Sys.fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  
