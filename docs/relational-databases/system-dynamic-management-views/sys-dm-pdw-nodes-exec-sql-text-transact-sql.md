---
title: sys. DM _pdw_nodes_exec_sql_text (Transact-SQL) | Microsoft Docs
description: Vue de gestion dynamique qui retourne le texte du lot SQL identifié par le sql_handle spécifié.
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
ms.openlocfilehash: fd886217b2fb2caf0fe3f32e88b7bf0215ece1a9
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145674"
---
# <a name="syspdw_nodes_dm_exec_sql_text-transact-sql"></a>sys. PDW _nodes_dm_exec_sql_text (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Retourne le texte du lot SQL identifié par le *sql_handle*spécifié. Cette fonction à valeur de table remplace la fonction système **fn_get_sql**.  
   
## <a name="table-returned"></a>Table retournée  
|Nom de colonne|Data type|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**Int**|ID numérique unique associé au nœud.|
|**dbid**|**smallint**|ID de la base de données.<br /><br /> Pour les instructions SQL non planifiées et préparées, ID de la base de données dans laquelle les instructions ont été compilées.|  
|**objectid**|**Int**|ID de l’objet.<br /><br /> Est NULL pour les instructions SQL ad hoc et préparées.|  
|**nombre**|**smallint**|Pour une procédure stockée numérotée, cette colonne retourne le numéro de la procédure stockée. Pour plus d’informations, consultez [sys. &#40;NUMBERED_PROCEDURES Transact-&#41;SQL](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md).<br /><br /> Est NULL pour les instructions SQL ad hoc et préparées.|  
|**chiffrées**|**bit**|1 : le texte SQL est chiffré.<br /><br /> 0 : le texte SQL n’est pas chiffré.|  
|**texte**|**nvarchar(max)**|Texte de la requête SQL.<br /><br /> NULL pour les objets chiffrés.|  

## <a name="remarks"></a>Notes  
Les mêmes remarques dans [sys. DM _exec_sql_text](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql?view=sql-server-ver15) s’appliquent.  
  
## <a name="permissions"></a>Permissions  
 Exiger un rôle de serveur **sysadmin** ou `VIEW SERVER STATE` autorisation sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et Parallel Data Warehouse vues &#40;de gestion dynamique Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Étapes suivantes
 Pour obtenir d’autres conseils de développement, consultez [vue d’ensemble du développement SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).