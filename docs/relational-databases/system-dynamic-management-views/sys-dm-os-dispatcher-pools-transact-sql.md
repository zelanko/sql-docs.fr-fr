---
title: sys. dm_os_dispatcher_pools (Transact-SQL) | Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6ec15e83ee3def969522963d757feeacfd2d5353
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754196"
---
# <a name="sysdm_os_dispatcher_pools-transact-sql"></a>sys.dm_os_dispatcher_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Retourne des informations sur les pools de répartiteurs de la session. Les pools de répartiteurs sont des pools de threads utilisés par les composants système pour effectuer  un traitement en arrière-plan.  
  
> [!NOTE]  
>  Pour appeler cette valeur à partir de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , utilisez le nom **sys. dm_pdw_nodes_os_dispatcher_pools**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|dispatcher_pool_address|**varbinary (8)**|Adresse du pool de répartiteurs. dispatcher_pool_address est unique. N'accepte pas la valeur NULL.|  
|type|**nvarchar(256)**|Type du pool de répartiteurs. N'accepte pas la valeur NULL. Il existe deux types de pools de répartiteurs :<br /><br /> DISP_POOL_XE_ENGINE<br /><br /> DISP_POOL_XE_SESSION<br /><br /> Interroger la DMV pour obtenir la liste complète|  
|name|**nvarchar(256)**|Nom du pool de répartiteurs. N'accepte pas la valeur NULL.|  
|dispatcher_count|**int**|Nombre de threads de répartiteurs actifs. N'accepte pas la valeur NULL.|  
|dispatcher_ideal_count|**int**|Nombre de threads de répartiteurs que le pool de répartiteurs peut être amené à utiliser. N'accepte pas la valeur NULL.|  
|dispatcher_timeout_ms|**int**|Durée, en millisecondes, pendant laquelle un répartiteur attend une nouvelle tâche avant de se fermer. N'accepte pas la valeur NULL.|  
|dispatcher_waiting_count|**int**|Nombre de threads de répartiteurs inactifs. N'accepte pas la valeur NULL.|  
|queue_length|**int**|Nombre d'éléments de travail attendant d'être gérés par le pool de répartiteurs. N'accepte pas la valeur NULL.|  
|pdw_node_id|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ,[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , requiert l' `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   

## <a name="see-also"></a>Voir aussi  
  
  


