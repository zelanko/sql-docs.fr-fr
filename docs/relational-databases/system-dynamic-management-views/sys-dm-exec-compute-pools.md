---
description: sys.dm_exec_compute_pools (Transact-SQL)
title: sys.dm_exec_compute_pools (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, big-data-clusters
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_compute_pools
- dm_exec_compute_pools_TSQL
- dm_exec_compute_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_compute_pools dynamic management view
ms.assetid: ''
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-ver15||>=sql-server-linux-2017'
ms.openlocfilehash: f6affbcc67e3c4a95929263a3c90bd93e1ec7826
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97411206"
---
# <a name="sysdm_exec_compute_pools-transact-sql"></a>sys.dm_exec_compute_pools (Transact-SQL)
[!INCLUDE[sqlserver2019](../../includes/applies-to-version/sqlserver2019.md)]

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|name|`sysname`|Nom du pool de calcul. N'accepte pas la valeur NULL. Retourne `default` pour le pool de calcul par défaut. |
|compute_pool_id|`int`|Identificateur unique du pool. Clé pour cette vue.|  
|location|`sysname`|Point de terminaison à contrôleur dans un cluster Big Data SQL. N'accepte pas la valeur NULL. |

## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , requiert l' `VIEW SERVER STATE` autorisation.

## <a name="see-also"></a>Voir aussi

[Que sont [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)] ](../../big-data-cluster/big-data-cluster-overview.md)?
