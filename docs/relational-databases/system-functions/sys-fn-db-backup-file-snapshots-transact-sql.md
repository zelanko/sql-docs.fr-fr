---
description: sys. fn_db_backup_file_snapshots (Transact-SQL)
title: sys. fn_db_backup_file_snapshots (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: 067a1d65b65c1e2cc9bde252e6f56951e87950a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427791"
---
# <a name="sysfn_db_backup_file_snapshots-transact-sql"></a>sys. fn_db_backup_file_snapshots (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Retourne les instantanés Azure associés aux fichiers de base de données. Si la base de données spécifiée est introuvable ou si les fichiers de base de données ne sont pas stockés dans le service de stockage d’objets BLOB Microsoft Azure, aucune ligne n’est retournée. Utilisez cette fonction système conjointement avec la procédure stockée système **sys. sp_delete_backup_file_snapshot** pour identifier et supprimer les instantanés de sauvegarde orphelins. Pour plus d’informations, consultez [Sauvegarde d’instantanés de fichiers pour les fichiers de base de données dans Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_db_backup_file_snapshots   
   [ ( database_name ) ]  
```  
  
## <a name="arguments"></a>Arguments  
 *Database_name*  
 Nom de la base de données interrogée. Si la valeur est NULL, cette fonction est exécutée dans l’étendue de la base de données actuelle.  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|file_id|**int**|ID de fichier de la base de données. N'accepte pas la valeur NULL.|  
|snapshot_time|**nvarchar(260)**|Horodateur de l’instantané tel qu’il est retourné par l’API REST. Retourne la valeur NULL si aucun instantané n’existe.|  
|snapshot_url|**nvarchar(360)**|URL complète de l’instantané de fichier. Retourne la valeur NULL si aucun instantané n’existe.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation VIEW DATABASE STATE sur la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_delete_backup_file_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
