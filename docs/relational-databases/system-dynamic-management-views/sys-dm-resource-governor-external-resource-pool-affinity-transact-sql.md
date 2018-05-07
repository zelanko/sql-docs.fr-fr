---
title: Sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- sys.dm_resource_governor_external_resource_pool_affinity_TSQL
- dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity
ms.assetid: e32fac49-5161-47c0-8540-af3fe730c00c
caps.latest.revision: 8
author: jeannt
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 981b47224de858bcc5d1702ff1a0322b23b11c8b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmresourcegovernorexternalresourcepoolaffinity-transact-sql"></a>Sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**S’applique à** : [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] et [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Retourne les informations d’affinité du processeur sur la configuration actuelle du pool de ressources externes.
  
|Nom de colonne|Type de données| Description|
|----------------|---------------|-----------------|
|pool_id|**int**|L’ID du pool de ressources externes. N'accepte pas la valeur NULL.|
|processor_group|**smallint**|ID du groupe de processeur logique Windows. N'accepte pas la valeur NULL.|
|cpu_mask|**bigint**|Masque binaire représentant les unités centrales associées à ce pool. N'accepte pas la valeur NULL.|
  
## <a name="remarks"></a>Notes

Qui est créées avec une affinité `AUTO` n’apparaissent pas dans cette vue, car ils n’ont aucun affinité. Pour plus d’informations, consultez la [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41; ](../../t-sql/statements/create-external-resource-pool-transact-sql.md) et [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-external-resource-pool-transact-sql.md) instructions.

## <a name="permissions"></a>Autorisations

Nécessite l'autorisation `VIEW SERVER STATE`.

## <a name="see-also"></a>Voir aussi

[Gouvernance des ressources de Machine Learning dans SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)

[Sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[external scripts enabled (option de configuration de serveur)](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
