---
title: Sys.dm_db_rda_migration_status (Transact-SQL) | Microsoft Docs
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3027978ca57b5ea94c69dc2410b0d25d73ce3823
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740977"
---
# <a name="stretch-database---sysdmdbrdamigrationstatus"></a>Stretch Database - sys.dm_db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque lot de données migrées à partir de chaque table compatible Stretch sur l’instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les lots sont identifiés par leur heure de début et l’heure de fin.  
  
 **Sys.dm_db_rda_migration_status** porte sur le contexte actuel de la base de données. Vérifiez que vous êtes dans le contexte de base de données des tables d’activer Stretch pour lequel vous souhaitez voir l’état de la migration.  
  
 Dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], la sortie de **sys.dm_db_rda_migration_status** est limité à 200 lignes.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**Int**|L’ID de la table à partir de laquelle les lignes ont été migrés.|  
|**database_id**|**Int**|ID de la base de données à partir de laquelle les lignes ont été migrés.|  
|**migrated_rows**|**bigint**|Le nombre de lignes migrées dans ce lot.|  
|**start_time_utc**|**datetime**|L’heure UTC à laquelle le lot a démarré.|  
|**end_time_utc**|**datetime**|L’heure UTC à laquelle le lot terminé.|  
|**error_number**|**Int**|Si le lot échoue, le numéro d’erreur de l’erreur qui s’est produite ; Sinon, null.|  
|**error_severity**|**Int**|Si le lot échoue, la gravité de l’erreur qui s’est produite ; Sinon, null.|  
|**error_state**|**Int**|Si le lot échoue, l’état de l’erreur qui s’est produite ; Sinon, null.<br /><br /> Le **error_state** indique la condition ou l’emplacement où l’erreur s’est produite.|  
  
## <a name="see-also"></a>Voir aussi  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
