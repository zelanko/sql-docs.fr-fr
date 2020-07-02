---
title: sys. dm_cluster_endpoints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, big-data-clusters
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_cluster_endpoints
- dm_cluster_endpoints_TSQL
- dm_cluster_endpoints
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cluster_endpoints dynamic management view
ms.assetid: ''
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 95f251db2efe471455d18f4735be99ecee962a7d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717502"
---
# <a name="sysdm_cluster_endpoints-transact-sql"></a>sys. dm_cluster_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx_md](../../includes/applies-to-version/sqlserver2019.md)]

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|name|`sysname`|Nom du service exposé en externe dans un cluster SQL Big Data. Identificateur unique du point de terminaison. Clé pour cette vue. N'accepte pas la valeur NULL. |  
|description|`nvarchar(4000)`|Description du service. N'accepte pas la valeur NULL. |
|endpoint|`sysname`|URL de point de terminaison ou attribut de connexion. N'accepte pas la valeur NULL. |
|protocol_desc|`sysname`|Description du protocole de point de terminaison |

## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , requiert l' `VIEW SERVER STATE` autorisation.

## <a name="see-also"></a>Voir aussi

[Que sont [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)] ](../../big-data-cluster/big-data-cluster-overview.md)?
