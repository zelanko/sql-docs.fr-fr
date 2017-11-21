---
title: "Autorisations de groupe de disponibilité REVOKE (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
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
- Availability Groups [SQL Server], permissions
- REVOKE statement, availability groups
- revoking permissions, [SQL Server], availability groups
- permissions [SQL Server], availability group
ms.assetid: 02c77378-a36d-4286-9235-d8867a2b92ad
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1573f866cec3105cde4eeab59c230ede46144ac3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-availability-group-permissions-transact-sql"></a>REVOKE (Révocation d'autorisations de groupe de disponibilité) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Révoque des autorisations sur un groupe de disponibilité Always On. 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission  [ ,...n ]   
    ON AVAILABILITY GROUP :: availability_group_name  
    { FROM | TO } < server_principal >  [ ,...n ]  
    [ CASCADE ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
        SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey  
```  
  
## <a name="arguments"></a>Arguments  
 *autorisation*  
 Spécifie une autorisation qu'il est possible de révoquer sur un groupe de disponibilité. Pour obtenir la liste des autorisations, consultez la section Notes plus loin dans cette rubrique.  
  
 SUR le groupe de disponibilité **::***availability_group_name*  
 Spécifie le groupe de disponibilité sur lequel l'autorisation est révoquée. Le qualificateur d’étendue (**::**) est requis.  
  
 {À PARTIR DE | À} \<principal_de_serveur > Spécifie le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion auquel l’autorisation est révoquée.  
  
 *SQL_Server_login*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_from_Windows_login*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée à partir d'une connexion Windows.  
  
 *SQL_Server_login_from_certificate*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappée sur un certificat.  
  
 *SQL_Server_login_from_AsymKey*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappée sur une clé asymétrique.  
  
 GRANT OPTION  
 Indique que le droit d'accorder l'autorisation spécifiée à d'autres principaux sera révoqué. L'autorisation elle-même ne sera pas révoquée.  
  
> [!IMPORTANT]  
>  Si le principal possède l'autorisation spécifiée sans l'option GRANT, l'autorisation elle-même sera révoquée.  
  
 CASCADE  
 Indique que l'autorisation en cours de révocation est également révoquée sur les principaux auxquels cette autorisation a été accordée ou révoquée par ce principal.  
  
> [!IMPORTANT]  
>  Une révocation en cascade d'une autorisation accordée avec l'option WITH GRANT OPTION entraîne la révocation des deux options GRANT et DENY de cette autorisation.  
  
 En tant que *SQL_Server_login*  
 Spécifie la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de laquelle le principal qui exécute cette requête dérive son droit de révoquer l'autorisation.  
  
## <a name="remarks"></a>Notes  
 Révoquer des autorisations au niveau de l’étendue du serveur uniquement lorsque la base de données actuelle est **master**.  
  
 Informations sur les groupes de disponibilité sont visibles dans le [sys.availability_groups &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) affichage catalogue. Pour plus d’informations sur les autorisations de serveur sont visibles dans le [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) vue de catalogue et des informations sur les principaux de serveur est visible dans le [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) vue de catalogue.  
  
 Un groupe de disponibilité est un élément sécurisable au niveau serveur. Les autorisations les plus spécifiques et limitées qu'il est possible de révoquer sur un groupe de disponibilité sont répertoriées dans le tableau ci-dessous, avec les autorisations plus générales qui les incluent de manière implicite.  
  
|Autorisations de groupe de disponibilité|Impliquée par une autorisation de groupe de disponibilité|Déduite d'une autorisation de serveur|  
|-----------------------------------|----------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY AVAILABILITY GROUP|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL sur le groupe de disponibilité ou l'autorisation ALTER ANY AVAILABILTIY GROUP sur le serveur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-revoking-view-definition-permission-on-an-availability-group"></a>A. Révocation de l'autorisation VIEW DEFINITION sur un groupe de disponibilité  
 L'exemple suivant révoque l'autorisation `VIEW DEFINITION` sur le groupe de disponibilité `MyAg` sur la connexion `ZArifin`de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
USE master;  
REVOKE VIEW DEFINITION ON AVAILABILITY GROUP::MyAg TO ZArifin;  
GO  
```  
  
### <a name="b-revoking-take-ownership-permission-with-the-cascade"></a>B. Révocation de l'autorisation TAKE OWNERSHIP avec l'option CASCADE  
 Dans l'exemple ci-dessous, l'autorisation `TAKE OWNERSHIP` sur le groupe de disponibilité `MyAg` est révoquée pour l'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `PKomosinski` et pour tous les principaux auxquels `PKomosinski` a accordé l'autorisation TAKE sur MyAg.  
  
```  
USE master;  
REVOKE TAKE OWNERSHIP ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    CASCADE;  
GO  
```  
  
### <a name="c-revoking-a-previously-granted-with-grant-option-clause"></a>C. Révocation d'une clause WITH GRANT OPTION précédemment accordée  
 Si une autorisation a été accordée à l’aide de la clause WITH GRANT OPTION, utilisez REVOKE GRANT OPTION FOR... Pour supprimer la clause WITH GRANT OPTION. L'exemple suivant accorde l'autorisation puis supprime la partie WITH GRANT de l'autorisation.  
  
```  
USE master;  
GRANT CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    WITH GRANT OPTION;  
GO  
REVOKE GRANT OPTION FOR CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski  
CASCADE  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations de groupe de disponibilité GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)   
 [REFUSER des autorisations de groupe de disponibilité &#40; Transact-SQL &#41;](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [Sys.availability_groups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Affichages catalogue des groupes de disponibilité Always On &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


