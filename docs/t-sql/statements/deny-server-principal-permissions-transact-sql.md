---
title: REFUSER des autorisations de serveur Principal (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/09/2017
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
- DENY statement, impersonate
- permissions [SQL Server], impersonate
- impersonate [SQL Server], denying
- DENY statement, logins
- permissions [SQL Server], logins
- denying permissions [SQL Server], logins
- servers [SQL Server], permissions
- logins [SQL Server], denying access
ms.assetid: 859affa7-0567-47d1-9490-57c1abbd619b
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 15be2bfb51e6cdd9d111f052c62838c3326c61b5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="deny-server-principal-permissions-transact-sql"></a>DENY – refus d'autorisations du principal de serveur (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet de refuser des autorisations accordées sur une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DENY permission [ ,...n ] }   
    ON   
    { [ LOGIN :: SQL_Server_login ]  
      | [ SERVER ROLE :: server_role ] }   
    TO <server_principal> [ ,...n ]  
    [ CASCADE ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
    SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey   
    | server_role  
```  
  
## <a name="arguments"></a>Arguments  
 *autorisation*  
 Spécifie une autorisation qui peut être refusée sur une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des autorisations, consultez la section Notes plus loin dans cette rubrique.  
  
 CONNEXION **::** *SQL_Server_login*  
 Spécifie la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur laquelle l'autorisation doit être refusée. Le qualificateur d’étendue (**::**) est requis.  
  
 RÔLE de serveur **::** *server_role*  
 Spécifie le rôle de serveur sur lequel l'autorisation est refusée. Le qualificateur d’étendue (**::**) est requis.  
  
 POUR \<principal_de_serveur >  
 Spécifie le compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou le rôle de serveur pour lequel l'autorisation est accordée.  
  
 POUR *SQL_Server_login*  
 Spécifie la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour laquelle l'autorisation doit être refusée.  
  
 *SQL_Server_login*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_from_Windows_login*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée à partir d'une connexion Windows.  
  
 *SQL_Server_login_from_certificate*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappée sur un certificat.  
  
 *SQL_Server_login_from_AsymKey*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappée sur une clé asymétrique.  
  
 *server_role*  
 Spécifie le nom d'un rôle de serveur.  
  
 CASCADE  
 Indique que l'autorisation à refuser est également refusée pour les autres principaux auxquels elle a été accordée par ce principal.  
  
 En tant que *SQL_Server_login*  
 Spécifie la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de laquelle le principal qui exécute cette requête dérive son droit de refuser l'autorisation.  
  
## <a name="remarks"></a>Notes  
 Les autorisations dans l'étendue du serveur peuvent être refusées seulement lorsque la base de données en cours est master.  
  
 Pour plus d’informations sur les autorisations de serveur sont disponibles dans le [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) affichage catalogue. Informations sur les principaux de serveur sont disponibles dans le [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) vue de catalogue.  
  
 L’instruction DENY échoue si CASCADE n’est pas spécifié lors du refus d’une autorisation à une entité qui a été accordée cette autorisation avec l’option GRANT OPTION.  
  
 Les comptes de connexion et les rôles de serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont des éléments sécurisables au niveau du serveur. Les autorisations les plus spécifiques et limitées qu'il est possible de refuser sur un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un rôle de serveur sont répertoriées dans le tableau ci-dessous, avec les autorisations plus générales qui les incluent de manière implicite.  
  
|Compte de connexion SQL Server ou autorisation de rôle de serveur|Déduite d'une autorisation de rôle de serveur ou de compte de connexion SQL Server|Déduite d'une autorisation de serveur|  
|------------------------------------------------|-----------------------------------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL SERVER|  
|IMPERSONATE|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
|ALTER|CONTROL|ALTER ANY LOGIN<br /><br /> ALTER ANY SERVER ROLE|  
  
## <a name="permissions"></a>Permissions  
 Pour les comptes de connexion, requiert l'autorisation CONTROL sur le compte de connexion ou l'autorisation ALTER ANY LOGIN sur le serveur.  
  
 Pour les rôles de serveur, requiert l'autorisation CONTROL sur le rôle de serveur ou l'autorisation ALTER ANY SERVER ROLE sur le serveur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-denying-impersonate-permission-on-a-login"></a>A. Refus d'une autorisation IMPERSONATE sur une connexion  
 L’exemple suivant refuse `IMPERSONATE` l’autorisation sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion `WanidaBenshoof` à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion créée à partir de l’utilisateur Windows `AdvWorks\YoonM`.  
  
```  
USE master;  
DENY IMPERSONATE ON LOGIN::WanidaBenshoof TO [AdvWorks\YoonM];  
GO  
```  
  
### <a name="b-denying-view-definition-permission-with-cascade"></a>B. Refuser l’autorisation VIEW DEFINITION avec l’option CASCADE  
 Dans l'exemple ci-dessous, l'autorisation `VIEW DEFINITION` sur la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `EricKurjan` est refusée à la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `RMeyyappan`. L'option `CASCADE` indique que l'autorisation `VIEW DEFINITION` sur `EricKurjan` sera également refusée aux principaux auxquels `RMeyyappan` a accordé cette autorisation.  
  
```  
USE master;  
DENY VIEW DEFINITION ON LOGIN::EricKurjan TO RMeyyappan   
    CASCADE;  
GO   
```  
  
### <a name="c-denying-view-definition-permission-on-a-server-role"></a>C. Refus d'une autorisation VIEW DEFINITION sur un rôle de serveur  
 L'exemple suivant refuse `VIEW DEFINITION` sur le rôle de serveur `Sales` au rôle de serveur `Auditors`.  
  
```  
USE master;  
DENY VIEW DEFINITION ON SERVER ROLE::Sales TO Auditors ;  
GO   
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [Autorisations du principal du serveur GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-server-principal-permissions-transact-sql.md)   
 [Autorisations du principal du serveur REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-server-principal-permissions-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  

