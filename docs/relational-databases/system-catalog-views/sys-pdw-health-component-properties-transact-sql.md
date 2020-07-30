---
title: sys. pdw_health_component_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7c0366492dbf22364b04bc436262f7cb83fe8505
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396038"
---
# <a name="syspdw_health_component_properties-transact-sql"></a>sys. pdw_health_component_properties (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Stocke les propriétés qui décrivent un appareil. Certaines propriétés affichent l’état de l’appareil et certaines propriétés décrivent l’appareil lui-même.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Identificateur unique de la propriété d’un composant.<br /><br /> property_id et component_id forment la clé de cette vue.|NOT NULL|  
|component_id|**int**|ID du composant. Consultez [sys. pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id et component_id forment la clé de cette vue.|NOT NULL|  
|property_name|**nvarchar(255)**|Nom de la propriété.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nom de la propriété tel que défini par le fabricant.|NOT NULL|  
|is_key|**bit**|Détermine si l’instance d’appareil est unique ou non unique.|NOT NULL<br /><br /> 0-l’instance d’appareil est unique.<br /><br /> 1-l’instance d’appareil n’est pas unique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue SQL Data Warehouse et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
