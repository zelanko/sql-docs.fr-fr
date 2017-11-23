---
title: Sys.dm_os_memory_nodes (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/13/2017
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
- dm_os_memory_nodes_TSQL
- sys.dm_os_memory_nodes
- sys.dm_os_memory_nodes_TSQL
- dm_os_memory_nodes
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_memory_nodes dynamic management view
ms.assetid: bf4032fe-7db1-40e9-a62e-d69cebff4b44
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5284229fd7c102ceb23e8123cd355b8be29190f0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosmemorynodes-transact-sql"></a>sys.dm_os_memory_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Les allocations qui sont internes à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent le gestionnaire de mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La différence entre les compteurs de mémoire de processus à partir de suivi **sys.dm_os_process_memory** et compteurs internes peuvent indiquer l’utilisation de la mémoire à partir des composants externes dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] espace mémoire.  
  
 Les nœuds sont créés en fonction des nœuds de mémoire NUMA physiques. Ils peuvent être différents à partir des nœuds de l’UC dans **sys.dm_os_nodes**.  
  
 Aucune allocation effectuée directement par le biais de routines d'allocations de mémoire Windows ne fait l'objet d'un suivi. Le tableau suivant fournit des informations sur les allocations de mémoire effectuées uniquement en utilisant des interfaces du gestionnaire de mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Pour appeler cette de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_memory_nodes**.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**memory_node_id**|**smallint**|Spécifie l'identificateur du nœud de mémoire. Aux **memory_node_id** de **sys.dm_os_memory_clerks**. N'accepte pas la valeur NULL.|  
|**virtual_address_space_reserved_kb**|**bigint**|Indique le nombre de réservations d'adresses virtuelles, en kilo-octets (Ko), qui ne sont ni validées ni mappées à des pages physiques. N'accepte pas la valeur NULL.|  
|**virtual_address_space_committed_kb**|**bigint**|Spécifie la quantité d'adresse virtuelle, en Ko, qui a été validée ou mappée à des pages physiques. N'accepte pas la valeur NULL.|  
|**locked_page_allocations_kb**|**bigint**|Spécifie la quantité de mémoire physique, en Ko, qui a été verrouillée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. N'accepte pas la valeur NULL.|  
|**single_pages_kb**|**bigint**|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantité de mémoire allouée, en Ko, en utilisant l'allocateur de page unique par les threads en cours d'exécution sur ce nœud. Cette mémoire est allouée à partir du pool de mémoires tampons. Cette valeur indique le nœud où la demande d'allocation s'est produite, et non l'emplacement physique où la demande d'allocation a été satisfaite.|  
|**pages_kb**|**bigint**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Spécifie la quantité de mémoire validée, en Ko, allouée de ce nœud NUMA par l'allocateur de pages du gestionnaire de mémoire. N'accepte pas la valeur NULL.|  
|**multi_pages_kb**|**bigint**|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantité de mémoire allouée, en Ko, en utilisant l'allocateur de plusieurs pages par les threads en cours d'exécution sur ce nœud. Cette mémoire provient de l'extérieur du pool de mémoires tampons. Cette valeur indique le nœud où les demandes d'allocations se sont produites, et non l'emplacement physique où la demande d'allocation a été satisfaite.|  
|**shared_memory_reserved_kb**|**bigint**|Spécifie la quantité de mémoire partagée, en Ko, qui a été réservée à partir de ce nœud. N'accepte pas la valeur NULL.|  
|**shared_memory_committed_kb**|**bigint**|Spécifie la quantité de mémoire partagée, en Ko, qui a été validée sur ce nœud. N'accepte pas la valeur NULL.|  
|**cpu_affinity_mask**|**bigint**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> À usage interne uniquement N'accepte pas la valeur NULL.|  
|**online_scheduler_mask**|**bigint**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> À usage interne uniquement N'accepte pas la valeur NULL.|  
|**processor_group**|**smallint**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> À usage interne uniquement N'accepte pas la valeur NULL.|  
|**foreign_committed_kb**|**bigint**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Spécifie la quantité de mémoire validée, en Ko, d'autres nœuds de mémoire. N'accepte pas la valeur NULL.|  
|**target_kb** |**bigint** |**S’applique aux**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Spécifie l’objectif de la mémoire pour le nœud de mémoire, en Ko. |   
|**pdw_node_id**|**int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur du nœud qui se trouve sur cette distribution.|  
  
## <a name="permissions"></a>Permissions  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveaux Premium, nécessite le `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard et les niveaux de base, nécessite le **administrateur du serveur** ou **administrateur Active Directory de Azure** compte.   
  
## <a name="see-also"></a>Voir aussi  
  [Système d’exploitation de serveur SQL relatives des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


