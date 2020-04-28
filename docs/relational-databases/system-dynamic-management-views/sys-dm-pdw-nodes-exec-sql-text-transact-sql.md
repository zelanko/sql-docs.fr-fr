---
title: sys. dm_pdw_nodes_exec_sql_text (Transact-SQL) | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73145674"
---
# <a name="syspdw_nodes_dm_exec_sql_text-transact-sql"></a>sys. pdw_nodes_dm_exec_sql_text (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Retourne le texte du lot SQL identifié par le *sql_handle*spécifié. Cette fonction à valeur de table remplace la fonction système **fn_get_sql**.  
   
## <a name="table-returned"></a>Table retournée  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|ID numérique unique associé au nœud.|
|**dbid**|**smallint**|ID de la base de données.<br /><br /> Pour les instructions SQL non planifiées et préparées, ID de la base de données dans laquelle les instructions ont été compilées.|  
|**arguments**|**int**|ID de l'objet.<br /><br /> Est NULL pour les instructions SQL ad hoc et préparées.|  
|**number**|**smallint**|Pour une procédure stockée numérotée, cette colonne retourne le numéro de la procédure stockée. Pour plus d’informations, consultez [sys. numbered_procedures &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md).<br /><br /> Est NULL pour les instructions SQL ad hoc et préparées.|  
|**chiffrées**|**bit**|1 : le texte SQL est chiffré.<br /><br /> 0 : le texte SQL n’est pas chiffré.|  
|**text**|**nvarchar(max)**|Texte de la requête SQL.<br /><br /> NULL pour les objets chiffrés.|  

## <a name="remarks"></a>Notes  
Les mêmes remarques dans [sys. dm_exec_sql_text](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql?view=sql-server-ver15) s’appliquent.  
  
## <a name="permissions"></a>Autorisations  
 Exiger **sysadmin** un rôle de serveur `VIEW SERVER STATE` sysadmin ou une autorisation sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Étapes suivantes
 Pour obtenir des conseils supplémentaires en matière de développement, consultez l’article [Vue d’ensemble sur le développement SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).