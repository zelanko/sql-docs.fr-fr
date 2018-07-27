---
title: Sys.dm_resource_governor_external_resource_pools (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/02/2018
ms.suite: sql
ms.prod: sql
ms.technology: machine-learning
ms.reviewer: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pools_TSQL
- sys.dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_external_resource_pools
- sys.dm_resource_governor_external_resource_pools
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 80beafc8a281f7f4af71484acfa01ed0016b7de2
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107661"
---
# <a name="sysdmresourcegovernorexternalresourcepools-transact-sql"></a>Sys.dm_resource_governor_external_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Retourne des informations sur l’état actuel du pool de ressources externes, la configuration actuelle de pools de ressources et les statistiques de pool de ressources. 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône de lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Nom de Colmn      |Type de données      |Description|  
|----------------|---------------|-----------------| 
| external_pool_id|**Int**|ID du pool de ressources. N'accepte pas la valeur NULL. |
| NAME|**sysname**|Le nom du pool de ressources. N'accepte pas la valeur NULL. 
| pool_version|**Int**|Numéro de version interne.|
| max_cpu_percent|**Int**|Configuration actuelle de la bande passante processeur moyenne maximale pour toutes les demandes dans le pool de ressources en cas de contention du processeur. N'accepte pas la valeur NULL. |
| max_processes|**Int**|Nombre maximal de processus externes simultanées. La valeur par défaut 0 spécifie qu'il n'y a pas de limite. N'accepte pas la valeur NULL.|
| max_memory_percent|**Int**|Configuration actuelle du pourcentage de la mémoire totale du serveur qui peut être utilisé par les demandes dans ce pool de ressources. N'accepte pas la valeur NULL. |
| statistics_start_time|**datetime**|Heure à laquelle les statistiques ont été réinitialisées pour ce pool. N'accepte pas la valeur NULL. 
| peak_memory_kb|**bigint**|La quantité maximale de mémoire utilisée, en kilo-octets, pour le pool de ressources. N'accepte pas la valeur NULL. |
| write_io_count|**Int**|Total des entrées/sorties d'écriture émises depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL. |
| read_io_count|**Int**|Total d'entrées/sorties de lecture émises depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL. |
| total_cpu_kernel_ms|**bigint**|Le temps processeur cumulé utilisateur noyau en millisecondes depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL. |
| total_cpu_user_ms|**bigint**|Temps utilisateur processeur cumulé en millisecondes depuis que les statistiques du gouverneur de ressources ont été réinitialisées. N'accepte pas la valeur NULL. |
| active_processes_count|**Int**|Le nombre de processus externes en cours d’exécution au moment de la demande. N'accepte pas la valeur NULL. |

 
## <a name="permissions"></a>Permissions

Nécessite l'autorisation `VIEW SERVER STATE`.

## <a name="see-also"></a>Voir aussi  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
