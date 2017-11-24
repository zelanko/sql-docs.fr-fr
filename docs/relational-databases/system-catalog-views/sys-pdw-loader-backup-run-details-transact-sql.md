---
title: Sys.pdw_loader_backup_run_details (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 79e69b2a74841e790eb178aa2f8d1b693cfe7c5a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>Sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations détaillées, au-delà des informations dans d’autres [sys.pdw_loader_backup_runs &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), à propos de la sauvegarde en cours et terminée et les opérations de restauration dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et sur la sauvegarde en cours et terminée, restaurer et opérations de chargement dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Les informations sont conservées entre les redémarrages du système.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Identificateur unique pour une sauvegarde spécifique ou une restauration s’exécuter.<br /><br /> run_id et pdw_node_id forment la clé pour cette vue.||  
|pdw_node_id|**int**|Identificateur unique d’un nœud d’application pour laquelle cet enregistrement conserve les détails.<br /><br /> run_id et pdw_node_id forment la clé pour cette vue.|Consultez node_id dans [sys.dm_pdw_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16)**|L’état actuel de l’exécution.|ANNULÉ, « TERMINÉ', 'ÉCHEC', 'EN FILE D’ATTENTE', « EN COURS D’EXÉCUTION »|  
|start_time|**datetime**|Heure de début de l’opération sur ce nœud particulier.||  
|end_time|**datetime**|Heure à laquelle l’opération s’est terminée sur ce nœud particulier, le cas échéant.||  
|total_elapsed_time|**int**|Durée totale de que l’opération a été exécuté sur ce nœud particulier.|Si total_elapsed_time dépasse la valeur maximale pour un entier (24.8 jours en millisecondes), cela entraînera l’échec de matérialisation en raison d’un dépassement de capacité.<br /><br /> La valeur maximale, en millisecondes est équivalente à 24.8 jours.|  
|Progression|**int**|Progression de l’opération exprimée en pourcentage.|0 à 100.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
