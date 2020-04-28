---
title: sys. dm_pdw_sys_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 0bc6c97f4d41023b822f42a6bbe4c5b193d42e45
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088762"
---
# <a name="sysdm_pdw_sys_info-transact-sql"></a>sys. dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Fournit un ensemble de compteurs au niveau de l’appareil qui reflètent l’activité globale sur l’appliance.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|Nombre de sessions actuellement dans le système.|0 pour max_active_sessions (voir ci-dessous).|  
|idle_sessions|**int**|Nombre de sessions actuellement inactives.||  
|active_requests|**int**|Nombre de demandes actives en cours d’exécution.||  
|queued_requests|**int**|Nombre de demandes actuellement mises en file d’attente.||  
|active_loads|**int**|Nombre de chargements en cours d’exécution dans le système.||  
|queued_loads|**int**|Nombre de chargements en file d’attente en attente d’exécution.||  
|active_backups|**int**|Nombre de sauvegardes en cours d’exécution.||  
|active_restores|**int**|Nombre de restaurations de sauvegarde en cours d’exécution.||  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
