---
title: Sys.pdw_health_component_status_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4b2d572b79c15c369e33190c183c249de3b8fb0c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000861"
---
# <a name="syspdwhealthcomponentstatusmappings-transact-sql"></a>sys.pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Définit le mappage entre le [!INCLUDE[ssDW](../../includes/ssdw-md.md)] état des composants et les noms de composant défini par le fabricant.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**Int**|Identificateur unique de la propriété.<br /><br /> property_id et physical_name id_composant forment la clé pour cette vue.|NOT NULL|  
|id_composant|**Int**|L’ID du composant. Consultez [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id et physical_name id_composant forment la clé pour cette vue.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nom de la propriété comme défini par le fabricant.<br /><br /> property_id et physical_name id_composant forment la clé pour cette vue.|NOT NULL|  
|logical_name|**nvarchar(255)**|Nom de la propriété comme défini par [!INCLUDE[ssDW](../../includes/ssdw-md.md)].|NOT NULL<br /><br /> 0 - l’instance de périphérique est unique.<br /><br /> 1 - instance de périphérique n’est pas unique.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
