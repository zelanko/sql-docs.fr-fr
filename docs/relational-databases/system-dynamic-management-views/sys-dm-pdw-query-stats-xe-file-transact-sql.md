---
title: Sys.dm_pdw_query_stats_xe_file (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.component: dmv's
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e0cd402f-04d0-4a5b-b725-88b31bb7862e
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cbdace90b863ec646cd1994771ce22015ad79ac5
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmpdwquerystatsxefile-transact-sql"></a>Sys.dm_pdw_query_stats_xe_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Cette DMV est déconseillée et sera supprimée dans une version ultérieure. Dans cette version, il retourne 0 ligne.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|événement|**nvarchar(60)**|Clé pour cette vue.||  
|données|**xml**|||  
|pdw_node_id|**int**|Nœud sur lequel cette instance Xevent est en cours d’exécution.||  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les données en parallèle de l’entrepôt de vues de gestion dynamique &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
