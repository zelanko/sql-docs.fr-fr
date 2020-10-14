---
description: sys.pdw_health_components (Transact-SQL)
title: sys.pdw_health_components (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: d5c7589b-09b0-4f12-ab84-feb3ec3fbaaa
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2b27f535bbe440e3ce09602b4c1098a33d3883f2
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92034807"
---
# <a name="syspdw_health_components-transact-sql"></a>sys.pdw_health_components (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Stocke des informations sur tous les composants et périphériques qui existent dans le système. Cela inclut le matériel, les périphériques de stockage et les périphériques réseau.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|component_id|**int**|Identificateur unique d’un composant ou d’un périphérique.<br /><br /> Clé pour cette vue.|NOT NULL|  
|group_id|**Int**|Groupe de composants logiques auquel ce composant appartient. Voir [sys.pdw_health_components (parallèle Data Warehouse)](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|component_name|**nvarchar(255)**|Nom du composant.|NOT NULL|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue Azure Synapse Analytics et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
