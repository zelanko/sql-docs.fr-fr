---
title: CREATE SERVER AUDIT SPECIFICATION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SERVER_AUDIT_SPECIFICATION_TSQL
- CREATE SERVER AUDIT SPECIFICATION
dev_langs: TSQL
helpviewer_keywords: CREATE SERVER AUDIT SPECIFICATION statement
ms.assetid: db77fa77-fedb-40ac-83e6-06343063e518
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06457f549575de83fc93c53d204a79061f4f4254
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="create-server-audit-specification-transact-sql"></a>CREATE SERVER AUDIT SPECIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée un objet de spécification d'audit de serveur à l'aide de la fonctionnalité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit. Pour plus d’informations, consultez [SQL Server Audit &#40moteur de base de données&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE SERVER AUDIT SPECIFICATION audit_specification_name  
FOR SERVER AUDIT audit_name  
{  
    { ADD ( { audit_action_group_name } )   
    } [, ...n]  
    [ WITH ( STATE = { ON | OFF } ) ]  
}  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *audit_specification_name*  
 Nom de la spécification d’audit de serveur.  
  
 *audit_name*  
 Nom de l’audit auquel cette spécification est appliquée.  
  
 *audit_action_group_name*  
 Nom d'un groupe d'actions pouvant être auditées au niveau du serveur. Pour obtenir la liste de groupes d’actions d’Audit, consultez [groupes d’actions d’Audit SQL Server et les Actions](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md).  
  
 AVEC **(** ÉTAT  **=**  {ON | {OFF} **)**  
 Active ou désactive la collecte d'enregistrements d'audit pour cette spécification d'audit.  
  
## <a name="remarks"></a>Notes  
 Un audit doit exister pour que vous puissiez créer une spécification d'audit de serveur correspondante. Lorsqu'une spécification d'audit de serveur est créée, elle est dans un état désactivé.  
  
## <a name="permissions"></a>Permissions  
 Les utilisateurs disposant de l'autorisation ALTER ANY SERVER AUDIT peuvent créer des spécifications d'audit du serveur et les lier à un audit quelconque.  
  
 Après la création d’une spécification d’audit de serveur, elle peut être affichée par des principaux avec le serveur de contrôle de base de données, ou des autorisations ALTER ANY SERVER AUDIT, le compte sysadmin ou principaux ayant un accès explicit à l’audit.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une spécification de l'audit du serveur nommée `HIPPA_Audit_Specification` qui audite les échecs de connexion, pour un audit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nommé `HIPPA_Audit`.  
  
```  
CREATE SERVER AUDIT SPECIFICATION HIPPA_Audit_Specification  
FOR SERVER AUDIT HIPPA_Audit  
    ADD (FAILED_LOGIN_GROUP);  
GO  
```  
  
 Pour obtenir un exemple complet sur la création d’un audit, consultez [SQL Server Audit &#40; moteur de base de données &#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CRÉER une spécification d’AUDIT de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sys.fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [Sys.server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [Sys.server_file_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [Sys.server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [Sys.server_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [Sys.Database audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [Sys.database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [Sys.dm_server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [Sys.dm_audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Créer un audit du serveur et une spécification d’audit du serveur](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
