---
title: Sys.fn_db_backup_file_snapshots (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 45010ff2-219f-4086-9ea4-016a6c17cddd
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7845ef36347d9131ed6991674b4e09b23ee34155
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670429"
---
# <a name="sysfndbbackupfilesnapshots-transact-sql"></a>Sys.fn_db_backup_file_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Retourne des instantanés Azure associées avec les fichiers de base de données. Si la base de données spécifié est introuvable ou si les fichiers de base de données ne sont pas stockés dans le service de stockage d’objets Blob Microsoft Azure, ne retourne aucune ligne. Utilisez cette fonction système conjointement avec le **sys.sp_delete_backup_file_snapshot** procédures stockées système pour identifier et supprimer des instantanés de sauvegarde orphelins. Pour plus d’informations, consultez [Sauvegarde d’instantanés de fichiers pour les fichiers de base de données dans Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_db_backup_file_snapshots   
   [ ( database_name ) ]  
```  
  
## <a name="arguments"></a>Arguments  
 *Nom_base_de_données*  
 Le nom de la base de données en cours d’interrogation. Si NULL, cette fonction est exécutée dans l’étendue actuelle de la base de données.  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|file_id|**Int**|ID du fichier pour la base de données. N'accepte pas la valeur NULL.|  
|snapshot_time|**nvarchar(260)**|L’horodatage de l’instantané tel qu’il est retourné par l’API REST. Retourne NULL si aucun instantané n’existe.|  
|snapshot_url|**nvarchar(360)**|L’URL complète vers l’instantané de fichier. Retourne NULL si aucun instantané n’existe.|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation VIEW DATABASE STATE sur la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_delete_backup_file_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
