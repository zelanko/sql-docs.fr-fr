---
title: Sys.dm_hadr_availability_replica_cluster_states (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_availability_replica_cluster_states_TSQL
- dm_hadr_availability_replica_cluster_states
- sys.dm_hadr_availability_replica_cluster_states
- dm_hadr_availability_replica_cluster_states_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_availability_replica_cluster_states dynamic management view
ms.assetid: 2e0dd780-6a71-4f4b-b7f7-6e063bec71d6
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 004857a97be6be430e2f7e88335ba0abf4a03dbd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmhadravailabilityreplicaclusterstates-transact-sql"></a>sys.dm_hadr_availability_replica_cluster_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque Always On réplica de disponibilité (indépendamment de son état de jointure) tous les toujours sur des groupes de disponibilité (indépendamment de l’emplacement de réplica) dans le cluster de Clustering de basculement Windows Server (WSFC).  
  
##  <a name="connected_state"></a>  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|Identificateur unique du réplica de disponibilité.|  
|**replica_server_name**|**nvarchar (256)**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge le réplica.|  
|**group_id**|**uniqueidentifier**|Identificateur unique du groupe de disponibilité.|  
|**join_state**|**tinyint**|0 = Non attachée<br /><br /> 1 = Instance attachée et autonome<br /><br /> 2 = Instance de cluster de basculement attachée|  
|**join_state_desc**|**nvarchar(60)**|NOT_JOINED<br /><br /> JOINED_STANDALONE_INSTANCE<br /><br /> JOINED_FAILOVER_CLUSTER_INSTANCE|  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller des groupes de disponibilité &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
