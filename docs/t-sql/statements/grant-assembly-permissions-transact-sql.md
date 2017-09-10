---
title: Autorisations sur un Assembly de GRANT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/12/2017
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
- granting permissions [SQL Server], assemblies
- assemblies [CLR integration], permissions
- GRANT statement, assemblies
ms.assetid: dce1e027-f859-4967-bdda-16a95ae460d0
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dac4e6d367f159660d2743c3bee37ece397b7dd6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="grant-assembly-permissions-transact-sql"></a>GRANT - Autorisations sur un assembly (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Accorde des autorisations sur un assembly.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GRANT { permission [ ,...n ] } ON ASSEMBLY :: assembly_name  
    TO database_principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS granting_principal ]  
```  
  
## <a name="arguments"></a>Arguments  
 *autorisation*  
 Spécifie une autorisation qu'il est possible d'accorder sur un assembly. Voir ci-dessous.  
  
 SUR l’ASSEMBLY **::***assembly_name*  
 Spécifie l'assembly sur lequel l'autorisation est accordée. Le qualificateur d'étendue "::" est indispensable.  
  
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
 Un assembly est un élément sécurisable au niveau base de données contenu par la base de données parente dans la hiérarchie des autorisations. Les autorisations les plus particulières et les plus limitées qu'il est possible d'accorder sur un assembly sont mentionnées ci-dessous, ainsi que les autorisations plus générales qui les englobent implicitement.  
  
|Autorisation sur un assembly|Impliquée par une autorisation sur un assembly|Impliquée par une autorisation de base de données|  
|-------------------------|------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ASSEMBLY|  
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
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CRÉER un rôle d’APPLICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

