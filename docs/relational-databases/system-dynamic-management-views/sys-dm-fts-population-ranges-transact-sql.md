---
title: Sys.dm_fts_population_ranges (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_population_ranges
- sys.dm_fts_population_ranges_TSQL
- dm_fts_population_ranges_TSQL
- dm_fts_population_ranges
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_population_ranges dynamic management view
ms.assetid: 58d8564b-9c43-4965-a31c-2893890334ef
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 78b1e3850f9d1b009bd32d8e43a7c5e20e2af85f
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmftspopulationranges-transact-sql"></a>sys.dm_fts_population_ranges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les plages spécifiques liées au remplissage en cours de l'index de recherche en texte intégral.  
   
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**memory_address**|**varbinary(8)**|Adresse des mémoires tampon allouées pour une activité liée à cette sous-plage d'un remplissage d'index de texte intégral.|  
|**parent_memory_address**|**varbinary(8)**|Adresse des mémoires tampon représentant l'objet parent de toutes les plages d'un remplissage lié à un index de texte intégral.|  
|**is_retry**|**bit**|Si la valeur est 1, cette sous-plage est chargée de récupérer les lignes qui ont rencontré des erreurs.|  
|**session_id**|**smallint**|ID de la session qui est en train de traiter cette tâche.|  
|**processed_row_count**|**int**|Nombre de lignes qui ont été traitées par cette plage. La progression vers l'avant est persistante et comptée toutes les 5 minutes, et non à chaque validation de lot.|  
|**error_count**|**int**|Nombre de lignes qui ont rencontré des erreurs par cette plage. La progression vers l'avant est persistante et comptée toutes les 5 minutes, et non à chaque validation de lot.|  
  
## <a name="permissions"></a>Autorisations  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   
 
## <a name="physical-joins"></a>Jointures physiques  
 ![Jointures significatives de cette vue de gestion dynamique](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-population-ranges-1.gif "jointures significatives de cette vue de gestion dynamique")  
  
## <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|From|Pour|Relation|  
|----------|--------|------------------|  
|dm_fts_population_ranges.parent_memory_address|dm_fts_index_population.memory_address|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
  [Recherche en texte intégral et les fonctions et vues de gestion dynamique de la recherche sémantique &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

