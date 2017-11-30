---
title: Sys.dm_repl_tranhash (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_tranhash
- sys.dm_repl_tranhash_TSQL
- dm_repl_tranhash_TSQL
- dm_repl_tranhash
dev_langs: TSQL
helpviewer_keywords: sys.dm_repl_tranhash dynamic management view
ms.assetid: 0cc52338-e805-4ed4-9835-b19bbf72448e
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a294cc70ded39ed12f07e16eada7b90a9a3e9b89
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="sysdmrepltranhash-transact-sql"></a>sys.dm_repl_tranhash (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur les transactions en cours de réplication dans une publication transactionnelle.  
  
|column_name|data_type|description|  
|------------------|----------------|-----------------|  
|**compartiments**|**bigint**|Nombre de compartiments dans la table de hachage.|  
|**hashed_trans**|**bigint**|Nombre de transactions validées qui ont été répliquées dans le traitement en cours.|  
|**completed_trans**|**bigint**|Nombre de transactions terminées jusqu'à présent.|  
|**compensated_trans**|**bigint**|Nombre de transactions contenant des restaurations partielles.|  
|**first_begin_lsn**|**nvarchar (64)**|Numéro séquentiel dans le journal (NSE) de départ le plus ancien dans le traitement en cours.|  
|**last_commit_lsn**|**nvarchar (64)**|Numéro NSE de la dernière validation dans le traitement en cours.|  
  
## <a name="permissions"></a>Permissions  
 Requiert l’autorisation VIEW DATABASE STATE sur la base de données de publication pour appeler **dm_repl_tranhash**.  
  
## <a name="remarks"></a>Notes  
 Les informations ne sont retournées que pour les objets de base de données répliqués actuellement chargés dans le cache des articles de réplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique &#40; liées à la réplication Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  
