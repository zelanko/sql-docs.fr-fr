---
title: Sys.dm_os_memory_cache_hash_tables (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_hash_tables_TSQL
- sys.dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_hash_tables dynamic management view
ms.assetid: 68b94f35-8f80-4d2b-bcde-7a21934219af
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d5a52fc7c614752cde43a1670f2fb299b35aa0ee
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265766"
---
# <a name="sysdmosmemorycachehashtables-transact-sql"></a>sys.dm_os_memory_cache_hash_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une ligne pour chaque cache actif dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  À appeler à partir [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_memory_cache_hash_tables**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Adresse (clé primaire) de l'entrée du cache. N'accepte pas la valeur NULL.|  
|**name**|**nvarchar (256)**|Nom du cache. N'accepte pas la valeur NULL.|  
|**type**|**nvarchar(60)**|Type de cache. N'accepte pas la valeur NULL.|  
|**table_level**|**int**|Numéro de la table de hachage. Un cache peut posséder plusieurs tables de hachage qui correspondent à différentes fonctions de hachage. N'accepte pas la valeur NULL.|  
|**buckets_count**|**int**|Nombre de compartiments dans la table de hachage. N'accepte pas la valeur NULL.|  
|**buckets_in_use_count**|**Int**|Nombre de compartiments actuellement utilisés. N'accepte pas la valeur NULL.|  
|**buckets_min_length**|**int**|Nombre minimum d'entrées de cache dans un compartiment. N'accepte pas la valeur NULL.|  
|**buckets_max_length**|**Int**|Nombre maximum d'entrées de cache dans un compartiment. N'accepte pas la valeur NULL.|  
|**buckets_avg_length**|**int**|Nombre moyen d'entrées de cache dans chaque compartiment. N'accepte pas la valeur NULL.|  
|**buckets_max_length_ever**|**int**|Nombre maximum d'entrées mises en cache dans un compartiment de cette table de hachage depuis le démarrage du serveur. N'accepte pas la valeur NULL.|  
|**hits_count**|**bigint**|Nombre d'accès au cache. N'accepte pas la valeur NULL.|  
|**misses_count**|**bigint**|Nombre des échecs du cache. N'accepte pas la valeur NULL.|  
|**buckets_avg_scan_hit_length**|**Int**|Nombre moyen d'entrées examinées dans un compartiment avant la détection de l'élément recherché. N'accepte pas la valeur NULL.|  
|**buckets_avg_scan_miss_length**|**Int**|Nombre moyen d'entrées examinées dans un compartiment avant la fin de la recherche infructueuse. N'accepte pas la valeur NULL.|  
|**pdw_node_id**|**Int**|L’identificateur pour le nœud se trouvant sur cette distribution.<br /><br /> **S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Autorisations 

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveaux Premium, nécessite le `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard et les niveaux de base, nécessite le **administrateur du serveur** ou un **administrateur Azure Active Directory** compte.   

## <a name="see-also"></a>Voir aussi  
 
  [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


