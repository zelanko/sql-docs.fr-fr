---
title: Sys.fn_db_backup_file_snapshots (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/03/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 45010ff2-219f-4086-9ea4-016a6c17cddd
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 30988d44e03a40ffcb8317a603b99633c21c8068
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="sysfndbbackupfilesnapshots-transact-sql"></a>Sys.fn_db_backup_file_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Retourne des instantanés Azure associés aux fichiers de base de données. Si la base de données spécifiée est introuvable ou si les fichiers de base de données ne sont pas stockés dans le service de stockage d’objets Blob Microsoft Azure, ne retourne aucune ligne. Utilisez cette fonction système conjointement avec la **sys.sp_delete_backup_file_snapshot** procédures stockées système pour identifier et supprimer des instantanés de sauvegarde orphelins. Pour plus d’informations, consultez [Sauvegarde d’instantanés de fichiers pour les fichiers de base de données dans Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_db_backup_file_snapshots   
   [ ( database_name ) ]  
```  
  
## <a name="arguments"></a>Arguments  
 *Nom_base_de_données*  
 Le nom de la base de données qui est interrogée. Si NULL, cette fonction est exécutée dans l’étendue actuelle de la base de données.  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|file_id|**int**|ID de fichier pour la base de données. N'accepte pas la valeur NULL.|  
|snapshot_time|**nvarchar (260)**|L’horodatage de l’instantané telle qu’elle est retournée par l’API REST. Retourne NULL si aucun instantané n’existe.|  
|snapshot_url|**nvarchar(360)**|L’URL complète vers l’instantané de fichier. Retourne NULL si aucun instantané n’existe pas.|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation VIEW DATABASE STATE sur la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_delete_backup_file_snapshot &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
