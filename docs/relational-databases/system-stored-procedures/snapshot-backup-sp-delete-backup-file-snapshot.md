---
description: sp_delete_backup_file_snapshot (Transact-SQL)
title: sp_delete_backup_file_snapshot (Transact-SQL) | Microsoft Docs
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.custom: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5afe5530-a404-4fa5-af3c-bc7c3ca43ce6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a9689e6f739173f3e6b0f69a8e5d648c1faeac3e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469781"
---
# <a name="sp_delete_backup_file_snapshot-transact-sql"></a>sp_delete_backup_file_snapshot (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Supprime un instantané de sauvegarde spécifié de la base de données spécifiée. Utilisez cette procédure stockée système conjointement avec la fonction système **sys. fn_db_backup_file_snapshots** pour identifier et supprimer les instantanés de sauvegarde orphelins. Pour plus d’informations, consultez [Sauvegarde d’instantanés de fichiers pour les fichiers de base de données dans Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  

  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.sp_delete_backup_file_snapshot  
    [ @db_name = ] N'<database_name>  
    , [ @snapshot_url = ] N'<snapshot_url>  
```  
  
## <a name="arguments"></a>Arguments  
 *[ @db_name =] database_name*  
 Nom de la base de données contenant l’instantané à supprimer, fourni en tant que chaîne Unicode.  
  
 *[ @snapshot_url =] snapshot_url*  
 URL de l’instantané à supprimer, fournie sous forme de chaîne Unicode.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation ALTER ANY DATABASE.  
  
## <a name="see-also"></a>Voir aussi  
 [sys. fn_db_backup_file_snapshots &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
