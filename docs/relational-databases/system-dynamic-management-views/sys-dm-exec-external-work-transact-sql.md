---
title: Sys.dm_exec_external_work (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_EXTERNAL_WORK
- DM_EXEC_EXTERNAL_WORK_TSQL
- SYS.DM_EXEC_EXTERNAL_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_external_work management view
- dm_exec_external_work management view
- PolyBase,views
- PolyBase
ms.assetid: 7597d97b-1fde-4135-ac35-4af12968f300
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a53a32f01dcf4646ee0bc12843c188b9b0e8e4c0
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52418623"
---
# <a name="sysdmexecexternalwork-transact-sql"></a>Sys.dm_exec_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Retourne des informations sur la charge de travail par travail, sur chaque nœud de calcul.  
  
 Sys.dm_exec_external_work de requête pour identifier le travail lancé pour communiquer avec la source de données externe (par exemple, Hadoop ou externes SQL Server).  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Identificateur unique pour les requêtes PolyBase associé.|Consultez *request_ID* dans [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**Int**|La demande que l’exécution de ce processus de travail.|Consultez *step_index* dans [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|dms_step_index|**Int**|Étape dans le plan DMS ce processus de travail est en cours d’exécution.|Consultez [sys.dm_exec_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md).|  
|compute_node_id|**Int**|Le nœud le processus de travail s’exécute sur.|Consultez [sys.dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|Type|**nvarchar(60)**|Le type de travail externe.|Fichier de fractionnement|  
|work_id|**Int**|ID du fractionnement réels.|Supérieur ou égal à 0.|  
|input_name|**nvarchar(4000)**|Nom de l’entrée à lire|Nom de fichier lors de l’utilisation de Hadoop.|  
|read_location|**bigint**|Décalage ou lire l’emplacement.|Offset du fichier à lire.|  
|bytes_processed|**bigint**|Nombre total d’octets traité par ce processus de travail.|Supérieur ou égal à 0.|  
|length|**bigint**|Longueur de la division ou d’un bloc HDFS en cas de Hadoop|Définissables par l’utilisateur. La valeur par défaut est 64M|  
|status|**nvarchar(32)**|État du processus de travail|En attente, traitement, terminé, échec, abandonnée|  
|start_time|**datetime**|Début du travail||  
|end_time|**datetime**|Fin du travail||  
|total_elapsed_time|**Int**|Durée totale en millisecondes||  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes avec les vues de gestion dynamique de PolyBase](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à la base de données &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
