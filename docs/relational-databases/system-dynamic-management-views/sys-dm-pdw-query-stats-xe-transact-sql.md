---
title: Sys.dm_pdw_query_stats_xe (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d551241-db35-4958-b60f-55e996f95c1f
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b6c641ac0a99d872f05eac9c0a7cac97c14238dc
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmpdwquerystatsxe-transact-sql"></a>Sys.dm_pdw_query_stats_xe (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Cette DMV est déconseillée et sera supprimée dans une version ultérieure. Dans cette version, il retourne 0 ligne.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|événement|**nvarchar(60)**|Clé pour cette vue.||  
|event_id|**nvarchar(36)**|||  
|create_time|**datetime**|||  
|session_id|**int**|Id de la session.|Consultez session_id dans [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|cpu|**int**|||  
|reads|**int**|Nombre de lectures logiques depuis le début de l’événement.||  
|writes|**int**|Nombre d’écritures logiques depuis le début de l’événement.||  
|sql_text|**nvarchar(4000)**|||  
|client_app_name|**nvarchar(255)**|||  
|pile_tsql|**nvarchar(255)**|||  
|pdw_node_id|**int**|Nœud sur lequel cette instance Xevent est en cours d’exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les données en parallèle de l’entrepôt de vues de gestion dynamique &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
