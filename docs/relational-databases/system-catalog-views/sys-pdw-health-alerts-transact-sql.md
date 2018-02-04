---
title: sys.pdw_health_alerts (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
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
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28a38f60127100d80a7f9c52caa9851597403c45
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Stocke des propriétés pour les alertes différents qui peuvent se produire sur le système ; Il s’agit d’une table de catalogue pour les alertes.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|Identificateur unique de l’alerte.<br /><br /> Clé pour cette vue.|NOT NULL|  
|component_id|**int**|ID du composant à que cette alerte s’applique. Le composant est un identificateur de composant général, tel que « Bloc d’alimentation » et n’est pas spécifique à une installation. Consultez [sys.pdw_health_components &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Nom de l’alerte.|NOT NULL|  
|state|**nvarchar(32)**|État de l’alerte.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> 'Operational'<br /><br /> 'Opérationnelle'<br /><br /> 'Degraded'<br /><br /> 'Failed'|  
|severity|**nvarchar(32)**|Gravité de l’alerte.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> « Information »<br /><br /> « Avertissement »<br /><br /> 'Error'|  
|type|**nvarchar(32)**|Type d’alerte.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> StatusChange - l’état du périphérique a changé.<br /><br /> Seuil - une valeur a dépassé la valeur de seuil.|  
|description|**nvarchar(4000)**|Description de l’alerte.|NOT NULL|  
|condition|**nvarchar(255)**|Utilisé lorsque type = seuil. Définit le mode de calcul du seuil d’alerte.|NULL|  
|status|**nvarchar(32)**|État de l’alerte|NULL|  
|condition_value|**bit**|Indique si l’alerte est autorisée à se produire au cours du système.|NULL<br /><br /> Valeurs possibles<br /><br /> 0 - pas d’alerte.<br /><br /> 1 - alerte est générée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
