---
title: Sys.stats_columns (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 12/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- stats_columns_TSQL
- stats_columns
- sys.stats_columns
- sys.stats_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.stats_columns catalog view
ms.assetid: 93414d07-97e9-4501-8577-f35b8d68fbe9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13114155ad4820ee293acdd11b7833083dafd9fc
ms.sourcegitcommit: c4633058216bcf6748db0eaa0e815761dc98c24d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2017
---
# <a name="sysstatscolumns-transact-sql"></a>sys.stats_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne pour chaque colonne qui fait partie de **sys.stats** des statistiques.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|ID de l'objet dont cette colonne fait partie.|  
|**stats_id**|**Int**|ID des statistiques auxquelles cette colonne prend part.<br /><br />Si les statistiques correspondent à un index, le *stats_id* valeur est identique à la *index_id* valeur dans le [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vue de catalogue.|  
|**stats_column_id**|**Int**|Ordinal à partir de 1 dans l'ensemble des colonnes de statistiques.|  
|**column_id**|**Int**|ID de la colonne à partir de **sys.columns**.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
 [Statistiques](../../relational-databases/statistics/statistics.md)    
 [sys.dm_db_stats_properties &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [Sys.dm_db_stats_histogram &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md)   
 [Sys.stats &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)  
  
  
