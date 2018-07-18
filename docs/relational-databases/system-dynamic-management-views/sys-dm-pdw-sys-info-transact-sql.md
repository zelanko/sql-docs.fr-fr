---
title: Sys.dm_pdw_sys_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4333413236f790bf2838d768585ea75537784e6d
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926440"
---
# <a name="sysdmpdwsysinfo-transact-sql"></a>sys.dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Fournit un ensemble de compteurs au niveau de l’appliance qui reflètent l’activité globale sur l’appliance.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**Int**|Nombre de sessions actuellement dans le système.|0 à max_active_sessions (voir ci-dessous).|  
|idle_sessions|**Int**|Nombre de sessions actuellement inactives.||  
|active_requests|**Int**|Nombre de demandes actives en cours d’exécution.||  
|queued_requests|**Int**|Nombre de demandes en file d’attente.||  
|active_loads|**Int**|Nombre de charges en cours d’exécution dans le système.||  
|queued_loads|**Int**|Nombre de charges en file d’attente en attente pour l’exécution.||  
|active_backups|**Int**|Nombre de sauvegardes en cours d’exécution.||  
|active_restores|**Int**|Nombre de restaurations de sauvegarde en cours d’exécution.||  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
