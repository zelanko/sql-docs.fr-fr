---
title: Sys.dm_resource_governor_resource_pool_volumes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_volumes_TSQL
- dm_resource_governor_resource_pool_volumes_TSQL
- dm_resource_governor_resource_pool_volumes
- sys.dm_resource_governor_resource_pool_volumes
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_volumes
- sys.dm_resource_governor_resource_pool_volumes
ms.assetid: fa692e56-c561-4533-97c5-bc12c600553f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9ab74e76db2820d5a0242e386aa70130597e7e9f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718537"
---
# <a name="sysdmresourcegovernorresourcepoolvolumes-transact-sql"></a>Sys.dm_resource_governor_resource_pool_volumes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur les statistiques d'E/S du pool de ressources actuel pour chaque volume de disque. Ces informations sont également disponibles au niveau du pool de ressources dans [sys.dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).  
  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|pool_id|**Int**|ID du pool de ressources. N'accepte pas la valeur NULL.|  
|volume_name|**sysname**|Nom du volume de disque. N'accepte pas la valeur NULL.|  
|read_io_queued_total|**Int**|Total IOs en file d’attente de lecture dans la mesure où le gouverneur de ressources est réinitialisé. N'accepte pas la valeur NULL.|  
|read_io_issued_total|**Int**|Total d'entrées/sorties de lecture émises depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL.|  
|read_ios_completed_total|**Int**|Total d'entrées/sorties de lecture terminées depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL.|  
|read_ios_throttled_total|**Int**|Total d'entrées/sorties de lecture limitées depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL.|  
|read_bytes_total|**bigint**|Nombre total d'octets lus depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL.|  
|read_io_stall_total_ms|**bigint**|Durée totale (en millisecondes) entre l'arrivée des E/S de lecture et la fin de l'opération. N'accepte pas la valeur NULL.|  
|read_io_stall_queued_ms|**bigint**|Durée totale (en millisecondes) entre l'arrivée des E/S de lecture et leur émission. Latence introduite par la gouvernance des ressources d'E/S. N'accepte pas la valeur NULL.|  
|write_io_queued_total|**Int**|Total des entrées/sorties d'écriture empilées depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL.|  
|write_io_issued_total|**Int**|Total des entrées/sorties d'écriture émises depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL.|  
|write_io_completed_total|**Int**|Total des entrées/sorties d'écriture terminées depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL|  
|write_io_throttled_total|**Int**|Total des entrées/sorties d'écriture limitées depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL|  
|write_bytes_total|**bigint**|Nombre total d'octets écrits depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL.|  
|write_io_stall_total_ms|**bigint**|Durée totale (en millisecondes) entre l'émission des E/S d'écriture et la fin de l'opération. N'accepte pas la valeur NULL.|  
|write_io_stall_queued_ms|**bigint**|Durée totale (en millisecondes) entre l'arrivée des E/S d'écriture et leur émission. Latence introduite par la gouvernance des ressources d'E/S. N'accepte pas la valeur NULL.|  
|io_issue_violations_total|**Int**|Total des violations d'émission d'E/S. Autrement dit, le nombre de fois où la fréquence d'émission d'E/S était inférieure à la fréquence réservée. N'accepte pas la valeur NULL.|  
|io_issue_delay_total_ms|**bigint**|Durée totale (en millisecondes) entre l'émission planifiée et l'émission réelle des E/S. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation VIEW SERVER STATE.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [sys.resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

