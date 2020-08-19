---
description: sys. pdw_health_component_groups (Transact-SQL)
title: sys. pdw_health_component_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 5ba27432-7a29-4420-b73d-def621c0b3ac
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a327506fbfe71aa7473669bd63f7c4aec147fd7f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490270"
---
# <a name="syspdw_health_component_groups-transact-sql"></a>sys. pdw_health_component_groups (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Stocke des informations sur les regroupements logiques des composants et des appareils.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|group_id|**int**|Identificateur unique pour les composants et les périphériques.<br /><br /> Clé pour cette vue.|NOT NULL|  
|group_name|**nvarchar(255)**|Nom de groupe logique pour les composants et les périphériques.|NOT NULL|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue SQL Data Warehouse et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
