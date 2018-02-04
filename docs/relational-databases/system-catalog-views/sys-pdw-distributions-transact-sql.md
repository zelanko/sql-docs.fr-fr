---
title: sys.pdw_distributions (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 572b5187-9753-4063-adf8-65dea87d11f8
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 07694ebc741c769e97991e81de40fe73023106a0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwdistributions-transact-sql"></a>sys.pdw_distributions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur les distributions sur le matériel. Il répertorie une ligne par distribution de l’application.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|Id numérique unique associée à la distribution.<br /><br /> Clé pour cette vue.|1 au nombre de nœuds de calcul dans l’appliance multipliée par le nombre de distributions par nœud de calcul.|  
|pdw_node_id|**int**|ID du nœud que se trouve sur cette distribution.|Consultez pdw_node_id dans [sys.dm_pdw_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|name|**nvarchar(32)**|Identificateur associé à la distribution, utilisée comme suffixe sur les tables distribuées de chaîne.|Chaîne composée de « A-Z », « a-z », « 0-9', '_','-'.|  
|position|**int**|Position de la distribution dans un nœud respective pour les autres distributions sur ce nœud.|1 pour le nombre de distributions par nœud.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
