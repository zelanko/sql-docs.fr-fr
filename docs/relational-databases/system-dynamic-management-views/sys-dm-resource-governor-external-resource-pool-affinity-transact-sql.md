---
title: sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL) Microsoft Docs
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77d0d322139be1f1c6086622855600a7c24fc4c9
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664323"
---
# <a name="sysdm_resource_governor_external_resource_pool_affinity-transact-sql"></a>sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**S’applique à :** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] et [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Renvoie les informations d’affinité du processeur sur la configuration actuelle du pool de ressources externes.
  
|Nom de la colonne|Type de données|Description|
|----------------|---------------|-----------------|
|pool_id|**Int**|L’ID du pool de ressources externes. N'accepte pas la valeur NULL.|
|processor_group|**smallint**|ID du groupe de processeur logique Windows. N'accepte pas la valeur NULL.|
|cpu_mask|**bigint**|Le masque binaire représentant les processeurs associés à ce pool. N'accepte pas la valeur NULL.|
  
## <a name="remarks"></a>Notes

Les piscines qui sont créées `AUTO` avec une affinité de ne pas apparaître dans cette vue parce qu’ils n’ont aucune affinité. Pour de plus amples renseignements, consultez les déclarations de&#41;[DE RESSOURCES EXTERNES CREATE EXTERNAL POOL&#41;&#40;Transact-SQL](../../t-sql/statements/create-external-resource-pool-transact-sql.md) et ALTER EXTERNAL RESOURCE POOL &#40;[Transact-SQL.](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)

## <a name="permissions"></a>Autorisations

Nécessite l'autorisation `VIEW SERVER STATE`.

## <a name="see-also"></a>Voir aussi

[Gouvernance des ressources de Machine Learning dans SQL Server](../../machine-learning/administration/resource-governor.md)

[sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[external scripts enabled (option de configuration de serveur)](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
