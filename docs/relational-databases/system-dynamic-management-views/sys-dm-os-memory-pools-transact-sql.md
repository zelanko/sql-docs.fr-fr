---
title: sys.dm_os_memory_pools (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_pools_TSQL
- dm_os_memory_pools
- dm_os_memory_pools_TSQL
- sys.dm_os_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_pools dynamic management view
ms.assetid: 1ef053f3-c6f3-456e-82b6-26e4bd630d46
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dbd5ce36c9d83eb6347bcba71c26c3fd71c4513d
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265737"
---
# <a name="sysdmosmemorypools-transact-sql"></a>sys.dm_os_memory_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une ligne pour chaque objet stocké dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez utiliser cet vue pour surveiller l'utilisation de la mémoire cache et pour identifier les comportements de mise en cache incorrects.  
  
> [!NOTE]  
>  À appeler à partir [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_memory_pools**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**memory_pool_address**|**varbinary(8)**|Adresse mémoire de l'entrée qui représente le pool de mémoire. N'accepte pas la valeur NULL.|  
|**pool_id**|**int**|Identificateur d'un pool spécifique au sein d'un ensemble de pools. N'accepte pas la valeur NULL.|  
|**type**|**nvarchar(60)**|Type de pool d'objets. N'accepte pas la valeur NULL. Pour plus d’informations, consultez [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**name**|**nvarchar (256)**|Nom affecté par le système à cet objet de mémoire. N'accepte pas la valeur NULL.|  
|**max_free_entries_count**|**bigint**|Nombre maximum d'entrées libres possibles dans un pool. N'accepte pas la valeur NULL.|  
|**free_entries_count**|**bigint**|Nombre d'entrées actuellement stockées dans le pool. N'accepte pas la valeur NULL.|  
|**removed_in_all_rounds_count**|**bigint**|Nombre d'entrées supprimées du pool depuis le démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. N'accepte pas la valeur NULL.|  
|**pdw_node_id**|**Int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveaux Premium, nécessite le `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard et les niveaux de base, nécessite le **administrateur du serveur** ou un **administrateur Azure Active Directory** compte.   

## <a name="remarks"></a>Notes  
 Les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent parfois une structure de pools commune pour mettre en mémoire cache des types de données homogènes sans état (stateless). La structure des pools de mémoire est plus simple que celle des mémoires cache. Toutes les entrées des pools sont considérées égales. En interne, les pools sont des régisseurs de mémoire et peuvent être utilisés dans les mêmes situations.  
  
## <a name="see-also"></a>Voir aussi  
 
  [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


