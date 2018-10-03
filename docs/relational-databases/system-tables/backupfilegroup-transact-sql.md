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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b1d7cc485899a7f8173552788471ef6ec45ce49c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832977"
---
# <a name="backupfilegroup-transact-sql"></a>backupfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque groupe de fichiers d'une base de données au moment de la sauvegarde. **backupfilegroup** est stocké dans le **msdb** base de données.  
  
> [!NOTE]  
>  Le **backupfilegroup** tableau présente la configuration de groupe de fichiers de la base de données, pas du jeu de sauvegarde. Pour déterminer si un fichier est inclus dans le jeu de sauvegarde, utilisez le **is_present** colonne de la [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md) table.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**Int**|Jeu de sauvegarde contenant ce groupe de fichiers.|  
|**nom**|**sysname**|Nom du groupe de fichiers|  
|**filegroup_id**|**Int**|ID du groupe de fichiers ; il est unique dans la base de données. Correspond à **data_space_id** dans **sys.filegroups**.|  
|**filegroup_guid**|**uniqueidentifier**|Identificateur unique universel du groupe de fichiers. Sa valeur peut être NULL.|  
|**type**|**char(2)**|Type de contenu, un des suivants :<br /><br /> FG = Groupe de fichiers « Lignes »<br /><br /> SL = Groupe de fichiers de journal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**type_desc**|**nvarchar(60)**|Description du type de fonction, un des suivants :<br /><br /> ROWS_FILEGROUP<br /><br /> SQL_LOG_FILEGROUP|  
|**is_default**|**bit**|Groupe de fichiers par défaut ; il est utilisé quand aucun groupe de fichiers n'est spécifié dans CREATE TABLE ni dans CREATE INDEX.|  
|**is_readonly**|**bit**|1 = Le groupe de fichiers est en lecture seule.|  
|**log_filegroup_guid**|**uniqueidentifier**|Sa valeur peut être NULL.|  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]  
>  Le même nom de groupe de fichiers peut apparaître dans différentes bases de données ; néanmoins, chaque groupe de fichiers a son propre GUID. Par conséquent, **(backup_set_id, filegroup_guid)** est une clé unique qui identifie un groupe de fichiers dans **backupfilegroup**.  
  
 RESTORE VERIFYONLY FROM *backup_device* avec LOADHISTORY remplit les colonnes de la **backupmediaset** table avec les valeurs appropriées de l’en-tête de support de sauvegarde.  
  
 Pour réduire le nombre de lignes dans cette table et dans d’autres tables d’historique de sauvegarde et, exécutez le [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration des Tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Tables système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
