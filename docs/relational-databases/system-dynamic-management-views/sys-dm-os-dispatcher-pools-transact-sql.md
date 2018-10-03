---
title: Sys.dm_os_dispatcher_pools (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_dispatcher_pools_TSQL
- dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], views
- sys.dm_os_dispatcher_pools DMV
ms.assetid: b9edbc83-c6bc-4753-9bb5-a454cfe7d6bf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a7a03063ad61c380f72e9a52b71f268b06d822d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756507"
---
# <a name="sysdmosdispatcherpools-transact-sql"></a>sys.dm_os_dispatcher_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur les pools de répartiteurs de la session. Les pools de répartiteurs sont des pools de threads utilisés par les composants système pour effectuer  un traitement en arrière-plan.  
  
> [!NOTE]  
>  À appeler à partir [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_dispatcher_pools**.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|dispatcher_pool_address|**varbinary(8)**|Adresse du pool de répartiteurs. dispatcher_pool_address est unique. N'accepte pas la valeur NULL.|  
|Type|**nvarchar (256)**|Type du pool de répartiteurs. N'accepte pas la valeur NULL. Il existe deux types de pools de répartiteurs :<br /><br /> DISP_POOL_XE_ENGINE<br /><br /> DISP_POOL_XE_SESSION<br /><br /> Interrogez la DMV pour obtenir la liste complète|  
|NAME|**nvarchar (256)**|Nom du pool de répartiteurs. N'accepte pas la valeur NULL.|  
|dispatcher_count|**Int**|Nombre de threads de répartiteurs actifs. N'accepte pas la valeur NULL.|  
|dispatcher_ideal_count|**Int**|Nombre de threads de répartiteurs que le pool de répartiteurs peut être amené à utiliser. N'accepte pas la valeur NULL.|  
|dispatcher_timeout_ms|**Int**|Durée, en millisecondes, pendant laquelle un répartiteur attend une nouvelle tâche avant de se fermer. N'accepte pas la valeur NULL.|  
|dispatcher_waiting_count|**Int**|Nombre de threads de répartiteurs inactifs. N'accepte pas la valeur NULL.|  
|queue_length|**Int**|Nombre d'éléments de travail attendant d'être gérés par le pool de répartiteurs. N'accepte pas la valeur NULL.|  
|pdw_node_id|**Int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
## <a name="permissions"></a>Permissions

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   

## <a name="see-also"></a>Voir aussi  
  
  


