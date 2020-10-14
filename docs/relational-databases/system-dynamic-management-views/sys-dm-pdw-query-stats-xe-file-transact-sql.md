---
description: sys.dm_pdw_query_stats_xe_file (Transact-SQL)
title: sys.dm_pdw_query_stats_xe_file (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e0cd402f-04d0-4a5b-b725-88b31bb7862e
author: markingmyname
ms.author: maghan
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cd4cd9bd7937e9d6a03df70d03e3b51776d7bdbe
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035272"
---
# <a name="sysdm_pdw_query_stats_xe_file-transact-sql"></a>sys.dm_pdw_query_stats_xe_file (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Cette DMV est déconseillée et sera supprimée dans une version ultérieure. Dans cette version, elle retourne 0 ligne.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|event|**nvarchar(60)**|Clé pour cette vue.||  
|Données|**xml**|||  
|pdw_node_id|**int**|Nœud sur lequel cette instance XEvent est en cours d’exécution.||  
  
## <a name="see-also"></a>Voir aussi  
 [Azure Synapse Analytics et les vues de gestion dynamique Parallel Data Warehouse &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
