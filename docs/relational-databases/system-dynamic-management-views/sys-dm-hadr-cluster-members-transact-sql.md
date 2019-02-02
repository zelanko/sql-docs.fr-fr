---
title: sys.dm_hadr_cluster_members (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_cluster_members_TSQL
- sys.dm_hadr_cluster_members
- dm_hadr_cluster_members_TSQL
- dm_hadr_cluster_members
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_cluster_members catalog view
ms.assetid: feb20b3a-8835-41d3-9a1c-91d3117bc170
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e19451a24d35e63fa84a17d409d19b5c9b02ccc3
ms.sourcegitcommit: 7c052fc969d0f2c99ad574f99076dc1200d118c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2019
ms.locfileid: "55570722"
---
# <a name="sysdmhadrclustermembers-transact-sql"></a>sys.dm_hadr_cluster_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Si le nœud WSFC qui héberge une instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activée pour [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] possède un quorum WSFC, retourne une ligne pour chacun des membres qui constituent le quorum et l'état de chacun d'eux. Cela inclut tous les nœuds du cluster (retournés avec le type CLUSTER_ENUM_NODE par la **Clusterenum** (fonction)) et le témoin de disque ou partage de fichiers, le cas échéant. La ligne retournée pour un membre donné contient des informations sur l'état de ce membre. Par exemple, pour un cluster à cinq nœuds avec un quorum de nœud majoritaire dans lequel un nœud est arrêté, lorsque **sys.dm_hadr_cluster_members** sont interrogées à partir d’une instance de serveur est activé pour [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] qui réside sur un nœud avec quorum, **sys.dm_hadr_cluster_members** reflète l’état du nœud arrêté en tant que « NODE_DOWN ».  
  
 Si le nœud WSFC n'a aucun quorum, aucune ligne n'est retournée.  
  
 Utilisez cette vue de gestion dynamique pour répondre aux questions suivantes :  
  
-   Quels nœuds sont en cours d'exécution sur le cluster WSFC ?  
  
-   Combien d'échecs de plus le cluster WSFC peut-il tolérer avant de perdre le quorum dans le cas d'un nœud majoritaire ?  

 > [!TIP]
 > À compter de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], cette vue de gestion dynamique prend en charge le basculement Instances de Cluster AlwaysOn en plus des groupes de disponibilité AlwaysOn.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar(128)**|Nom de membre, qui peut être un nom d'ordinateur, une lettre de lecteur ou un chemin d'accès de partage de fichiers.|  
|**member_type**|**tinyint**|Type du membre. Peut prendre une des valeurs suivantes :<br /><br /> 0 = Nœud WSFC<br /><br /> 1 = Disque témoin<br /><br /> 2 = Témoin de partage de fichiers<br /><br /> 3 = témoin cloud|  
|**member_type_desc**|**nvarchar(50)**|Description de **member_type**, l’un des :<br /><br /> CLUSTER_NODE<br /><br /> DISK_WITNESS<br /><br /> FILE_SHARE_WITNESS<br /><br /> CLOUD_WITNESS|  
|**member_state**|**tinyint**|État du membre. Peut prendre une des valeurs suivantes :<br /><br /> 0 = Hors connexion<br /><br /> 1 = En ligne|  
|**member_state_desc**|**nvarchar(60)**|Description de **member_state**, l’un des :<br /><br /> UP<br /><br /> VERS LE BAS|  
|**number_of_quorum_votes**|**tinyint**|Nombre de votes de quorum détenus par ce membre de quorum. Pour aucune majorité : Quorums seul disque, cette valeur par défaut est 0. Pour les autres types de quorum, cette valeur est par défaut 1.|  
  
## <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="examples"></a>Exemples  
  
## <a name="see-also"></a>Voir aussi  
 [Vues et fonctions de gestion dynamiques de groupes de disponibilité Always On &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Affichages catalogue des groupes de disponibilité Always On &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Surveiller des groupes de disponibilité &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
