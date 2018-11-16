---
title: Sys.dm_pdw_wait_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cfb8d905-c34f-44de-9574-dde81e170916
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a62b88ae5c5e0589b54781c85ff43cc39babe2fb
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51667808"
---
# <a name="sysdmpdwwaitstats-transact-sql"></a>Sys.dm_pdw_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations relatives à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] état du système d’exploitation liée aux instances en cours d’exécution sur les différents nœuds. Pour obtenir la liste des types d’attentes et leur description, consultez [sys.dm_os_wait_stats](https://msdn.microsoft.com/library/ms179984\(v=sql.120\).aspx).  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|**pdw_node_id**|**Int**|ID du nœud que cette entrée fait référence.||  
|**wait_name**|**nvarchar(255)**|Nom du type d'attente.||  
|**max_wait_time**|**bigint**|Délai d’attente maximal de ce type d’attente.||  
|**request_count**|**bigint**|Nombre d’attentes de ce type en attente d’attente.||  
|**signal_time**|**bigint**|Différence entre le moment où le thread qui attend a été signalé et le moment où il a commencé à s'exécuter.||  
|**completed_count**|**bigint**|Nombre total d’attentes de ce type résolus depuis le dernier serveur de redémarrer.||  
|**wait_time**|**bigint**|Temps d’attente total pour ce type d’attente dans millisecons. Temps inclusif de signal_time.||  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [Sys.dm_pdw_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
  
