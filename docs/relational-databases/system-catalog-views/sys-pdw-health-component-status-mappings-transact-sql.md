---
title: sys.pdw_health_component_status_mappings (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9ad5eb1009749cc33d142e7807447caf738190de
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwhealthcomponentstatusmappings-transact-sql"></a>sys.pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Définit le mappage entre les [!INCLUDE[ssDW](../../includes/ssdw-md.md)] état des composants et les noms de composant défini par le fabricant.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Identificateur unique de la propriété.<br /><br /> property_id et physical_name id_composant forment la clé pour cette vue.|NOT NULL|  
|component_id|**int**|L’ID du composant. Consultez [sys.pdw_health_components &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id et physical_name id_composant forment la clé pour cette vue.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nom de la propriété comme défini par le fabricant.<br /><br /> property_id et physical_name id_composant forment la clé pour cette vue.|NOT NULL|  
|logical_name|**nvarchar(255)**|Nom de la propriété comme défini par [!INCLUDE[ssDW](../../includes/ssdw-md.md)].|NOT NULL<br /><br /> 0 - l’instance de périphérique est unique.<br /><br /> 1 - instance de l’appareil n’est pas unique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
