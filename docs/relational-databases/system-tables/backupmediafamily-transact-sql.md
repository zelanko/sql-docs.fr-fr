---
title: backupmediafamily (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- backupmediafamily
- backupmediafamily_TSQL
dev_langs: TSQL
helpviewer_keywords:
- backupmediafamily system table
- backup media [SQL Server], backupmediafamily system table
ms.assetid: ee16de24-3d95-4b2e-a094-78df2514d18a
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7e814887bb97d14d165c39ad4a8d634bf84947b1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="backupmediafamily-transact-sql"></a>backupmediafamily (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette table contient une ligne pour chaque famille de supports de sauvegardes. Si une famille de supports réside dans un support de sauvegarde miroir, elle a une ligne distincte pour chaque miroir du support de sauvegarde. Cette table est stockée dans le **msdb** base de données.  
    
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|Numéro d'identification unique du support de sauvegarde dont cette famille est membre. Références **backupmediaset (media_set_id)**|  
|**family_sequence_number**|**tinyint**|Position de la famille de supports dans le support de sauvegarde.|  
|**media_family_id**|**uniqueidentifier**|Numéro d'identification unique de la famille de supports de sauvegarde. Sa valeur peut être NULL.|  
|**media_count**|**int**|Nombre de supports de sauvegarde dans la famille de supports. Sa valeur peut être NULL.|  
|**logical_device_name**|**nvarchar (128)**|Nom de cette unité de sauvegarde dans **sys.backup_devices.name**. S’il s’agit d’une unité de sauvegarde temporaire (par opposition à une unité de sauvegarde permanente qui existe dans **sys.backup_devices**), la valeur de **logical_device_name** a la valeur NULL.|  
|**physical_device_name**|**nvarchar (260)**|Nom physique de l'unité de sauvegarde Sa valeur peut être NULL.|  
|**device_type**|**tinyint**|Type de l'unité de sauvegarde :<br /><br /> 2 = Disque<br /><br /> 5 = Bande<br /><br /> 7 = Unité virtuelle<br /><br /> 105 = Unité de sauvegarde constante.<br /><br /> Sa valeur peut être NULL.<br /><br /> Tous les noms et les numéros d’unités peut être trouvé dans **sys.backup_devices**.|  
|**physical_block_size**|**int**|Taille du bloc physique réservé à l'écriture de la famille de supports de sauvegarde. Sa valeur peut être NULL.|  
|**mise en miroir**|**tinyint**|Nombre de miroirs (0-3).|  
  
## <a name="remarks"></a>Notes  
 RESTORE VERIFYONLY FROM *backup_device* WITH LOADHISTORY remplit les colonnes de la **backupmediaset** table avec les valeurs appropriées de l’en-tête du support de sauvegarde.  
  
 Pour réduire le nombre de lignes dans cette table et dans d’autres tables d’historique de sauvegarde et, exécutez le [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration Tables &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Tables système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
