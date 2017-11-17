---
title: "Base de données de l’octroi d’une étendue d’informations d’identification (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 06/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GRANT DATABASE SCOPED CREDENTIAL
- GRANT_DATABASE_SCOPED_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], database scoped credential
- permissions [SQL Server], database scoped credential
- database scoped credential [SQL Server], permissions
- GRANT statement, database scoped credentials
ms.assetid: 501f2c8a-6aeb-41af-bf0b-974d17af33c0
caps.latest.revision: 3
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8fff82fbd6c81fea9cd9a7a95cabf35b0b8ecb7f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="grant-database-scoped-credential-permissions-transact-sql"></a>ALLOCATION de base de données étendue des autorisations d’informations d’identification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Accorde les autorisations requises sur une base de données d’une étendue d’informations d’identification. 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GRANT permission  [ ,...n ]    
    ON DATABASE SCOPED CREDENTIAL :: credential_name   
    TO principal [ ,...n ] [ WITH GRANT OPTION ]   
    [ AS granting_principal ]   
```  
  
## <a name="arguments"></a>Arguments  
 *autorisation*  
 Spécifie une autorisation qui peut être accordée sur une base de données d’une étendue d’informations d’identification. Voir ci-dessous.  
  
 SUR les informations d’identification de base de données d’une étendue **::***credential_name*  
 Spécifie les informations d’identification de la portée de la base de données sur lequel l’autorisation est accordée. Le qualificateur d'étendue "::" est indispensable.  
  
 *principal_base_de_données*  
 Spécifie le principal auquel l'autorisation est accordée. Il peut s'agir :  
  
-   d'un utilisateur de base de données ;  
-   d'un rôle de base de données ;  
-   d'un rôle d'application ;  
-   d'un utilisateur de base de données mappé sur une connexion Windows ;  
-   d'un utilisateur de base de données mappé sur un groupe Windows ;  
-   d'un utilisateur de base de données mappé sur un certificat ;  
-   d'un utilisateur de base de données mappé à une clé asymétrique ;  
-   d'un utilisateur de base de données qui n'est pas mappé sur le principal d'un serveur.  
  
GRANT OPTION  
 Indique que le principal a également la possibilité d'accorder l'autorisation spécifiée à d'autres principaux.  
  
En tant que *granting_principal*  
 Spécifie un principal dont le principal qui exécute cette requête dérive son droit d'accorder l'autorisation. Il peut s'agir :  
  
-   d'un utilisateur de base de données ;  
-   d'un rôle de base de données ;  
-   d'un rôle d'application ;  
-   d'un utilisateur de base de données mappé sur une connexion Windows ;  
-   d'un utilisateur de base de données mappé sur un groupe Windows ;  
-   d'un utilisateur de base de données mappé sur un certificat ;  
-   d'un utilisateur de base de données mappé à une clé asymétrique ;  
-   d'un utilisateur de base de données qui n'est pas mappé sur le principal d'un serveur.  
  
## <a name="remarks"></a>Notes  
 Informations d’identification d’une étendue de la base de données sont un base de données au niveau élément sécurisable contenu dans la base de données qui est son parent dans la hiérarchie des autorisations. Les autorisations plus spécifiques et limitées qui peuvent être accordées sur une information d’identification de base de données applique sont répertoriées ci-dessous, ainsi que les autorisations plus générales qui les incluent de manière implicite.  
  
|Autorisation des informations d’identification d’une étendue de base de données|Impliquée par une autorisation d’informations d’identification de base de données d’une étendue|Impliquée par une autorisation de base de données|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Le fournisseur d'autorisations (ou le principal spécifié avec l'option AS) doit posséder l'autorisation elle-même avec l'option GRANT OPTION ou une autorisation plus élevée qui implique l'autorisation accordée.  
  
 En cas d'utilisation de l'option AS, ces critères s'appliquent.  
  
|En tant que *granting_principal*|Autres autorisations nécessaires|  
|------------------------------|------------------------------------|  
|Utilisateur de base de données|L’autorisation IMPERSONATE sur l’utilisateur, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à une connexion Windows|L’autorisation IMPERSONATE sur l’utilisateur, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à un groupe Windows|L’appartenance au groupe Windows, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à un certificat|L’appartenance au **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance à la **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à une clé asymétrique|L’appartenance au **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance à la **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données qui n'est mappé sur aucun principal d'un serveur|L’autorisation IMPERSONATE sur l’utilisateur, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Rôle de base de données|L’autorisation ALTER sur le rôle, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Rôle d'application|L’autorisation ALTER sur le rôle, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
  
 Les propriétaires d'objets peuvent accorder des autorisations sur les objets qu'ils possèdent. Les principaux ayant l'autorisation CONTROL sur un élément sécurisable peuvent accorder une autorisation sur cet élément.  
  
 Les détenteurs de l’autorisation CONTROL SERVER, tels que les membres de la **sysadmin** rôle serveur fixe, peuvent accorder une autorisation sur n’importe quel élément sécurisable du serveur. Les détenteurs de l’autorisation CONTROL sur une base de données, tels que les membres de la **db_owner** rôle de base de données fixe, peuvent accorder une autorisation sur n’importe quel élément sécurisable dans la base de données. Les détenteurs de l'autorisation CONTROL sur un schéma peuvent accorder une autorisation sur n'importe quel objet dans ce schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Base de données de la révocation d’une étendue d’informations d’identification (Transact-SQL)](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)   
 [REFUSER l’étendue de la base de données d’informations d’identification (Transact-SQL)](../../t-sql/statements/deny-database-scoped-credential-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

