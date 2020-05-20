---
title: backupfilegroup (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupfilegroup_TSQL
- backupfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], backupfilegroup system table
- backupfilegroup system table
ms.assetid: d26e8fbe-f5c5-4e10-b2bd-0d8e16ea21f9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0e2f1c1ae33bd94ffcbe6faef16523d7d808ac70
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827378"
---
# <a name="backupfilegroup-transact-sql"></a>backupfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque groupe de fichiers d'une base de données au moment de la sauvegarde. **backupfilegroup** est stocké dans la base de données **msdb** .  
  
> [!NOTE]  
>  La table **backupfilegroup** affiche la configuration du groupe de fichiers de la base de données, et non du jeu de sauvegarde. Pour déterminer si un fichier est inclus dans le jeu de sauvegarde, utilisez la colonne **is_present** de la table [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md) .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|Jeu de sauvegarde contenant ce groupe de fichiers.|  
|**name**|**sysname**|Nom du groupe de fichiers|  
|**filegroup_id**|**int**|ID du groupe de fichiers ; il est unique dans la base de données. Correspond à **data_space_id** dans **sys. FileGroups**.|  
|**filegroup_guid**|**uniqueidentifier**|Identificateur unique universel du groupe de fichiers. Sa valeur peut être NULL.|  
|**type**|**char(2)**|Type de contenu, un des suivants :<br /><br /> FG = Groupe de fichiers « Lignes »<br /><br /> SL = Groupe de fichiers de journal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**type_desc**|**nvarchar(60)**|Description du type de fonction, un des suivants :<br /><br /> ROWS_FILEGROUP<br /><br /> SQL_LOG_FILEGROUP|  
|**is_default**|**bit**|Groupe de fichiers par défaut ; il est utilisé quand aucun groupe de fichiers n'est spécifié dans CREATE TABLE ni dans CREATE INDEX.|  
|**is_readonly**|**bit**|1 = Le groupe de fichiers est en lecture seule.|  
|**log_filegroup_guid**|**uniqueidentifier**|Sa valeur peut être NULL.|  
  
## <a name="remarks"></a>Remarques  
  
> [!IMPORTANT]  
>  Le même nom de groupe de fichiers peut apparaître dans différentes bases de données ; néanmoins, chaque groupe de fichiers a son propre GUID. Par conséquent, **(backup_set_id, filegroup_guid)** est une clé unique qui identifie un groupe de fichiers dans **backupfilegroup**.  
  
 RESTORE VERIFYONLY à partir de *backup_device* avec LoadHistory remplit les colonnes de la table **backupmediaset** avec les valeurs appropriées de l’en-tête Media-Set.  
  
 Pour réduire le nombre de lignes dans cette table et dans d’autres tables de sauvegarde et d’historique, exécutez la procédure stockée [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration de tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Tables système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
