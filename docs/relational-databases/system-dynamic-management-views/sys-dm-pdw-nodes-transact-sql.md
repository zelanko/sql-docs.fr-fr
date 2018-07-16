---
title: Sys.dm_pdw_nodes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3f307d70f7c161743d81c33916046e88cadad9e9
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926790"
---
# <a name="sysdmpdwnodes-transact-sql"></a>Sys.dm_pdw_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur tous les nœuds dans [!INCLUDE[ssAPS](../../includes/ssaps-md.md)]. Elle répertorie une ligne par nœud dans l’appliance.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**Int**|Id numérique unique associé au nœud.<br /><br /> Clé pour cette vue.|Unique sur l’appliance, quel que soit le type.|  
|Type|**nvarchar(32)**|Type du nœud.|« COMPUTE », « CONTRÔLE », « MANAGEMENT »|  
|NAME|**nvarchar(32)**|Nom logique du nœud.|N’importe quelle chaîne de longueur appropriée.|  
|address|**nvarchar(32)**|Adresse IP de ce nœud.|Dans le format [0-255]. 0-255. 0-255. 0-255.|  
|is_passive|**Int**|Indique si la machine virtuelle en cours d’exécution du nœud est en cours d’exécution sur le serveur affecté ou qu’il a basculé vers le serveur de secours.|0 – machine virtuelle du nœud est en cours d’exécution sur le serveur d’origine.<br /><br /> 1 – machine virtuelle du nœud est en cours d’exécution sur le serveur de secours.|  
|région|**nvarchar(32)**|La région où le nœud est en cours d’exécution.|'PDW », « HDINSIGHT »|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
