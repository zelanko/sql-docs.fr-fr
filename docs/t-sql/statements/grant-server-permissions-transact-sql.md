---
title: ACCORDER des autorisations Server (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
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
- GRANT statement, servers
- permissions [SQL Server], servers
- servers [SQL Server], permissions
- granting permissions [SQL Server], servers
ms.assetid: 7e880a5a-3bdc-491f-a167-7a9ed338be7f
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 19c46828634ccd9a2ebced169b32381402c4f224
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="grant-server-permissions-transact-sql"></a>GRANT – octroi d'autorisations de serveur (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet d'accorder des autorisations sur un serveur. 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GRANT permission [ ,...n ]   
    TO <grantee_principal> [ ,...n ] [ WITH GRANT OPTION ]  
    [ AS <grantor_principal> ]  
  
<grantee_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
  
<grantor_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
```  
  
## <a name="arguments"></a>Arguments  
 *autorisation*  
 Spécifie une autorisation qui peut être accordée sur un serveur. Pour obtenir la liste des autorisations, consultez la section Notes plus loin dans cette rubrique.  
  
 POUR \<principal_bénéficiaire > Spécifie le principal auquel l’autorisation est accordée.  
  
 En tant que \<grantor_principal > Spécifie le principal à partir duquel le principal qui exécute cette requête dérive son droit d’accorder l’autorisation.  
  
 WITH GRANT OPTION  
 Indique que le principal a également la possibilité d'accorder l'autorisation spécifiée à d'autres principaux.  
  
 *SQL_Server_login*  
 Spécifie une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_mapped_to_Windows_login*  
 Spécifie une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappée sur une connexion Windows.  
  
 *SQL_Server_login_mapped_to_Windows_group*  
 Spécifie une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappée sur un groupe Windows.  
  
 *SQL_Server_login_mapped_to_certificate*  
 Spécifie un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappé à un certificat.  
  
 *SQL_Server_login_mapped_to_asymmetric_key*  
 Spécifie un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappé à une clé asymétrique.  
  
 *server_role*  
 Spécifie un rôle de serveur défini par l'utilisateur.  
  
## <a name="remarks"></a>Notes  
 Les autorisations dans l'étendue du serveur peuvent être accordées seulement lorsque la base de données en cours est master.  
  
 Informations sur les autorisations de serveur peuvent être consultées dans le [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) vue de catalogue et des informations sur les principaux de serveur peuvent être affichés dans le [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) vue de catalogue. Informations sur l’appartenance des rôles de serveur peuvent être consultées dans le [sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md) affichage catalogue.  
  
 Un serveur représente le plus haut niveau de la hiérarchie des autorisations. Les autorisations les plus spécifiques et limitées qu'il est possible d'accorder sur un serveur sont répertoriées dans le tableau ci-dessous.  
  
|Autorisation de serveur|Déduite d'une autorisation de serveur|  
|-----------------------|----------------------------------|  
|ADMINISTER BULK OPERATIONS|CONTROL SERVER|  
|ALTER ANY AVAILABILITY GROUP<br /><br /> **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|ALTER ANY CONNECTION|CONTROL SERVER|  
|ALTER ANY CREDENTIAL|CONTROL SERVER|  
|ALTER ANY DATABASE|CONTROL SERVER|  
|ALTER ANY ENDPOINT|CONTROL SERVER|  
|ALTER ANY EVENT NOTIFICATION|CONTROL SERVER|  
|ALTER ANY EVENT SESSION|CONTROL SERVER|  
|ALTER ANY LINKED SERVER|CONTROL SERVER|  
|ALTER ANY LOGIN|CONTROL SERVER|  
|ALTER ANY SERVER AUDIT|CONTROL SERVER|  
|ALTER ANY SERVER ROLE<br /><br /> **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|ALTER RESOURCES|CONTROL SERVER|  
|ALTER SERVER STATE|CONTROL SERVER|  
|ALTER SETTINGS|CONTROL SERVER|  
|ALTER TRACE|CONTROL SERVER|  
|AUTHENTICATE SERVER|CONTROL SERVER|  
|CONNECT ANY DATABASE<br /><br /> **S'applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via la [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|CONNECT SQL|CONTROL SERVER|  
|CONTROL SERVER|CONTROL SERVER|  
|CREATE ANY DATABASE|ALTER ANY DATABASE|  
|CREATE AVAILABILITY GROUP<br /><br /> **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|ALTER ANY AVAILABILITY GROUP|  
|CREATE DDL EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|CREATE ENDPOINT|ALTER ANY ENDPOINT|  
|CREATE SERVER ROLE<br /><br /> **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|ALTER ANY SERVER ROLE|  
|CREATE TRACE EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|EXTERNAL ACCESS ASSEMBLY|CONTROL SERVER|  
|IMPERSONATE ANY LOGIN<br /><br /> **S'applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via la [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|SELECT ALL USER SECURABLES<br /><br /> **S'applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via la [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|SHUTDOWN|CONTROL SERVER|  
|UNSAFE ASSEMBLY|CONTROL SERVER|  
|VIEW ANY DATABASE|VIEW ANY DEFINITION|  
|VIEW ANY DEFINITION|CONTROL SERVER|  
|VIEW SERVER STATE|ALTER SERVER STATE|  
  
## <a name="remarks"></a>Notes  
 Les trois autorisations de serveur suivantes ont été ajoutées dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 **Se connecter à une base de données** autorisation  
 Accordez l'autorisation **CONNECT ANY DATABASE** à une connexion qui doit se connecter à toutes les bases de données existantes et à celles qui pourront être créées. N'accorde pas d'autorisation dans une base de données au-delà de la connexion. Combiner avec **SELECT ALL USER SECURABLES** ou **VIEW SERVER STATE** pour autoriser un processus d’audit afficher toutes les données ou tous les États de la base de données sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Emprunter l’identité de n’importe quelle connexion** autorisation  
 Lorsque cette autorisation est accordée, elle permet à un processus de niveau intermédiaire d'emprunter l'identité du compte des clients qui se connectent, à mesure qu'il se connecte aux bases de données. Si cette autorisation est refusée, une connexion dotée de privilèges élevés peut être bloquée à partir de l'emprunt d'identité d'autres connexions. Par exemple, une connexion dotée de l'autorisation **CONTROL SERVER** peut être bloquée à partir de l'emprunt d'identité d'autres connexions.  
  
 **Sélectionnez tous les éléments SÉCURISABLES d’utilisateur** autorisation  
 Lorsque cette autorisation est accordée, une connexion telle qu'un auditeur peut afficher les données de toutes les bases de données auxquelles l'utilisateur se connecte. Lorsque refusé, empêche l’accès aux objets, sauf si elles sont dans le **sys** schéma.  
  
## <a name="permissions"></a>Permissions  
 Le fournisseur d'autorisations (ou le principal spécifié avec l'option AS) doit posséder l'autorisation elle-même avec l'option GRANT OPTION ou une autorisation plus élevée qui implique l'autorisation accordée. Les membres du rôle serveur fixe sysadmin peuvent accorder toutes les autorisations.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-granting-a-permission-to-a-login"></a>A. Octroi d'une autorisation à une connexion  
 Dans l'exemple ci-dessous, l'autorisation `CONTROL SERVER` est accordée à la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `TerryEminhizer`.  
  
```  
USE master;  
GRANT CONTROL SERVER TO TerryEminhizer;  
GO  
```  
  
### <a name="b-granting-a-permission-that-has-grant-permission"></a>B. Octroi d'une autorisation qui possède l'autorisation GRANT  
 Dans l'exemple suivant, l'autorisation `ALTER ANY EVENT NOTIFICATION` est accordée à la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `JanethEsteves` avec le droit d'accorder cette autorisation à une autre connexion.  
  
```  
USE master;  
GRANT ALTER ANY EVENT NOTIFICATION TO JanethEsteves WITH GRANT OPTION;  
GO  
```  
  
### <a name="c-granting-a-permission-to-a-server-role"></a>C. Octroi d'une autorisation à un rôle de serveur  
 L'exemple suivant crée deux rôles de serveur nommés `ITDevAdmin` et `ITDevelopers`. Il accorde l'autorisation `ALTER ANY DATABASE` au rôle de serveur défini par l'utilisateur `ITDevAdmin`, notamment l'option `WITH GRANT` afin que le rôle de serveur `ITDevAdmin` puisse réaffecter l'autorisation `ALTER ANY DATABASE` L'exemple accorde ensuite à `ITDevelopers` l'autorisation d'utiliser l'autorisation `ALTER ANY DATABASE` du rôle de serveur `ITDevAdmin`.  
  
```  
USE master;  
CREATE SERVER ROLE ITDevAdmin ;  
CREATE SERVER ROLE ITDevelopers ;  
GRANT ALTER ANY DATABASE TO ITDevAdmin WITH GRANT OPTION ;  
GRANT ALTER ANY DATABASE TO ITDevelopers AS ITDevAdmin ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [REFUSER des autorisations de serveur &#40; Transact-SQL &#41;](../../t-sql/statements/deny-server-permissions-transact-sql.md)   
 [RÉVOQUER les autorisations de serveur &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-server-permissions-transact-sql.md)   
 [Hiérarchie des autorisations &#40;Moteur de base de données&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [Sys.fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  


