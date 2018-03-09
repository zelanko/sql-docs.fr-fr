---
title: sys.dm_pdw_component_health_status (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9de0ecd4e004d45f3cf56a5f9fcadd6563eb04f6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwcomponenthealthstatus-transact-sql"></a>sys.dm_pdw_component_health_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contient des informations sur l’intégrité actuelle des composants de l’application.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||Non NULL|  
|component_id|int|L’ID du composant. Consultez [sys.pdw_health_components &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, id_composant, property_id et component_instance_id forment la clé pour cette vue.|Non NULL|  
|property_id|**int**|L’ID de la propriété. Consultez [sys.pdw_health_component_properties &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md).|NOT NULL|  
|component_instance_id|**nvarchar(255)**|Identifie une instance d’un composant. Par exemple, une instance d’un processeur peut être identifiée par component_instance_id = 'CPU1'.<br /><br /> pdw_node_id, id_composant, property_id et component_instance_id forment la clé pour cette vue.|NOT NULL|  
|property_value|**nvarchar(255)**|La valeur actuelle de la propriété.|NULL|  
|update_time|**datetime**|La dernière mise à jour de la métrique.|NOT NULL|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de gestion dynamique de l’entrepôt de données en parallèle &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
