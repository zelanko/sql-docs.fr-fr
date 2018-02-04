---
title: sys.dm_pdw_os_performance_counters (Transact-SQL) | Microsoft Docs
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
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 85c804c4045e0f601512cbf5ab76d98634c1fce2
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwosperformancecounters-transact-sql"></a>sys.dm_pdw_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contient des informations sur les compteurs de performances de Windows pour les nœuds dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|L’ID du nœud qui contient le compteur.<br /><br /> pdw_node_id et counter_name forment la clé pour cette vue.|Consultez node_id dans [sys.dm_pdw_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|counter_name|**nvarchar(255)**|Nom du compteur de performances Windows.||  
|counter_category|**nvarchar(255)**|Nom de catégorie de compteur de performances Windows.||  
|nom_instance|**nvarchar(255)**|Nom d'une instance particulière du compteur.||  
|counter_value|**Decimal(38,10)**|Valeur actuelle du compteur.||  
|last_update_time|**Datetime2(3)**|Horodatage de la dernière mise à jour la valeur.||  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de gestion dynamique de l’entrepôt de données en parallèle &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
