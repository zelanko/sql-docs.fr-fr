---
title: sys. pdw_health_component_status_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: def9dc4a7601e4d5a89794e85f4e209036966f73
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87397115"
---
# <a name="syspdw_health_component_status_mappings-transact-sql"></a>sys. pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Définit le mappage entre les [!INCLUDE[ssDW](../../includes/ssdw-md.md)] États des composants et les noms de composants définis par le fabricant.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Identificateur unique de la propriété.<br /><br /> property_id, component_id et physical_name forment la clé de cette vue.|NOT NULL|  
|component_id|**int**|ID du composant. Consultez [sys. pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id, component_id et physical_name forment la clé de cette vue.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nom de la propriété tel que défini par le fabricant.<br /><br /> property_id, component_id et physical_name forment la clé de cette vue.|NOT NULL|  
|logical_name|**nvarchar(255)**|Nom de la propriété tel que défini par [!INCLUDE[ssDW](../../includes/ssdw-md.md)] .|NOT NULL<br /><br /> 0-l’instance d’appareil est unique.<br /><br /> 1-l’instance d’appareil n’est pas unique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue SQL Data Warehouse et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
