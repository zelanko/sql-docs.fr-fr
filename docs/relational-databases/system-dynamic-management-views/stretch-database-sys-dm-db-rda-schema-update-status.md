---
title: sys.dm_db_rda_schema_update_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_schema_update_status
- sys.dm_db_rda_schema_update_status_TSQL
- dm_db_rda_schema_update_status
- dm_db_rda_schema_update_status_TSQL
helpviewer_keywords:
- sys.dm_db_rda_schema_update_status dynamic management view
ms.assetid: 364e3caa-a7c6-4be5-a029-0b19da34de3e
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 611fe9d5bea47204b655f2defe5072d2dd17be92
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937016"
---
# <a name="stretch-database---sysdmdbrdaschemaupdatestatus"></a>Stretch Database - sys.dm_db_rda_schema_update_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque tâche de mise à jour de schéma pour l’archive de données distante de chaque table compatible Stretch dans la base de données actuelle. Les tâches sont identifiés par leur ID de tâche.  
  
 **dm_db_rda_schema_update_status** porte sur le contexte actuel de la base de données. Vérifiez que vous êtes dans le contexte de base de données de la table compatible Stretch pour lequel vous souhaitez voir l’état de mise à jour de schéma.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**Int**|L’ID de la table compatible Stretch locale dont les données à distance archiver le schéma est en cours de mise à jour.|  
|**database_id**|**int**|ID de la base de données qui contient la table compatible Stretch locale.|  
|**task_id**|**bigint**|ID de la tâche de mise à jour de schéma archive des données à distance.|  
|**task_type**|**Int**|Le type de la tâche de mise à jour de schéma archive des données à distance.|  
|**task_type_desc**|**nvarchar**|La description du type de la tâche de mise à jour de schéma archive des données à distance.|  
|**task_state**|**Int**|L’état de la tâche de mise à jour de schéma archive des données à distance.|  
|**task_state_des**|**nvarchar**|La description de l’état de la tâche de mise à jour de schéma archive des données à distance.|  
|**start_time_utc**|**datetime**|L’heure UTC à laquelle les données distantes archiver mise à jour de schéma démarré.|  
|**end_time_utc**|**datetime**|L’heure UTC à laquelle les données distantes archiver mise à jour de schéma terminée.|  
|**error_number**|**int**|Si la mise à jour du schéma d’archive des données à distance échoue, le numéro d’erreur de l’erreur qui s’est produite ; Sinon, null.|  
|**error_severity**|**int**|Si la mise à jour du schéma d’archive des données à distance échoue, la gravité de l’erreur qui s’est produite ; Sinon, null.|  
|**error_state**|**int**|Si la mise à jour du schéma d’archive des données à distance échoue, l’état de l’erreur qui s’est produite ; Sinon, null. L’error_state indique la condition ou l’emplacement où l’erreur s’est produite.|  
  
## <a name="see-also"></a>Voir aussi  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
