---
title: sys. dm_pdw_nodes_exec_text_query_plan (Transact-SQL) | Microsoft Docs
description: Vue de gestion dynamique qui retourne le Showplan au format texte pour un lot TSQL ou pour une instruction spécifique dans le lot.
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 7473d7cad5ba4448feca92c4a3c3f4a8804a1b65
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396637"
---
# <a name="sysdm_pdw_nodes_exec_text_query_plan--transact-sql"></a>sys. dm_pdw_nodes_exec_text_query_plan (Transact-SQL)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Retourne le plan d'exécution de requêtes au format texte pour un lot [!INCLUDE[tsql](../../includes/tsql-md.md)] ou pour une instruction spécifique dans le lot.

## <a name="table-returned"></a>Table retournée  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_ID**|**int**|ID numérique unique associé au nœud.|
|**dbid**|**smallint**|ID de la base de données de contexte qui était en fonction lorsque l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] correspondant à ce plan a été compilée. Pour les instructions SQL ad hoc et préparées, l'ID de la base de données où les instructions ont été compilées.<br /><br /> Colonne acceptant la valeur NULL.|  
|**arguments**|**int**|ID de l'objet (par exemple, procédure stockée ou fonction définie par l'utilisateur) pour ce plan de requête. Pour les traitements ad hoc et préparés, cette colonne est **null**.<br /><br /> Colonne acceptant la valeur NULL.|  
|**number**|**smallint**|Entier servant à la numérotation des procédures stockées. Pour les traitements ad hoc et préparés, cette colonne est **null**.<br /><br /> Colonne acceptant la valeur NULL.| 
|**chiffrées**|**bit**|Indique si la procédure stockée correspondante est chiffrée.<br /><br /> 0 = Non chiffrée.<br /><br /> 1 = Chiffrée.<br /><br /> Colonne n'acceptant pas la valeur NULL.|  
|**query_plan**|**nvarchar(max)**|Contient la représentation Showplan au moment de la compilation du plan d’exécution de requête spécifié avec *plan_handle*. Le Showplan est au format texte. Un plan est généré pour chaque traitement contenant par exemple des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ad hoc, des appels de procédures stockées et des appels de fonctions définies par l'utilisateur.<br /><br /> Colonne acceptant la valeur NULL.|  

## <a name="remarks"></a>Notes  
Les mêmes remarques dans [sys. dm_exec_text_query_plan](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql?view=sql-server-ver15) s’appliquent.  

## <a name="permissions"></a>Autorisations  
 Exiger un rôle de serveur **sysadmin** ou une `VIEW SERVER STATE` autorisation sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Étapes suivantes
 Pour obtenir des conseils supplémentaires en matière de développement, consultez l’article [Vue d’ensemble sur le développement SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).