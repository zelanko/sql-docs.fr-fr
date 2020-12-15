---
description: sys.dm_pdw_os_performance_counters (Transact-SQL)
title: sys.dm_pdw_os_performance_counters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
author: markingmyname
ms.author: maghan
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: 67a0bf0b52b0fc4d31400bf009476d76fdc1b1f5
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97440761"
---
# <a name="sysdm_pdw_os_performance_counters-transact-sql"></a>sys.dm_pdw_os_performance_counters (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Contient des informations sur les compteurs de performances Windows pour les nœuds dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] .  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|ID du nœud qui contient le compteur.<br /><br /> pdw_node_id et counter_name forment la clé de cette vue.|Consultez node_id dans [sys.dm_pdw_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|counter_name|**nvarchar(255)**|Nom du compteur de performances Windows.||  
|counter_category|**nvarchar(255)**|Nom de la catégorie du compteur de performance Windows.||  
|nom_instance|**nvarchar(255)**|Nom d'une instance particulière du compteur.||  
|counter_value|**Décimal (38, 10)**|Valeur actuelle du compteur.||  
|last_update_time|**Datetime2 (3)**|Horodateur de la dernière mise à jour de la valeur.||  
  
## <a name="see-also"></a>Voir aussi  
 [Azure Synapse Analytics et les vues de gestion dynamique Parallel Data Warehouse &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
