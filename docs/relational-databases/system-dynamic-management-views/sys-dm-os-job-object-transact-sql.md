---
title: Sys.dm_os_job_object (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 04/17/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 673f1bffeea908da211cd5ff76bad9d96dabcded
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396309"
---
# <a name="sysdmosjobobject-azure-sql-database"></a>Sys.dm_os_job_object (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Retourne une ligne unique décrivant la configuration de l’objet de travail qui gère le processus SQL Server, ainsi que certaines statistiques de consommation de ressources au niveau de l’objet de travail. Retourne un jeu vide si SQL Server n’est pas en cours d’exécution dans un objet de tâche. 

Un objet de tâche est une construction de Windows qui implémente la gouvernance des ressources processeur, mémoire et d’e/s au niveau du système d’exploitation. Pour plus d’informations sur les objets de travail, consultez [objets travail](/windows/desktop/ProcThread/job-objects). 
  
|Colonnes|Type de données|Description|  
|-------------|---------------|-----------------|  
|cpu_rate|**Int**|Spécifie la partie de cycles de processeur que les threads SQL Server peuvent utiliser pendant chaque intervalle de planification. La valeur est indiquée sous forme de pourcentage de cycles disponibles dans un intervalle de planification du cycle de 10000. Par exemple, la valeur 100 signifie que les threads peuvent utiliser des cœurs de processeur est à leur capacité maximale.|
|cpu_affinity_mask|**bigint**|Un masque de bits qui décrit les processeurs logiques du processus SQL Server peut utiliser au sein du groupe de processeur. Par exemple, cpu_affinity_mask 255 (1111 1111 en binaire) signifie que les huit premiers processeurs logiques peuvent être utilisés.|
|cpu_affinity_group|**Int**|Le numéro du groupe de processeur qui est utilisé par SQL Server.|
|memory_limit_mb|**bigint**|La quantité maximale de mémoire allouée, en Mo, que tous les processus de l’objet de travail, y compris SQL Server, permettent de manière cumulative.| 
|process_memory_limit_mb |**bigint**|La quantité maximale de mémoire allouée, en Mo, qu’un seul processus de l’objet de travail, telles que SQL Server, peut utiliser.|
|workingset_limit_mb |**bigint**|La quantité maximale de mémoire, en Mo, qui permet de la plage de travail de SQL Server.|
|non_sos_mem_gap_mb|**bigint**|La quantité de mémoire, en Mo, réserver pour les piles de threads, des DLL et des autres allocations de mémoire non SOS. Mémoire cible de SOS est la différence entre `process_memory_limit_mb` et `non_sos_mem_gap_mb`.| 
|low_mem_signal_threshold_mb|**bigint**|Un seuil de mémoire, en Mo. Lorsque la quantité de mémoire disponible pour l’objet de traitement est inférieure à ce seuil, un signal de notification de mémoire insuffisante est envoyé au processus SQL Server. |
|total_user_time|**bigint**|Le nombre total de graduations ns 100 threads au sein de l’objet de traitement ayant passé en mode utilisateur, étant donné que l’objet de traitement a été créé. |
|total_kernel_time |**bigint**|Le nombre total de graduations ns 100 threads au sein de l’objet de traitement ayant passé en mode noyau, étant donné que l’objet de traitement a été créé. |
|write_operation_count |**bigint**|Le nombre total d’opérations d’écriture d’e/s sur les disques locaux émis par SQL Server dans la mesure où l’objet de traitement a été créé. |
|read_operation_count |**bigint**|Le nombre total d’e/s des opérations de lecture sur les disques locaux émis par SQL Server dans la mesure où l’objet de traitement a été créé. |
|peak_process_memory_used_mb|**bigint**|La quantité maximale de mémoire, en Mo, ce qui a un seul processus de l’objet de travail, telles que SQL Server, a utilisé dans la mesure où l’objet de traitement a été créé.| 
|peak_job_memory_used_mb|**bigint**|La quantité maximale de mémoire, en Mo, que tous les processus dans l’objet de traitement ont utilisé cumulativement étant donné que l’objet de travail a été créée.|
  
## <a name="permissions"></a>Permissions  
Sur SQL Database Managed Instance nécessite `VIEW SERVER STATE` autorisation. Sur la base de données SQL, nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.  
 
## <a name="see-also"></a>Voir aussi  

Pour plus d’informations sur les Instances gérées, consultez [SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
