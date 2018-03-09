---
title: sys.dm_db_fts_index_physical_stats (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_fts_index_physical_stats_TSQL
- dm_db_fts_index_physical_stats
- dm_db_fts_index_physical_stats_TSQL
- sys.dm_db_fts_index_physical_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_fts_index_physical_stats dynamic management view
ms.assetid: 997c3278-3630-47f6-ada3-190b6c16ce0e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c0d5bca8b85d6c0a86768ddd002f37358530affe
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdbftsindexphysicalstats-transact-sql"></a>sys.dm_db_fts_index_physical_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque index sémantique ou de recherche en texte intégral dans chaque table associée à un index sémantique ou de recherche en texte intégral.  
  
||||  
|-|-|-|  
|**Nom de colonne**|**Type**|**Description**|  
|**object_id**|int|ID d'objet de la table qui contient l'index.|  
|**fulltext_index_page_count**|**bigint**|Taille logique de l'extraction, en nombre de pages d'index.|  
|**keyphrase_index_page_count**|**bigint**|Taille logique de l'extraction, en nombre de pages d'index.|  
|**similarity_index_page_count**|**bigint**|Taille logique de l'extraction, en nombre de pages d'index.|  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Pour plus d’informations, consultez [gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md).  
  
## <a name="metadata"></a>Métadonnées  
 Pour plus d'informations sur l'état d'indexation sémantique, interrogez les vues de gestion dynamique suivantes :  
  
-   [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="permissions"></a>Autorisations  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveaux Premium, nécessite le `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard et les niveaux de base, nécessite le **administrateur du serveur** ou **administrateur Active Directory de Azure** compte.  

  
## <a name="examples"></a>Exemples  
 L'exemple suivant indique comment interroger la taille logique de chaque index sémantique ou de recherche en texte intégral dans chaque table associée à un index sémantique ou de recherche en texte intégral :  
  
```  
SELECT * FROM sys.dm_db_fts_index_physical_stats;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
