---
title: Sys.dm_exec_compute_nodes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODES_TSQL
- DM_EXEC_COMPUTE_NODES
- SYS.DM_EXEC_COMPUTE_NODES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_compute_nodes management view
- PolyBase, views
- PolyBase management views
- dm_exec_compute_nodes management view
ms.assetid: 0de4b7a4-401f-4e2d-9ab0-c54587e05154
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e09741600a63596d9b486ebf2d36a808e7981a87
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753117"
---
# <a name="sysdmexeccomputenodes-transact-sql"></a>Sys.dm_exec_compute_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contient des informations sur les nœuds utilisés avec la gestion des données PolyBase. Elle répertorie une ligne par nœud.  
  
 Utilisez cette vue de gestion dynamique pour afficher la liste de tous les nœuds du cluster de montée en puissance avec leur rôle, le nom et l’adresse IP.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**Int**|Id numérique unique associé au nœud. Clé pour cette vue.|Unique sur le cluster de montée en puissance, quel que soit le type.|  
|Type|**nvarchar(32)**|Type du nœud.|« COMPUTE », « PRINCIPAL »|  
|NAME|**nvarchar(32)**|Nom logique du nœud.|N’importe quelle chaîne de longueur appropriée.|  
|address|**nvarchar(32)**|Adresse IP de ce nœud.|Plage d’adresses IP|  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes avec les vues de gestion dynamique de PolyBase](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à la base de données &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
