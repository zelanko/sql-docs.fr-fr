---
title: Sys.dm_db_rda_schema_update_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_schema_update_status
- sys.dm_db_rda_schema_update_status_TSQL
- dm_db_rda_schema_update_status
- dm_db_rda_schema_update_status_TSQL
helpviewer_keywords:
- sys.dm_db_rda_schema_update_status dynamic management view
ms.assetid: 364e3caa-a7c6-4be5-a029-0b19da34de3e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cbd99f97902dbbd3c097b76b1f119f400f97c6f6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420058"
---
# <a name="stretch-database---sysdmdbrdaschemaupdatestatus"></a>Stretch Database - sys.dm_db_rda_schema_update_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque tâche de mise à jour de schéma pour l’archive de données distante de chaque table compatible Stretch dans la base de données actuelle. Les tâches sont identifiés par leur ID de tâche.  
  
 **dm_db_rda_schema_update_status** porte sur le contexte actuel de la base de données. Vérifiez que vous êtes dans le contexte de base de données de la table compatible Stretch pour lequel vous souhaitez voir l’état de mise à jour de schéma.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**Int**|L’ID de la table compatible Stretch locale dont les données à distance archiver le schéma est en cours de mise à jour.|  
|**database_id**|**Int**|ID de la base de données qui contient la table compatible Stretch locale.|  
|**id_tâche**|**bigint**|ID de la tâche de mise à jour de schéma archive des données à distance.|  
|**task_type**|**Int**|Le type de la tâche de mise à jour de schéma archive des données à distance.|  
|**task_type_desc**|**nvarchar**|La description du type de la tâche de mise à jour de schéma archive des données à distance.|  
|**task_state**|**Int**|L’état de la tâche de mise à jour de schéma archive des données à distance.|  
|**task_state_des**|**nvarchar**|La description de l’état de la tâche de mise à jour de schéma archive des données à distance.|  
|**start_time_utc**|**datetime**|L’heure UTC à laquelle les données distantes archiver mise à jour de schéma démarré.|  
|**end_time_utc**|**datetime**|L’heure UTC à laquelle les données distantes archiver mise à jour de schéma terminée.|  
|**error_number**|**Int**|Si la mise à jour du schéma d’archive des données à distance échoue, le numéro d’erreur de l’erreur qui s’est produite ; Sinon, null.|  
|**error_severity**|**Int**|Si la mise à jour du schéma d’archive des données à distance échoue, la gravité de l’erreur qui s’est produite ; Sinon, null.|  
|**error_state**|**Int**|Si la mise à jour du schéma d’archive des données à distance échoue, l’état de l’erreur qui s’est produite ; Sinon, null. L’error_state indique la condition ou l’emplacement où l’erreur s’est produite.|  
  
## <a name="see-also"></a>Voir aussi  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
