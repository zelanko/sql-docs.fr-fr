---
description: sys.pdw_diag_events (Transact-SQL)
title: sys.pdw_diag_events (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 59bb3e9c-2829-49a0-b382-652ed1f54f88
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9af8b5bb95dac16ab0359d3438f5b3f489313ba7
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035002"
---
# <a name="syspdw_diag_events-transact-sql"></a>sys.pdw_diag_events (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Contient des informations sur les événements qui peuvent être inclus dans les sessions de diagnostic sur le système.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|Nom de l’événement de diagnostic spécifique.||  
|**source**|**nvarchar(255)**|Source de l’événement (moteur, général, DMS, etc.)||  
|**is_enabled**|**bit**|Indique si l’événement est publié.||  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue Azure Synapse Analytics et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
