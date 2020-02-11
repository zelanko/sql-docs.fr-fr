---
title: sys. dm_db_rda_migration_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_migration_status
- sys.dm_db_rda_migration_status_TSQL
- dm_db_rda_migration_status
- dm_db_rda_migration_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_rda_migration_status dynamic management view
ms.assetid: faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 21e5230e4f3efd86fe90382202f0b21a0187a214
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937061"
---
# <a name="stretch-database---sysdm_db_rda_migration_status"></a>Stretch Database-sys. dm_db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque lot de données migrées à partir de chaque table prenant en charge Stretch sur l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]instance locale de. Les lots sont identifiés par l’heure de début et l’heure de fin.  
  
 **sys. dm_db_rda_migration_status** est limité au contexte de la base de données actuelle. Assurez-vous que vous êtes dans le contexte de la base de données des tables d’activation Stretch pour lesquelles vous souhaitez afficher l’état de la migration.  
  
 Dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], la sortie de **sys. dm_db_rda_migration_status** est limitée à 200 lignes.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|ID de la table à partir de laquelle les lignes ont été migrées.|  
|**database_id**|**int**|ID de la base de données à partir de laquelle les lignes ont été migrées.|  
|**migrated_rows**|**bigint**|Nombre de lignes migrées dans ce lot.|  
|**start_time_utc**|**DATETIME**|Heure UTC à laquelle le lot a démarré.|  
|**end_time_utc**|**DATETIME**|Heure UTC à laquelle le lot s’est terminé.|  
|**error_number**|**int**|Si le lot échoue, numéro d’erreur de l’erreur qui s’est produite ; Sinon, null.|  
|**error_severity**|**int**|Si le lot échoue, gravité de l’erreur qui s’est produite ; Sinon, null.|  
|**error_state**|**int**|Si le lot échoue, état de l’erreur qui s’est produite ; Sinon, null.<br /><br /> Le **ERROR_STATE** indique la condition ou l’emplacement où l’erreur s’est produite.|  
  
## <a name="see-also"></a>Voir aussi  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
