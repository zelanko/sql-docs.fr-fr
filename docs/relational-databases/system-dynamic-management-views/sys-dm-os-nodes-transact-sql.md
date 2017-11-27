---
title: Sys.dm_os_nodes (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_nodes
- dm_os_nodes_TSQL
- dm_os_nodes
- sys.dm_os_nodes_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_nodes dynamic management view
ms.assetid: c768b67c-82a4-47f5-850b-0ea282358d50
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5cf36f7156f9297231fc232e8fecafee5e77427c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosnodes-transact-sql"></a>sys.dm_os_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Un composant interne nommé SQLOS crée des structures de nœuds qui simulent la localité du processeur du matériel. Ces structures peuvent être modifiées en utilisant soft-NUMA pour créer des dispositions de nœuds personnalisées.  
  
 Le tableau suivant fournit des informations sur ces nœuds.  
  
> **Remarque :** pour appeler cette DMV à partir de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_nodes**.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|node_id|**smallint**|Identificateur du nœud.|  
|node_state_desc|**nvarchar (256)**|Description de l'état du nœud. Les valeurs sont affichées avec, en premier, les valeurs qui s'excluent mutuellement, suivies par les valeurs pouvant être associées. Exemple :<br /><br /> En ligne, Ressources de thread réduites, Préemptif différé<br /><br /> Il existe quatre valeurs node_state_desc qui s’excluent mutuellement. Ils sont répertoriés ci-dessous avec leurs descriptions.<br /><br /> En ligne : Le nœud est en ligne<br /><br /> En mode hors connexion : Nœud est hors connexion<br /><br /> INACTIF : Nœud n’a aucune demande en attente de travail et a entré un état inactif.<br /><br /> IDLE_READY : Nœud n’a pas de demandes de travail en attente et est prêt à entrer dans un état inactif.<br /><br /> Il existe cinq valeurs node_state_desc pouvant être associées, répertoriées ci-dessous, avec leurs descriptions.<br /><br /> DAC : Ce nœud est réservé à la connexion d’administration dédiée.<br /><br /> THREAD_RESOURCES_LOW : Aucun nouveau thread ne peut être créés sur ce nœud en raison d’une condition de mémoire insuffisante.<br /><br /> AJOUT à chaud : Indique les nœuds ont été ajoutés en réponse à un accès rapide Ajouter des événements de l’UC.|  
|memory_object_address|**varbinary (8)**|Adresse de l'objet mémoire associé à ce nœud. Relation un-à-un à sys.dm_os_memory_objects.memory_object_address.|  
|memory_clerk_address|**varbinary (8)**|Adresse du régisseur de mémoire associé à ce nœud. Relation un-à-un à sys.dm_os_memory_clerks.memory_clerk_address.|  
|io_completion_worker_address|**varbinary (8)**|Adresse du thread de travail assigné à l'achèvement d'E/S pour ce nœud. Relation un-à-un à sys.dm_os_workers.worker_address.|  
|memory_node_id|**smallint**|ID du nœud de mémoire auquel ce nœud appartient. Relation plusieurs-à-un à sys.dm_os_memory_nodes.memory_node_id.|  
|cpu_affinity_mask|**bigint**|Bitmap qui identifie les unités centrales auxquelles ce nœud est associé.|  
|online_scheduler_count|**smallint**|Nombre de planificateurs en ligne qui sont gérés par ce nœud.|  
|idle_scheduler_count|**smallint**|Nombre de planificateurs en ligne qui n'ont aucun thread de travail actif.|  
|active_worker_count|**int**|Nombre de threads de travail qui sont actifs sur tous les planificateurs gérés par ce nœud.|  
|avg_load_balance|**int**|Nombre moyen de tâches par planificateur sur ce nœud.|  
|timer_task_affinity_mask|**bigint**|Bitmap qui identifie les planificateurs auxquels des tâches de minuterie peuvent être assignées.|  
|permanent_task_affinity_mask|**bigint**|Bitmap qui identifie les planificateurs auxquels des tâches permanentes peuvent être assignées.|  
|resource_monitor_state|**bit**|Un moniteur de ressource est assigné à chaque nœud. Le moniteur de ressource peut être en cours d'exécution ou inactif. La valeur 1 indique qu'il est en cours d'exécution et la valeur 0 indique qu'il est inactif.|  
|online_scheduler_mask|**bigint**|Identifie le masque d'affinité de processus pour ce nœud.|  
|processor_group|**smallint**|Identifie le groupe de processeurs pour ce nœud.|  
|cpu_count |**int** |Nombre de processeurs disponibles pour ce nœud. |
|pdw_node_id|**int**|L’identificateur du nœud qui se trouve sur cette distribution.<br /><br /> **S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Permissions  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveaux Premium, nécessite le `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard et les niveaux de base, nécessite le **administrateur du serveur** ou **administrateur Active Directory de Azure** compte.  
  
## <a name="see-also"></a>Voir aussi  
  
 [Système d’exploitation de serveur SQL relatives des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [Soft-NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  


