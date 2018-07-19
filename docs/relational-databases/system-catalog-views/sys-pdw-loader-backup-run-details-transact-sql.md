---
title: Sys.pdw_loader_backup_run_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
caps.latest.revision: 9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d749acc32be0f871a670dff0284b719d1350c1c9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38047287"
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>Sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient davantage d’informations détaillées, au-delà des informations dans [sys.pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), sur la sauvegarde en cours et terminée et les opérations de restauration dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et sur en cours et effectué des opérations de sauvegarde, restauration et charge dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Ces informations sont conservées après le redémarrage du système.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**Int**|Identificateur unique pour une sauvegarde spécifique ou de rétablissement de l’exécution.<br /><br /> run_id et pdw_node_id forment la clé pour cette vue.||  
|pdw_node_id|**Int**|Identificateur unique d’un nœud d’appliance pour laquelle cet enregistrement conserve les détails.<br /><br /> run_id et pdw_node_id forment la clé pour cette vue.|Consultez node_id dans [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16)**|L’état actuel de l’exécution.|« ANNULÉ », « TERMINÉE », « ÉCHEC », « QUEUED », « RUNNING »|  
|start_time|**datetime**|Heure de début de l’opération sur ce nœud particulier.||  
|end_time|**datetime**|Heure à laquelle l’opération s’est terminée sur ce nœud particulier, le cas échéant.||  
|total_elapsed_time|**Int**|Durée totale de l’opération a été en cours d’exécution sur ce nœud particulier.|Si total_elapsed_time dépasse la valeur maximale d’un entier (24,8 jours en millisecondes), cela entraînera l’échec de matérialisation en raison d’un dépassement de capacité.<br /><br /> La valeur maximale en millisecondes est équivalente à 24,8 jours environ.|  
|progression|**Int**|Progression de l’opération exprimée en pourcentage.|0 à 100.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
