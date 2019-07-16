---
title: Sys.dm_exec_distributed_request_steps (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_distributed_request_steps
- sys.dm_exec_distributed_request_steps management view
ms.assetid: 1954541d-b716-4e03-8fcc-7022f428e01d
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b5c40ce6d1c7b7ef85f24fc8032559e000d89be1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097820"
---
# <a name="sysdmexecdistributedrequeststeps-transact-sql"></a>Sys.dm_exec_distributed_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les étapes qui composent une requête PolyBase donnée ou une requête. Elle répertorie une ligne par étape de la requête.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**int**|execution_id et step_index composent la clé pour cette vue. Id numérique unique associé à la demande.|Consultez les ID dans [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|La position de cette étape dans la séquence d’étapes qui composent la demande.|0 pour (n-1) pour une demande avec n étapes.|  
|operation_type|**nvarchar(128)**|Type de l’opération représentée par cette étape.|'MoveOperation', 'OnOperation', 'RandomIDOperation', 'RemoteOperation', 'ReturnOperation', 'ShuffleMoveOperation', 'TempTablePropertiesOperation', 'DropDiagnosticsNotifyOperation', 'HadoopShuffleOperation', 'HadoopBroadCastOperation', 'HadoopRoundRobinOperation'|  
|distribution_type|**nvarchar(32)**|Où l’étape s’exécute.|« AllComputeNodes «, » AllDistributions', « ComputeNode », « Distribution », « AllNodes », « SubsetNodes », « 'SubsetDistributions, » n’est pas spécifié ».|  
|location_type|**nvarchar(32)**|Où l’étape s’exécute.|« Compute', 'Head' ou « DMS ». Toutes les étapes de déplacement des données affichent « DMS ».|  
|status|**nvarchar(32)**|État de cette étape|'Pending', 'Running', 'Complete', 'Failed', 'UndoFailed', 'PendingCancel', 'Cancelled', 'Undone', 'Aborted'|  
|error_id|**nvarchar(36)**|Id unique de l’erreur associée à cette étape, le cas échéant|Consultez l’id de [sys.dm_exec_compute_node_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), NULL si aucune erreur ne s’est produite.|  
|start_time|**datetime**|Heure de début de l’étape d’exécution|Plus petit ou égal à l’heure actuelle et supérieur ou égal à end_compile_time de la requête à laquelle appartient cette étape.|  
|end_time|**datetime**|Heure à laquelle cette étape exécutée avec succès, a été annulée ou a échoué.|Plus petit ou égal à l’heure actuelle et supérieur ou égal à heure_début, la valeur NULL pour les étapes d’exécution ou en file d’attente.|  
|total_elapsed_time|**int**|Quantité totale de temps à qu'exécuter l’étape de requête, en millisecondes|Comprise entre 0 et la différence entre end_time et start_time. 0 pour les étapes en attente.|  
|row_count|**bigint**|Nombre total de lignes modifiées ou retourné par cette demande|0 pour les étapes qui ne pas de modification ou de retourner des données, le nombre de lignes affectées dans le cas contraire. La valeur -1 pour obtenir des instructions DMS.|  
|command|nvarchar(4000)|Contient le texte complet de la commande de cette étape.|Toute chaîne de requête valide pour une étape. Tronquée à 4 000 caractères.|  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes avec les vues de gestion dynamique de PolyBase](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à la base de données &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
