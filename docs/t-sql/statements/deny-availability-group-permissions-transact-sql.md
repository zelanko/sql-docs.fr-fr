---
title: "REFUSER des autorisations de groupe de disponibilité (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], permissions
- permissions [SQL Server], availability group
- DENY statement, availability groups
- denying permissions, [SQL Server], availability groups
ms.assetid: bda60b36-a0b9-4c20-80c1-6a5cb1d638a5
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4c51420215c7de26caea8a3feed66d67bb2ba07
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="deny-availability-group-permissions-transact-sql"></a>DENY (Refus d'autorisations de groupe de disponibilité) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Refuse des autorisations sur un groupe de disponibilité Always On dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DENY permission  [ ,...n ] ON AVAILABILITY GROUP :: availability_group_name  
        TO < server_principal >  [ ,...n ]  
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
 Spécifie une autorisation qu'il est possible de refuser sur un groupe de disponibilité. Pour obtenir la liste des autorisations, consultez la section Notes plus loin dans cette rubrique.  
  
 SUR le groupe de disponibilité **::***availability_group_name*  
 Spécifie le groupe de disponibilité sur lequel l'autorisation est refusée. Le qualificateur d’étendue (**::**) est requis.  
  
 POUR \<principal_de_serveur >  
 Spécifie la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour laquelle l'autorisation doit être refusée.  
  
 *SQL_Server_login*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_from_Windows_login*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée à partir d'une connexion Windows.  
  
 *SQL_Server_login_from_certificate*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappée sur un certificat.  
  
 *SQL_Server_login_from_AsymKey*  
 Spécifie le nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappée sur une clé asymétrique.  
  
 CASCADE  
 Indique que l'autorisation à refuser est également refusée pour les autres principaux auxquels elle a été accordée par ce principal.  
  
 En tant que *SQL_Server_login*  
 Spécifie la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de laquelle le principal qui exécute cette requête dérive son droit de refuser l'autorisation.  
  
## <a name="remarks"></a>Notes  
 Autorisations au niveau de l’étendue du serveur peuvent être refusées uniquement lorsque la base de données actuelle est **master**.  
  
 Informations sur les groupes de disponibilité sont visibles dans le [sys.availability_groups &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) affichage catalogue. Pour plus d’informations sur les autorisations de serveur sont visibles dans le [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) vue de catalogue et des informations sur les principaux de serveur est visible dans le [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) vue de catalogue.  
  
 Un groupe de disponibilité est un élément sécurisable au niveau serveur. Les autorisations les plus spécifiques et limitées qu'il est possible de refuser sur un groupe de disponibilité sont répertoriées dans le tableau ci-dessous, avec les autorisations plus générales qui les incluent de manière implicite.  
  
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
  
### <a name="a-denying-view-definition-permission-on-an-availability-group"></a>A. Refus de l'autorisation VIEW DEFINITION sur un groupe de disponibilité  
 L'exemple suivant refuse l'autorisation `VIEW DEFINITION` sur le groupe de disponibilité `MyAg` sur la connexion `ZArifin`de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
USE master;  
DENY VIEW DEFINITION ON AVAILABILITY GROUP::MyAg TO ZArifin;  
GO  
```  
  
### <a name="b-denying-take-ownership-permission-with-the-cascade-option"></a>B. Refus d'une autorisation TAKE OWNERSHIP avec l'optio CASCADE  
 Dans l'exemple ci-dessous, l'autorisation `TAKE OWNERSHIP` sur le groupe de disponibilité `MyAg` est refusée à l'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `PKomosinski` avec l'option `CASCADE`.  
  
```  
USE master;  
DENY TAKE OWNERSHIP ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    CASCADE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations de groupe de disponibilité REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)   
 [Autorisations de groupe de disponibilité GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [Sys.availability_groups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Affichages catalogue des groupes de disponibilité Always On &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
