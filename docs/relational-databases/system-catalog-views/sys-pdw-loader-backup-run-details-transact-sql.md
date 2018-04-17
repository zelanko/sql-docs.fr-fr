---
title: Sys.pdw_loader_backup_run_details (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 54c5df319bf2b9c019a3eac05cdd9a2a206b7517
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>Sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations détaillées, au-delà des informations dans d’autres [sys.pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), à propos de la sauvegarde en cours et terminée et les opérations de restauration dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et en cours et effectué la sauvegarde, restauration et les opérations de chargement dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Ces informations sont conservées après le redémarrage du système.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Identificateur unique pour une sauvegarde spécifique ou une restauration s’exécuter.<br /><br /> run_id et pdw_node_id forment la clé pour cette vue.||  
|pdw_node_id|**int**|Identificateur unique d’un nœud d’application pour laquelle cet enregistrement conserve les détails.<br /><br /> run_id et pdw_node_id forment la clé pour cette vue.|Consultez node_id dans [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16)**|L’état actuel de l’exécution.|ANNULÉ, « TERMINÉ', 'ÉCHEC', 'EN FILE D’ATTENTE', « EN COURS D’EXÉCUTION »|  
|start_time|**datetime**|Heure de début de l’opération sur ce nœud particulier.||  
|end_time|**datetime**|Heure à laquelle l’opération s’est terminée sur ce nœud particulier, le cas échéant.||  
|total_elapsed_time|**int**|Durée totale de que l’opération a été exécuté sur ce nœud particulier.|Si total_elapsed_time dépasse la valeur maximale pour un entier (24.8 jours en millisecondes), cela entraînera l’échec de matérialisation en raison d’un dépassement de capacité.<br /><br /> La valeur maximale, en millisecondes est équivalente à 24.8 jours.|  
|Progression|**int**|Progression de l’opération exprimée en pourcentage.|0 à 100.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
