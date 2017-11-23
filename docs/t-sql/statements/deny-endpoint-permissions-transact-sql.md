---
title: REFUSER des autorisations de point de terminaison (Transact-SQL) | Documents Microsoft
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
- endpoints [SQL Server], permissions
- DENY statement, endpoints
- denying permissions [SQL Server], endpoints
- permissions [SQL Server], endpoints
ms.assetid: 3ac40457-7529-4eda-95a4-5247345cc8cf
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93f438a2d3d546c6cb15672b5b617b4e35cee9a3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="deny-endpoint-permissions-transact-sql"></a>DENY – refus d'autorisations de point de terminaison (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet de refuser des autorisations sur un point de terminaison.  

  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DENY permission  [ ,...n ] ON ENDPOINT :: endpoint_name  
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
 Spécifie une autorisation qui peut être refusée sur un point de terminaison. Pour obtenir la liste des autorisations, consultez la section Notes plus loin dans cette rubrique.  
  
 SUR le point de terminaison **::***endpoint_name*  
 Spécifie le point de terminaison sur lequel l'autorisation doit être refusée. Le qualificateur d’étendue (**::**) est requis.  
  
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
  
 Informations sur les points de terminaison sont visibles dans le [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md) affichage catalogue. Pour plus d’informations sur les autorisations de serveur sont visibles dans le [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) vue de catalogue et des informations sur les principaux de serveur est visible dans le [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) vue de catalogue.  
  
 Un point de terminaison est un élément sécurisable au niveau serveur. Les autorisations les plus spécifiques et limitées qu'il est possible de refuser sur un point de terminaison sont répertoriées dans le tableau ci-dessous, avec les autorisations plus générales qui les incluent de manière implicite.  
  
|Autorisation de point de terminaison|Déduite d'une autorisation de point de terminaison|Déduite d'une autorisation de serveur|  
|-------------------------|------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY ENDPOINT|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL sur le point de terminaison ou l'autorisation ALTER ANY ENDPOINT sur le serveur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-denying-view-definition-permission-on-an-endpoint"></a>A. Refus d'une autorisation VIEW DEFINITION sur un point de terminaison  
 L’exemple suivant refuse `VIEW DEFINITION` l’autorisation sur le point de terminaison `Mirror7` à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion `ZArifin`.  
  
```  
USE master;  
DENY VIEW DEFINITION ON ENDPOINT::Mirror7 TO ZArifin;  
GO  
```  
  
### <a name="b-denying-take-ownership-permission-with-cascade-option"></a>B. Refus d'une autorisation TAKE OWNERSHIP avec l'option CASCADE  
 Dans l'exemple ci-dessous, l'autorisation `TAKE OWNERSHIP` sur le point de terminaison `Shipping83` est refusée à l'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `PKomosinski` et aux principaux auxquels `PKomosinski` a accordé l'autorisation `TAKE OWNERSHIP`.  
  
```  
USE master;  
DENY TAKE OWNERSHIP ON ENDPOINT::Shipping83 TO PKomosinski   
    CASCADE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations GRANT sur point de terminaison &#40;Transact-SQL&#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)   
 [RÉVOQUER les autorisations de point de terminaison &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)   
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [Affichages catalogue de points de terminaison &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [Sys.Endpoints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
