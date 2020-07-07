---
title: sys. dm_os_memory_cache_hash_tables (Transact-SQL) | Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9066c297cd81689c26e0cb298271ce76526733dd
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999088"
---
# <a name="sysdm_os_memory_cache_hash_tables-transact-sql"></a>sys.dm_os_memory_cache_hash_tables (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Retourne une ligne pour chaque cache actif dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Pour appeler cette valeur à partir de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , utilisez le nom **sys. dm_pdw_nodes_os_memory_cache_hash_tables**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary (8)**|Adresse (clé primaire) de l'entrée du cache. N'accepte pas la valeur NULL.|  
|**name**|**nvarchar(256)**|Nom du cache. N'accepte pas la valeur NULL.|  
|**type**|**nvarchar(60)**|Type de cache. N'accepte pas la valeur NULL.|  
|**table_level**|**int**|Numéro de la table de hachage. Un cache peut posséder plusieurs tables de hachage qui correspondent à différentes fonctions de hachage. N'accepte pas la valeur NULL.|  
|**buckets_count**|**int**|Nombre de compartiments dans la table de hachage. N'accepte pas la valeur NULL.|  
|**buckets_in_use_count**|**int**|Nombre de compartiments actuellement utilisés. N'accepte pas la valeur NULL.|  
|**buckets_min_length**|**int**|Nombre minimum d'entrées de cache dans un compartiment. N'accepte pas la valeur NULL.|  
|**buckets_max_length**|**int**|Nombre maximum d'entrées de cache dans un compartiment. N'accepte pas la valeur NULL.|  
|**buckets_avg_length**|**int**|Nombre moyen d'entrées de cache dans chaque compartiment. N'accepte pas la valeur NULL.|  
|**buckets_max_length_ever**|**int**|Nombre maximum d'entrées mises en cache dans un compartiment de cette table de hachage depuis le démarrage du serveur. N'accepte pas la valeur NULL.|  
|**hits_count**|**bigint**|Nombre d'accès au cache. N'accepte pas la valeur NULL.|  
|**misses_count**|**bigint**|Nombre des échecs du cache. N'accepte pas la valeur NULL.|  
|**buckets_avg_scan_hit_length**|**int**|Nombre moyen d'entrées examinées dans un compartiment avant la détection de l'élément recherché. N'accepte pas la valeur NULL.|  
|**buckets_avg_scan_miss_length**|**int**|Nombre moyen d'entrées examinées dans un compartiment avant la fin de la recherche infructueuse. N'accepte pas la valeur NULL.|  
|**pdw_node_id**|**int**|Identificateur du nœud sur lequel cette distribution se trouve.<br /><br /> **S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ,[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Autorisations 

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , requiert l' `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   

## <a name="see-also"></a>Voir aussi  
 
  [SQL Server vues de gestion dynamique liées au système d’exploitation &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


