---
title: sys.pdw_health_component_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e6f74c53c7b7380308ee0c620bcf07c1a8ddbc8f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56010860"
---
# <a name="syspdwhealthcomponentproperties-transact-sql"></a>sys.pdw_health_component_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Stocke les propriétés qui décrivent un appareil. Certaines propriétés indiquent l’état de l’appareil, et certaines propriétés décrivent l’appareil lui-même.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**Int**|Identificateur unique de la propriété d’un composant.<br /><br /> property_id et id_composant forment la clé pour cette vue.|NOT NULL|  
|component_id|**Int**|L’ID du composant. See [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id et id_composant forment la clé pour cette vue.|NOT NULL|  
|property_name|**nvarchar(255)**|Nom de la propriété.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nom de la propriété comme défini par le fabricant.|NOT NULL|  
|is_key|**bit**|Détermine si l’instance du périphérique est unique ou non.|NOT NULL<br /><br /> 0 - l’instance de périphérique est unique.<br /><br /> 1 - instance de périphérique n’est pas unique.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
