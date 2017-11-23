---
title: Sys.server_file_audits (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 04/05/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- server_file_audits_TSQL
- sys.server_file_audits_TSQL
- sys.server_file_audits
- server_file_audits
dev_langs: TSQL
helpviewer_keywords: sys.server_file_audits catalog view
ms.assetid: 553288a0-be57-4d79-ae53-b7cbd065e127
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 42a00870788129a007511766ea8b2a87ef73740d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysserverfileaudits-transact-sql"></a>sys.server_file_audits (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations détaillées sur le type d’audit de fichier dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’audit sur une instance de serveur. Pour plus d’informations, consultez [SQL Server Audit &#40moteur de base de données&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|audit_id|**int**|ID de l'audit.|  
|name|**sysname**|Nom de l’audit.|  
|audit_guid|**uniqueidentifier**|GUID de l'audit.|  
|create_date|**datetime**|Date UTC de création de l'audit de fichier.|  
|modify_date|**DateTime**|Date UTC de la dernière modification de l'audit de fichier.|  
|principal_id|**int**|ID du propriétaire de l'audit, tel qu'enregistré sur le serveur.|  
|Type|**char(2)**|Type d'audit :<br /><br /> 0 = Journal des événements de sécurité NT<br /><br /> 1 = Journal des événements d'applications NT<br /><br /> 2 = Fichier du système de fichiers|  
|type_desc|**nvarchar (60)**|Description du type d'audit.|  
|on_failure|**tinyint**|En cas d'échec :<br /><br /> 0 = Continuer<br /><br /> 1 = Arrêter l'instance de serveur<br /><br /> 2 = Faire échouer l'opération|  
|on_failure_desc|**nvarchar (60)**|En cas d'échec d'écriture d'une entrée d'audit :<br /><br /> CONTINUE<br /><br /> SHUTDOWN SERVER INSTANCE<br /><br /> FAIL OPERATION|  
|is_state_enabled|**tinyint**|0 = Désactivé<br /><br /> 1 = Activé|  
|queue_delay|**int**|Temps d'attente maximal suggéré, en millisecondes, avant d'écrire sur le disque. Si la valeur est 0, l'audit garantit une écriture avant la poursuite de l'événement.|  
|prédicat|**nvarchar(8000)**|Expression de prédicat qui est appliquée à l'événement.|  
|max_file_size|**bigint**|Taille maximale de l'audit en mégaoctets :<br /><br /> 0 = Illimitée/non applicable au type d'audit sélectionné.|  
|max_rollover_files|**int**|Nombre maximal de fichiers à utiliser avec l'option de substitution.|  
|max_files|**int**|Nombre maximal de fichiers à utiliser sans l'option de substitution.|  
|reserved_disk_space|**int**|Quantité d'espace disque à réserver par fichier.|  
|log_file_path|**nvarchar (260)**|Chemin d'accès à l'audit. Chemin d'accès au fichier pour l'audit de fichier, chemin d'accès du journal des applications pour l'audit de journal des applications.|  
|log_file_name|**nvarchar (260)**|Nom de base du fichier journal fourni dans CREATE AUDIT DDL. Un nombre incrémentiel est ajouté au fichier base_log_name en tant que suffixe pour la création du nom de fichier journal.|  
  
## <a name="permissions"></a>Permissions  
 Les principaux avec le **ALTER ANY SERVER AUDIT** ou **VIEW ANY DEFINITION** autorisation ont accès à cette vue de catalogue. En outre, l’entité de sécurité ne doit pas être refusée **VIEW ANY DEFINITION** autorisation.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CRÉER une spécification d’AUDIT de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sys.fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [Sys.server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [Sys.server_file_audits (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [Sys.server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [Sys.Database audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [Sys.database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [Sys.dm_server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [Sys.dm_audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Sys.dm_audit_class_type_map &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Créer un audit du serveur et une spécification d’audit du serveur](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
