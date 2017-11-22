---
title: Sys.index_resumable_operations (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.reviewer: 
ms.service: 
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.index_resumable_operations_TSQL
- sys.indexes_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.indexes
- sys.index_resumable_operations
ms.assetid: 
caps.latest.revision: "1"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb2d574822922598524458e9e5a5fe45638a178e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="indexresumableoperations-transact-sql"></a>index_resumable_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**Sys.index_resumable_operations** est une vue système qui surveille et vérifie l’état d’exécution actuel pour la reconstruction d’Index peut être reprise.  
**S’applique à**: SQL Server 2017 et Azure SQL Database 
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID de l’objet auquel cet index appartient (pas de valeur nulle).|  
|**index_id**|**int**|ID de l’index (pas de valeur nulle). **index_id** est unique que dans l’objet.|
|**nom**|**sysname**|Nom de l’index. **nom** est unique que dans l’objet.|  
|**sql_text**|**nvarchar(max)**|Texte de l’instruction DDL T-SQL|
|**last_max_dop**|**smallint**|La dernière MAX_DOP utilisé (par défaut = 0)|
|**partition_number**|**int**|Numéro de partition dans l’index ou le segment de mémoire propriétaire. Pour les index et les tables non partitionnées ou dans le cas de toutes les partitions sont en cours régénération de la valeur de cette colonne est NULL.|
|**état**|**tinyint**|État opérationnel de l’index peut être repris :<br /><br />0 = en cours d’exécution<br /><br />1 = pause|
|**state_desc**|**nvarchar (60)**|Description de l’état opérationnel d’index peut être repris (en cours d’exécution ou suspendu)|  
|**heure_début**|**datetime**|Heure de début d’une opération de index (pas de valeur nulle)|
|**last_pause_time**|**DateTime**| Opération d’index dernier temps de pause (null). NULL si l’opération est en cours d’exécution et jamais en pause.|
|**total_execution_time**|**int**|Temps total d’exécution à partir de l’heure de début en minutes (pas de valeur nulle)|
|**percent_complete**|**real**|Achèvement dans % (pas de valeur nulle) la progression de l’opération d’index.|
|**page_count**|**bigint**|Nombre total de pages d’index allouées par l’opération de création d’index de la nouvelle et les index de mappage (pas de valeur nulle). 

## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
   
## <a name="example"></a>Exemple  
 Liste de toutes les opérations de reconstruction d’index peut être repris qui se trouvent dans l’état PAUSE. 
  
```  
SELECT * FROM  sys.index_resumable_operations WHERE STATE = 1;  
```  
  
## <a name="see-also"></a>Voir aussi 
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)    
 [Affichages catalogue &#40; Transact-SQL &#41; ](catalog-views-transact-sql.md) [Objet affichages catalogue &#40; Transact-SQL &#41; ](object-catalog-views-transact-sql.md) [sys.indexes &#40; Transact-SQL &#41; ](sys-xml-indexes-transact-sql.md) [sys.index_columns &#40; Transact-SQL &#41;](sys-index-columns-transact-sql.md)   
 [Sys.xml_indexes &#40; Transact-SQL &#41;](sys-xml-indexes-transact-sql.md)   
 [Sys.Objects &#40; Transact-SQL &#41;](sys-index-columns-transact-sql.md)   
 [Sys.key_constraints &#40; Transact-SQL &#41;](sys-key-constraints-transact-sql.md)   
 [Sys.FileGroups &#40; Transact-SQL &#41;](sys-filegroups-transact-sql.md)   
 [Sys.partition_schemes &#40; Transact-SQL &#41;](sys-partition-schemes-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](querying-the-sql-server-system-catalog-faq.md)   
  
