---
title: sys.dm_pdw_component_health_alerts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 88f05392-1e97-4693-ba60-a4910af3c000
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7b3c6cb1c61c15cb81a5c9452b874263cf62bc02
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62690499"
---
# <a name="sysdmpdwcomponenthealthalerts-transact-sql"></a>sys.dm_pdw_component_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Magasins précédemment émis des alertes sur les composants de l’appliance.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**Int**|Identificateur unique d’un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nœud.<br /><br /> pdw_node_id id_composant, component_instance_id, alert_id et alert_instance_id forment la clé pour cette vue.|NOT NULL|  
|component_id|**Int**|L’ID du composant. See [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id id_composant, component_instance_id, alert_id et alert_instance_id forment la clé pour cette vue.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id id_composant, component_instance_id, alert_id et alert_instance_id forment la clé pour cette vue.|NOT NULL|  
|alert_id|**Int**|L’ID pour le type d’alerte. See [sys.pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id id_composant, component_instance_id, alert_id et alert_instance_id forment la clé pour cette vue.|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|Identifie une instance d’une alerte donnée.<br /><br /> pdw_node_id id_composant, component_instance_id, alert_id et alert_instance_id forment la clé pour cette vue.|NOT NULL|  
|previous_value|**nvarchar(255)**|Utilisé lorsque l’alerte est de type StatusChange. Il s’agit de l’état du composant précédent. Valeur est NULL pour les alertes de seuil de type. Consultez [sys.pdw_health_alerts &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) pour obtenir la liste des types d’alerte.|NULL|  
|current_value|**nvarchar(255)**|Utilisé lorsque l’alerte est de type StatusChange. Il s’agit de l’état du composant actuel. Valeur est NULL pour les alertes de seuil de type. Consultez [sys.pdw_health_alerts &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) pour obtenir la liste des types d’alerte.|NULL|  
|create_time|**datetime**|Heure et date à laquelle l’alerte a été générée.|NOT NULL|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
