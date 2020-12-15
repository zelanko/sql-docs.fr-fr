---
description: sys.pdw_health_component_groups (Transact-SQL)
title: sys.pdw_health_component_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 5ba27432-7a29-4420-b73d-def621c0b3ac
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: 552a4b28187687c21312c5918788eaf85e799597
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97464630"
---
# <a name="syspdw_health_component_groups-transact-sql"></a>sys.pdw_health_component_groups (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Stocke des informations sur les regroupements logiques des composants et des appareils.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|group_id|**int**|Identificateur unique pour les composants et les périphériques.<br /><br /> Clé pour cette vue.|NOT NULL|  
|group_name|**nvarchar(255)**|Nom de groupe logique pour les composants et les périphériques.|NOT NULL|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue Azure Synapse Analytics et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
