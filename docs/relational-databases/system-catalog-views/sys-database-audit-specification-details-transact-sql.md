---
title: sys. database_audit_specification_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_audit_specification_details
- sys.database_audit_specification_details_TSQL
- sys.database_audit_specification_details
- database_audit_specification_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_audit_specification_details catalog view
ms.assetid: 03fc60a9-1696-4109-b15e-a50046310859
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4dcf9664adcdeba495b53f1a1392781df3fa60bd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67940287"
---
# <a name="sysdatabase_audit_specification_details-transact-sql"></a>sys.database_audit_specification_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations sur les spécifications de l’audit de la base de données dans un audit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur une instance de serveur, pour toutes les bases de données. Pour plus d’informations, consultez [SQL Server Audit &#40;moteur de base de données&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md). Pour obtenir la liste de tous les audit_action_id et leurs noms, interrogez [sys. dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**database_specification_id**|**int**|ID de la spécification d'audit.|  
|**audit_action_id**|**int**|ID de l'action d'audit.|  
|**audit_action_name**|**Sa**|Nom de l'action d'audit ou du groupe d'actions d'audit|  
|**Classe**|**int**|Identifie la classe d'objets auditée.|  
|**class_ DESC**|**Nvarchar (60)**|Description de la classe d'objets auditée :<br /><br /> - SCHEMA<br /><br /> - TABLE|  
|**major_id**|**int**|ID majeur de l'objet audité, tel qu'un ID de table d'une action d'audit de table.|  
|**minor_id**|**Int**|ID secondaire de l'objet audité, interprété d'après la classe, telle que l'ID de colonne d'une action d'audit de table.|  
|**audited_principal_id**|**int**|Principal audité.|  
|**audited_result**|**Nvarchar (60)**|Résultats de l'action d'audit :<br /><br /> - SUCCESS AND FAILURE - SUCCESS<br /><br /> - FAILURE|  
|**is_group**|**64bits**|Indique si l'objet est un groupe :<br /><br /> 0 - Pas un groupe<br /><br /> 1 - Groupe|  
  
## <a name="permissions"></a>Autorisations  
 Les principaux avec les autorisations **ALTER ANY DATABASE audit** ou **View definition** , le rôle **dbo** et les membres du rôle de base de données fixe **db_owners** ont accès à cet affichage catalogue. En outre, l’autorisation **View definition** ne doit pas être refusée au principal.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER un AUDIT de serveur &#40;&#41;Transact-SQL](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;&#41;Transact-SQL](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CRÉER une spécification de l’AUDIT du serveur &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [SUPPRIMER la spécification de l’AUDIT du serveur &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CRÉER une spécification d’AUDIT de base de données &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [SUPPRIMER la spécification de l’AUDIT de la base de données &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZation &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys. fn_get_audit_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys. server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys. server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys. server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys. server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys. database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys. dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys. dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys. dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Créer un audit du serveur et une spécification d'audit du serveur](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
