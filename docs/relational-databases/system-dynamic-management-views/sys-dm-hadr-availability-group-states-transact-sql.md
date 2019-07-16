---
title: Sys.dm_hadr_availability_group_states (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_availability_group_states
- sys.dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_group_states dynamic management view
ms.assetid: d18019dd-f8dc-4492-b035-b1a639369b65
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 91efefbdc28480cf2a3b3fb579dba0946dba8a2e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900777"
---
# <a name="sysdmhadravailabilitygroupstates-transact-sql"></a>sys.dm_hadr_availability_group_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque groupe de disponibilité Always On qui possède un réplica de disponibilité sur l’instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Chaque ligne affiche les états qui définissent l'intégrité d'un groupe de disponibilité donné.  
  
> [!NOTE]  
>  Pour obtenir la liste complète des, interrogez la [sys.availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) vue de catalogue.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Identificateur unique du groupe de disponibilité.|  
|**primary_replica**|**varchar(128)**|Nom de l'instance de serveur qui héberge le réplica principal actuel.<br /><br /> NULL = N'est pas le réplica principal ou impossible de communiquer avec le cluster de basculement WSFC.|  
|**primary_recovery_health**|**tinyint**|Indique l'état de récupération du réplica principal, un des suivants :<br /><br /> 0 = en cours<br /><br /> 1 = En ligne<br /><br /> NULL<br /><br /> Sur les réplicas secondaires le **primary_recovery_health** colonne est NULL.|  
|**primary_recovery_health_desc**|**nvarchar(60)**|Description de **primary_replica_health**, l’un des :<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**secondary_recovery_health**|**tinyint**|Indique l’état de récupération d’un réplica de réplica secondaire, parmi :<br /><br /> 0 = en cours<br /><br /> 1 = En ligne<br /><br /> NULL<br /><br /> Sur le réplica principal, le **secondary_recovery_health** colonne est NULL.|  
|**secondary_recovery_health_desc**|**nvarchar(60)**|Description de **secondary_recovery_health**, l’un des :<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**synchronization_health**|**tinyint**|Reflète un cumul de la **synchronization_health** de tous les réplicas de disponibilité du groupe de disponibilité. Voici les valeurs possibles et leurs descriptions.<br /><br /> 0 : Non sain. Aucun des réplicas de disponibilité ne présente un **synchronization_health** (2 = sain).<br /><br /> 1 : Partiellement sain. L'état de synchronization de certains des réplicas de disponibilité est sain.<br /><br /> 2 : Sain. L'état de synchronization de chaque réplica de disponibilité est sain.<br /><br /> Pour plus d’informations sur l’intégrité de synchronisation de réplica, consultez le **synchronization_health** colonne [sys.dm_hadr_availability_replica_states &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql.md).|  
|**synchronization_health_desc**|**nvarchar(60)**|Description de **synchronization_health**, l’un des :<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller des groupes de disponibilité &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Groupes de disponibilité Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Fonctions et vues de gestion dynamique des groupes de disponibilité Always On &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)  
  
  
