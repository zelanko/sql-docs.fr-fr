---
title: Sys.pdw_health_alerts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6f8281d520f64580af8432dbf2004227ce628d41
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37987191"
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Stocke des propriétés pour les alertes de différents qui peuvent se produire dans le système ; Il s’agit d’une table de catalogue pour les alertes.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**Int**|Identificateur unique de l’alerte.<br /><br /> Clé pour cette vue.|NOT NULL|  
|id_composant|**Int**|ID du composant à que cette alerte s’applique. Le composant est un identificateur générales des composants, tels que « Bloc d’alimentation » et n’est pas spécifique à une installation. Consultez [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Nom de l’alerte.|NOT NULL|  
|state|**nvarchar(32)**|État de l’alerte.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> 'Operational'<br /><br /> « Non opérationnelle »<br /><br /> « Dégradé »<br /><br /> « Échec »|  
|severity|**nvarchar(32)**|Gravité de l’alerte.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> « Information »<br /><br /> « Avertissement »<br /><br /> « Erreur »|  
|Type|**nvarchar(32)**|Type d’alerte.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> StatusChange - l’état du périphérique a changé.<br /><br /> Seuil - une valeur a dépassé la valeur de seuil.|  
|description|**nvarchar(4000)**|Description de l’alerte.|NOT NULL|  
|condition|**nvarchar(255)**|Utilisé lorsque type = seuil. Définit le mode de calcul du seuil d’alerte.|NULL|  
|status|**nvarchar(32)**|État de l’alerte|NULL|  
|condition_value|**bit**|Indique si l’alerte est autorisée à se produire au cours du système.|NULL<br /><br /> Valeurs possibles<br /><br /> 0 - l’alerte n’est pas générée.<br /><br /> 1 - alerte est générée.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
