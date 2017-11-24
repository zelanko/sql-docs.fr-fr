---
title: sp_delete_backup_file_snapshot (Transact-SQL) | Documents Microsoft
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 5afe5530-a404-4fa5-af3c-bc7c3ca43ce6
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4cf8bf8484e77c15c951ca548ce00baccfaf5b38
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="snapshot-backup---spdeletebackupfilesnapshot"></a>Sauvegarde d’instantanés - sp_delete_backup_file_snapshot
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Supprime un instantané de sauvegarde spécifié à partir de la base de données spécifié. Utilisez cette procédure stockée système conjointement avec la **sys.fn_db_backup_file_snapshots** fonction système pour identifier et supprimer des orphelins des instantanés de sauvegarde. Pour plus d’informations, consultez [Sauvegarde d’instantanés de fichiers pour les fichiers de base de données dans Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  

  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.sp_delete_backup_file_snapshot  
    [ @db_name = ] N’<database_name>  
    , [ @snapshot_url = ] N’<snapshot_url>  
```  
  
## <a name="arguments"></a>Arguments  
 *[ @db_name =] nom_base_de_données*  
 Le nom de la base de données contenant l’instantané doit être supprimé, fournie sous forme de chaîne Unicode.  
  
 *[ @snapshot_url =] snapshot_url*  
 L’URL de l’instantané doit être supprimé, fournie sous forme de chaîne Unicode.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’autorisation ALTER ANY DATABASE.  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.fn_db_backup_file_snapshots &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
