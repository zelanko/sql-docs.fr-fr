---
title: Sys.index_resumable_operations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.index_resumable_operations_TSQL
- sys.indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes
- sys.index_resumable_operations
ms.assetid: ''
caps.latest.revision: 1
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 47ce09f820c979f059d5c5f4bad40304ca7a591d
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555419"
---
# <a name="indexresumableoperations-transact-sql"></a>index_resumable_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**Sys.index_resumable_operations** est une vue système qui surveille et vérifie l’état d’exécution actuel pour la reconstruction d’Index pouvant être reprise.  
**S’applique à**: SQL Server 2017 et Azure SQL Database 
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|ID de l’objet auquel cet index appartient (qui n’autorise pas la valeur null).|  
|**index_id**|**Int**|ID de l’index (qui n’autorise pas la valeur null). **index_id** est unique seulement dans l’objet.|
|**nom**|**sysname**|Nom de l’index. **nom** est unique seulement dans l’objet.|  
|**sql_text**|**nvarchar(max)**|Texte de l’instruction DDL T-SQL|
|**last_max_dop**|**smallint**|Dernière MAX_DOP utilisé (par défaut = 0)|
|**partition_number**|**Int**|Numéro de partition dans l’index ou le segment de mémoire propriétaire. Pour les tables non partitionnées et ou dans les cas toutes les partitions sont en cours de reconstruction de la valeur de cette colonne est NULL.|
|**state**|**tinyint**|État opérationnel pour les index pouvant être reprise :<br /><br />0 = en cours d’exécution<br /><br />1 = pause|
|**state_desc**|**nvarchar(60)**|Description de l’état opérationnel pour les index pouvant être reprise (en cours d’exécution ou suspendu)|  
|**start_time**|**datetime**|Heure de début d’une opération de index (qui n’autorise pas la valeur null)|
|**last_pause_time**|**datatime**| Opération d’index dernier temps de pause (null). NULL si l’opération est en cours d’exécution et ne sont jamais mise en pause.|
|**total_execution_time**|**Int**|Durée d’exécution totale à partir de l’heure de début en quelques minutes (qui n’autorise pas la valeur null)|
|**percent_complete**|**real**|Index de fin progression de l’opération dans % (pas de valeur nulle).|
|**page_count**|**bigint**|Nombre total de pages d’index allouées par l’opération de génération d’index pour le nouveau et les index de mappage (qui n’autorise pas la valeur null). 

## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
   
## <a name="example"></a>Exemple  
 Répertorier toutes les opérations de reconstruction d’index pouvant être reprise qui se trouvent dans l’état PAUSE. 
  
```  
SELECT * FROM  sys.index_resumable_operations WHERE STATE = 1;  
```  
  
## <a name="see-also"></a>Voir aussi 
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)    
 [Affichages catalogue &#40;Transact-SQL&#41; ](catalog-views-transact-sql.md) [affichages catalogue de l’objet &#40;Transact-SQL&#41; ](object-catalog-views-transact-sql.md) [sys.indexes &#40;Transact-SQL&#41; ](sys-xml-indexes-transact-sql.md) [sys.index_columns &#40;Transact-SQL&#41;](sys-index-columns-transact-sql.md)   
 [sys.xml_indexes &#40;Transact-SQL&#41;](sys-xml-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](sys-index-columns-transact-sql.md)   
 [sys.key_constraints &#40;Transact-SQL&#41;](sys-key-constraints-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](sys-filegroups-transact-sql.md)   
 [sys.partition_schemes &#40;Transact-SQL&#41;](sys-partition-schemes-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](querying-the-sql-server-system-catalog-faq.md)   
  
