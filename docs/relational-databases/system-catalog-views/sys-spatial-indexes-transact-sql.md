---
title: Sys.spatial_indexes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.spatial_indexes_TSQL
- spatial_indexes
- spatial_indexes_TSQL
- sys.spatial_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_indexes catalog view
ms.assetid: 40e967d5-2e8d-45af-bf5e-5251493cf7cb
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3b3a8337b40a3d6a6ff397775301f3e2d7aa4103
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031304"
---
# <a name="sysspatialindexes-transact-sql"></a>sys.spatial_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Représente les informations d'index principal des index spatiaux.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|\<héritée de colonnes >||Hérite des colonnes de [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).|  
|spatial_index_type|**tinyint**|Type d'index spatial :<br /><br /> 1 = Index spatial géométrique<br /><br /> 2 = Index spatial géographique|  
|spatial_index_type_desc|**nvarchar(60)**|Description du type d'index spatial :<br /><br /> GEOMETRY = Index spatial géométrique<br /><br /> GEOGRAPHY = Index spatial géographique|  
|tessellation_scheme|**sysname**|Nom du schéma de pavage :<br /><br /> GEOMETRY_GRID, GEOMETRY_AUTO_GRID,<br /><br /> GEOGRAPHY_GRID, GEOGRAPHY_AUTO_GRID<br /><br /> Remarque : Pour plus d’informations sur les schémas de pavage, consultez [vue d’ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md).|  
|\<héritée de colonnes >||Hérite des colonnes de [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).<br /><br /> Les colonnes héritées has_filter et filter_definition apparaissent après les colonnes qui sont spécifiques aux index spatiaux.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.spatial_index_tessellations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-spatial-index-tessellations-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [Vue d’ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)  
  
  
