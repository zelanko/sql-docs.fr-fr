---
title: sys.dm_pdw_component_health_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 602b8ed0c338ba85c35137cd2752fa4357bf63ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62692703"
---
# <a name="sysdmpdwcomponenthealthstatus-transact-sql"></a>sys.dm_pdw_component_health_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contient des informations sur l’intégrité actuelle des composants de l’appliance.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**Int**||Non Null|  
|component_id|INT|L’ID du composant. See [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, id_composant, property_id et component_instance_id forment la clé pour cette vue.|Non Null|  
|property_id|**Int**|L’ID de la propriété. Consultez [sys.pdw_health_component_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md).|NOT NULL|  
|component_instance_id|**nvarchar(255)**|Identifie une instance d’un composant. Par exemple, une instance d’un processeur peut être identifiée par component_instance_id = 'CPU1'.<br /><br /> pdw_node_id, id_composant, property_id et component_instance_id forment la clé pour cette vue.|NOT NULL|  
|property_value|**nvarchar(255)**|La valeur de propriété actuelle.|NULL|  
|update_time|**datetime**|La dernière fois que la mesure a été mis à jour.|NOT NULL|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
