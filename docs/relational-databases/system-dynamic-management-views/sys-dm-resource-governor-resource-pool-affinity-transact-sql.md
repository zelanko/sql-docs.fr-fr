---
description: sys.dm_resource_governor_resource_pool_affinity (Transact-SQL)
title: sys. dm_resource_governor_resource_pool_affinity (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_affinity_TSQL
- sys.dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_affinity
- sys.dm_resource_governor_resource_pool_affinity
ms.assetid: a197ec19-a2ba-44f5-a4f2-3eee33ebd77d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7aefd457e99626a1c16ce04b6ecbc579d2de1ed6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454847"
---
# <a name="sysdm_resource_governor_resource_pool_affinity-transact-sql"></a>sys.dm_resource_governor_resource_pool_affinity (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Suit l'affinité du pool de ressources.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Nom de Colmn|Type de données|Description|  
|----------------|---------------|-----------------|  
|Pool_id|**int**|ID du pool de ressources. N'accepte pas la valeur NULL.|  
|Processor_group|**smallint**|ID du groupe de processeur logique Windows. N'accepte pas la valeur NULL.|  
|Scheduler_mask|**bigint**|Masque binaire qui représente les planificateurs associés à ce pool. N'accepte pas la valeur NULL.|  
  
## <a name="remarks"></a>Notes  
 Les pools créés avec une affinité AUTO n'apparaîtront pas dans cette vue car elles n'ont pas d'affinité. Pour plus d’informations, consultez les instructions [Create RESOURCE pool &#40;Transact-sql&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md) et [ALTER resource pool &#40;transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
