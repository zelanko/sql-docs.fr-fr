---
title: "RÉVOQUER les autorisations de clé asymétrique (Transact-SQL) | Documents Microsoft"
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
- permissions [SQL Server], asymmetric keys
- asymmetric keys [SQL Server], permissions
- REVOKE statement, asymmetric keys
ms.assetid: 1a1063e8-ffc7-4775-a40d-e155740ad7b2
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d4f9f08fda905261e188bb90f8d85fd0a48b2f2c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-asymmetric-key-permissions-transact-sql"></a>REVOKE (Autorisations de clé asymétrique) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Révoque les autorisations associées à une clé asymétrique.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
REVOKE [ GRANT OPTION FOR ] { permission  [ ,...n ] }   
    ON ASYMMETRIC KEY :: asymmetric_key_name   
    { TO | FROM } database_principal [ ,...n ]  
    [ CASCADE ]  
    [ AS revoking_principal ]  
```  
  
## <a name="arguments"></a>Arguments  
 GRANT OPTION FOR  
 Indique que la possibilité d'accorder l'autorisation spécifiée sera révoquée.  
  
> [!IMPORTANT]  
>  Si le principal possède l'autorisation spécifiée sans l'option GRANT, l'autorisation elle-même sera révoquée.  
  
 *autorisation*  
 Spécifie une autorisation qu'il est possible de révoquer sur un assembly. Voir ci-dessous.  
  
 SUR la clé asymétrique **::***asymmetric_key_name*  
 Spécifie la clé asymétrique sur laquelle l'autorisation est révoquée. Le qualificateur d’étendue **::** est requis.  
  
 *principal_base_de_données*  
 Spécifie le principal pour lequel l'autorisation est révoquée. Il peut s'agir :  
  
-   Utilisateur de base de données  
  
-   Rôle de base de données  
  
-   Rôle d'application  
  
-   Utilisateur de base de données mappé à une connexion Windows  
  
-   Utilisateur de base de données mappé à un groupe Windows  
  
-   Utilisateur de base de données mappé à un certificat  
  
-   Utilisateur de base de données mappé à une clé asymétrique  
  
-   Utilisateur de la base de données non associé à un principal de serveur  
  
 CASCADE  
 Indique que l'autorisation en cours de révocation est également révoquée sur les principaux auxquels cette autorisation a été accordée ou révoquée par ce principal. L'autorisation elle-même ne sera pas révoquée.  
  
> [!CAUTION]  
>  Une révocation en cascade d'une autorisation accordée avec l'option WITH GRANT OPTION entraîne la révocation des deux options GRANT et DENY de cette autorisation.  
  
 En tant que *revoking_principal*  
 Spécifie un principal dont le principal qui exécute cette requête dérive son droit de révoquer l'autorisation. Il peut s'agir :  
  
-   Utilisateur de base de données  
  
-   Rôle de base de données  
  
-   Rôle d'application  
  
-   Utilisateur de base de données mappé à une connexion Windows  
  
-   Utilisateur de base de données mappé à un groupe Windows  
  
-   Utilisateur de base de données mappé à un certificat  
  
-   Utilisateur de base de données mappé à une clé asymétrique  
  
-   Utilisateur de la base de données non associé à un principal de serveur  
  
## <a name="remarks"></a>Notes  
 Une clé asymétrique est un élément sécurisable au niveau base de données contenu dans la base de données parente dans la hiérarchie des autorisations. Les autorisations les plus spécifiques et limitées qui peuvent être révoquées sur une clé asymétrique sont énumérées ci-dessous, ainsi que les autorisations plus générales qui les incluent par implication.  
  
|Autorisation de clé asymétrique|Impliquée par une autorisation de clé asymétrique|Impliquée par une autorisation de base de données|  
|-------------------------------|------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ASYMMETRIC KEY|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation CONTROL sur la clé asymétrique.  
  
## <a name="see-also"></a>Voir aussi  
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CRÉER un rôle d’APPLICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

