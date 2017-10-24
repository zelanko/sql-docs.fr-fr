---
title: ALTER SERVER ROLE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/06/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SERVER_ROLE_TSQL
- ALTER SERVER ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- SERVER ROLE, ALTER
- ALTER SERVER ROLE statement
ms.assetid: 7a4db7bb-c442-4e12-9a8a-114da5bc7710
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5f88c9aaf3e541d4213a3adeb77a0e457deb7c06
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-server-role-transact-sql"></a>ALTER SERVER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-pdw-md.md)]

Modifie l'appartenance d'un rôle serveur ou modifie le nom d'un rôle serveur défini par l'utilisateur. Les rôles serveur fixes ne peuvent pas être renommés.  
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server  
  
ALTER SERVER ROLE server_role_name   
{  
    [ ADD MEMBER server_principal ]  
  | [ DROP MEMBER server_principal ]  
  | [ WITH NAME = new_server_role_name ]  
} [ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
ALTER SERVER ROLE  server_role_name  ADD MEMBER login;  
  
ALTER SERVER ROLE  server_role_name  DROP MEMBER login;  
```  
  
## <a name="arguments"></a>Arguments  
*nom_rôle_serveur*  
Nom du rôle de serveur à modifier.  
  
Ajouter un membre *server_principal*  
Ajoute le principal de serveur spécifié au rôle de serveur. *server_principal* peut être un compte de connexion ou un rôle de serveur défini par l’utilisateur. *server_principal* ne peut pas être un rôle serveur fixe, un rôle de base de données ou administrateur système.  
  
DROP MEMBER *server_principal*  
Supprime le principal de serveur spécifié du rôle de serveur. *server_principal* peut être un compte de connexion ou un rôle de serveur défini par l’utilisateur. *server_principal* ne peut pas être un rôle serveur fixe, un rôle de base de données ou administrateur système.  
  
AVEC le nom  **=**  *new_server_role_name*  
Spécifie le nouveau nom du rôle de serveur défini par l'utilisateur. Ce nom ne peut pas déjà exister dans le serveur.  
  
## <a name="remarks"></a>Notes  
La modification du nom d'un rôle de serveur défini par l'utilisateur ne modifie pas le numéro d'identification, le propriétaire ou les autorisations du rôle.  
  
Pour modifier l’appartenance au rôle, `ALTER SERVER ROLE` remplace sp_addsrvrolemember et sp_dropsrvrolemember. Ces procédures stockées sont déconseillées.  
  
Vous pouvez consulter des rôles de serveur en interrogeant les affichages catalogue `sys.server_role_members` et `sys.server_principals`.  
  
Pour modifier le propriétaire d’un rôle de serveur défini par l’utilisateur, utilisez [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
Requiert `ALTER ANY SERVER ROLE` autorisation sur le serveur pour modifier le nom d’un rôle de serveur défini par l’utilisateur.  
  
**Rôles serveur fixes**  
  
Pour ajouter un membre à un rôle serveur fixe, vous devez être membre de ce rôle serveur fixe ou du rôle serveur fixe `sysadmin`.  
  
> [!NOTE]  
>  Le `CONTROL SERVER` et `ALTER ANY SERVER ROLE` autorisations ne sont pas suffisantes pour exécuter `ALTER SERVER ROLE` pour un rôle serveur fixe, et `ALTER` autorisation ne peut pas être accordée sur un rôle serveur fixe.  
  
**Rôles serveur définis par l’utilisateur**  
  
Pour ajouter un membre à un rôle de serveur défini par l’utilisateur, vous devez être un membre de la `sysadmin` rôle serveur fixe ou avez `CONTROL SERVER` ou `ALTER ANY SERVER ROLE` autorisation. Ou vous devez avoir `ALTER` autorisation sur ce rôle.  
  
> [!NOTE]  
>  Contrairement aux rôles serveur fixes, les membres d'un rôle de serveur défini par l'utilisateur n'ont pas intrinsèquement l'autorisation d'ajouter des membres à ce même rôle.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-the-name-of-a-server-role"></a>A. Modification du nom d'un rôle de serveur  
L'exemple suivant crée un rôle de serveur nommé `Product`, puis modifie le nom du rôle de serveur en `Production`.  
  
```  
CREATE SERVER ROLE Product ;  
ALTER SERVER ROLE Product WITH NAME = Production ;  
GO  
```  
  
### <a name="b-adding-a-domain-account-to-a-server-role"></a>B. Ajout d'un compte de domaine à un rôle de serveur  
L’exemple suivant ajoute un compte de domaine nommé `adventure-works\roberto0` au rôle de serveur défini par l’utilisateur nommé `Production`.  
  
```  
ALTER SERVER ROLE Production ADD MEMBER [adventure-works\roberto0] ;  
```  
  
### <a name="c-adding-a-sql-server-login-to-a-server-role"></a>C. Ajout d'un compte de connexion SQL Server à un rôle de serveur  
L’exemple suivant ajoute un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion nommée `Ted` à la `diskadmin` rôle serveur fixe.  
  
```  
ALTER SERVER ROLE diskadmin ADD MEMBER Ted ;  
GO  
```  
  
### <a name="d-removing-a-domain-account-from-a-server-role"></a>D. Suppression d'un compte de domaine d'un rôle de serveur  
L’exemple suivant supprime un compte de domaine nommé `adventure-works\roberto0` du rôle de serveur défini par l’utilisateur nommé `Production`.  
  
```  
ALTER SERVER ROLE Production DROP MEMBER [adventure-works\roberto0] ;  
```  
  
### <a name="e-removing-a-sql-server-login-from-a-server-role"></a>E. Suppression d'un compte de connexion SQL Server d'un rôle de serveur  
L’exemple suivant supprime le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion `Ted` à partir de la `diskadmin` rôle serveur fixe.  
  
```  
ALTER SERVER ROLE Production DROP MEMBER Ted ;  
GO  
```  
  
### <a name="f-granting-a-login-the-permission-to-add-logins-to-a-user-defined-server-role"></a>F. Octroi à un compte de connexion de l'autorisation d'ajouter des comptes de connexion à un rôle de serveur défini par l'utilisateur  
L'exemple suivant permet à `Ted` d'ajouter d'autres comptes de connexion au rôle de serveur défini par l'utilisateur nommé `Production`.  
  
```  
GRANT ALTER ON SERVER ROLE::Production TO Ted ;  
GO  
```  
  
### <a name="g-to-view-role-membership"></a>G. Pour consulter l'appartenance à un rôle  
Pour afficher l’appartenance au rôle, utilisez la **le rôle de serveur (membres)** page [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou exécutez la requête suivante :  
  
```  
SELECT SRM.role_principal_id, SP.name AS Role_Name,   
SRM.member_principal_id, SP2.name  AS Member_Name  
FROM sys.server_role_members AS SRM  
JOIN sys.server_principals AS SP  
    ON SRM.Role_principal_id = SP.principal_id  
JOIN sys.server_principals AS SP2   
    ON SRM.member_principal_id = SP2.principal_id  
ORDER BY  SP.name,  SP2.name  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Exemples :[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="h-basic-syntax"></a>H. Syntaxe de base  
L’exemple suivant ajoute la connexion `Anna` à la `LargeRC` rôle de serveur.  
  
```  
ALTER SERVER ROLE LargeRC ADD MEMBER Anna;  
```  
  
### <a name="i-remove-a-login-from-a-resource-class"></a>I. Supprimer une connexion à partir d’une classe de ressource.  
L’exemple suivant supprime l’appartenance de d’Anna le `LargeRC` rôle de serveur.  
  
```  
ALTER SERVER ROLE LargeRC DROP MEMBER Anna;  
```  
  
## <a name="see-also"></a>Voir aussi  
[CRÉER le rôle de serveur &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-role-transact-sql.md)   
[DROP SERVER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-role-transact-sql.md)   
[CRÉER un rôle &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
[ALTER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
[DROP ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
[Sécurité stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
[Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
[Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
[Sys.server_role_members &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)   
[sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  

