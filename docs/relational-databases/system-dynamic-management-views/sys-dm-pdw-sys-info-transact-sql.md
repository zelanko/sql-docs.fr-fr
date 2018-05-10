---
title: Sys.dm_pdw_sys_info (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e1fe45c9844346b96da561dc48786ffbed963d77
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmpdwsysinfo-transact-sql"></a>sys.dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Fournit un ensemble de compteurs au niveau du matériel qui reflètent l’activité globale du matériel.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|Nombre de sessions actuellement dans le système.|0 à max_active_sessions (voir ci-dessous).|  
|idle_sessions|**int**|Nombre de sessions actuellement inactives.||  
|active_requests|**int**|Nombre de demandes actives en cours d’exécution.||  
|queued_requests|**int**|Nombre de demandes actuellement en file d’attente.||  
|active_loads|**int**|Nombre de chargements en cours d’exécution dans le système.||  
|queued_loads|**int**|Nombre de charges en file d’attente en attente d’exécution.||  
|active_backups|**int**|Nombre de sauvegardes en cours d’exécution.||  
|active_restores|**int**|Nombre de restaurations de sauvegardes en cours d’exécution.||  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les données en parallèle de l’entrepôt de vues de gestion dynamique &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
