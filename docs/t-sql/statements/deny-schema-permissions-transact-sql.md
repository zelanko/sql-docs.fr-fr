---
title: DENY - Refuser des autorisations sur un schéma (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], schemas
- schemas [SQL Server], permissions
- permissions [SQL Server], schemas
- DENY statement, schemas
ms.assetid: 300a67c4-d226-4653-9e9f-7ae4d53fcf33
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5f5a86fc5eccf214828e969865cdedbc4379dc9c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85766663"
---
# <a name="deny-schema-permissions-transact-sql"></a>DENY (Autorisations de schéma) (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Refuse l'octroi d'autorisations sur un schéma.  
  

![Icône Lien d’article](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien d’article") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
DENY permission  [ ,...n ] } ON SCHEMA :: schema_name  
    TO database_principal [ ,...n ]   
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Arguments  
*permission*  
Spécifie une autorisation qui peut être refusée sur un schéma. Pour obtenir la liste de ces autorisations, consultez la section Remarques, plus loin dans cet article.  
  
ON SCHEMA **::** schema *_name*  
Spécifie le schéma sur lequel l’autorisation est refusée. Le qualificateur d’étendue **::** est obligatoire.  
  
*database_principal*  
Spécifie le principal pour lequel l'autorisation doit être refusée. *database_principal* peut être l’un des principaux suivants :  
  
-   Utilisateur de base de données  
-   Rôle de base de données  
-   Rôle d'application  
-   Utilisateur de base de données mappé à une connexion Windows  
-   Utilisateur de base de données mappé à un groupe Windows  
-   Utilisateur de base de données mappé à un certificat  
-   Utilisateur de base de données mappé à une clé asymétrique  
-   Utilisateur de base de données mappé à un principal de serveur  
  
CASCADE  
Refuse l’autorisation à tout autre principal auquel le *database_principal* a octroyé l’autorisation.
  
*denying_principal*  
Spécifie un principal dont le principal qui exécute cette requête dérive son droit de refuser l'autorisation. *denying_principal* peut être l’un des principaux suivants :  
  
-   Utilisateur de base de données  
-   Rôle de base de données  
-   Rôle d'application  
-   Utilisateur de base de données mappé à une connexion Windows  
-   Utilisateur de base de données mappé à un groupe Windows  
-   Utilisateur de base de données mappé à un certificat  
-   Utilisateur de base de données mappé à une clé asymétrique  
-   Utilisateur de base de données mappé à un principal de serveur  
  
## <a name="remarks"></a>Notes  
Un schéma est un sécurisable au niveau de la base de données. Il est contenu par la base de données qui est son parent dans la hiérarchie des autorisations. Les autorisations les plus spécifiques et limitées qu’il est possible de refuser sur un schéma sont listées dans le tableau suivant. Le tableau présente les autorisations plus générales qui les englobent de manière implicite.  
  
|Autorisation de schéma|Déduite d'une autorisation de schéma|Impliquée par une autorisation de base de données|  
|-----------------------|----------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SCHEMA|  
|CONTROL|CONTROL|CONTROL|  
|CREATE SEQUENCE|ALTER|ALTER ANY SCHEMA|  
|Suppression|CONTROL|Suppression|  
|Exécutez|CONTROL|Exécutez|  
|INSERT|CONTROL|INSERT|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|CONTROL|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Autorisations  
Requiert l'autorisation CONTROL pour le schéma. Si vous utilisez l’option AS, le principal spécifié doit être propriétaire du schéma.  
  
## <a name="see-also"></a>Voir aussi  
[CREATE SCHEMA &#40;Transact-SQL&#41;](../../t-sql/statements/create-schema-transact-sql.md)   
[DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
[Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
[Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
[sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
[sys.fn_my_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
[HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  
