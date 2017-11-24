---
title: restorefilegroup (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- restorefilegroup_TSQL
- restorefilegroup
dev_langs: TSQL
helpviewer_keywords:
- filegroups [SQL Server], restorefilegroup system table
- restorefilegroup system table
ms.assetid: 3aa15c55-6b72-4f76-97d7-bd88391d105c
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5cbdf5074c50b2072ef60bdccb0541f4760bdd43
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="restorefilegroup-transact-sql"></a>restorefilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne par groupe de fichiers restaurés. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|Numéro d'identification unique de l'opération de restauration correspondante. Références **RestoreHistory (restore_history_id)**.|  
|**FILEGROUP_NAME**|**nvarchar (128)**|Nom du groupe de fichiers restaurés. Sa valeur peut être NULL.<br /><br /> Si un instantané d'une base de données est rétabli, cette valeur est renseignée de la même façon que pour une restauration complète.|  
  
## <a name="remarks"></a>Notes  
 Pour réduire le nombre de lignes dans cette table et dans d’autres tables d’historique de sauvegarde et, exécutez le [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration Tables &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefile &#40; Transact-SQL &#41;](../../relational-databases/system-tables/restorefile-transact-sql.md)   
 [restorehistory &#40; Transact-SQL &#41;](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [Tables système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
