---
title: sys.dm_fts_semantic_similarity_population (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_semantic_similarity_population_TSQL
- sys.dm_fts_semantic_similarity_population
- dm_fts_semantic_similarity_population
- sys.dm_fts_semantic_similarity_population_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_semantic_similarity_population dynamic management view
ms.assetid: 33666f28-c370-47e2-a932-190316ed5f69
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: baeb646853294266e4dbca2a649236e1046ffa1f
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65947168"
---
# <a name="sysdmftssemanticsimilaritypopulation-transact-sql"></a>sys.dm_fts_semantic_similarity_population (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne d'informations d'état à propos du remplissage de l'index de ressemblance de document pour chaque index de ressemblance de chaque table associée à un index sémantique.  
  
 L'étape de remplissage suit l'étape d'extraction. Pour plus d’informations d’état d’extraction de ressemblance, consultez [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md).  
    
||||  
|-|-|-|  
|**Nom de colonne**|**Type**|**Description**|  
|**database_id**|**Int**|ID de la base de données qui contient l'index de texte intégral en cours de remplissage.|  
|**catalog_id**|**Int**|ID du catalogue de texte intégral qui contient cet index de texte intégral.|  
|**table_id**|**Int**|ID de la table pour laquelle l'index de recherche en texte intégral est rempli.|  
|**document_count**|**Int**|Nombre de documents totaux dans le remplissage|  
|**document_processed_count**|**Int**|Nombre de documents traités depuis le démarrage de ce cycle de remplissage|  
|**completion_type**|**Int**|État de la manière dont ce remplissage s'est terminé.|  
|**completion_type_description**|**nvarchar(120)**|Description du type d'achèvement.|  
|**worker_count**|**Int**|Nombre de threads de travail associés à l'extraction de ressemblance|  
|**status**|**Int**|État de ce remplissage. Remarque : certains états sont transitoires. Il peut s'agir :<br /><br /> 3 = Démarrage<br /><br /> 5 = Traitement normal<br /><br /> 7 = A arrêté le traitement<br /><br /> 11 = Remplissage abandonné|  
|**status_description**|**nvarchar(120)**|Description de l'état du remplissage.|  
|**start_time**|**datetime**|Heure de début du remplissage.|  
|**incremental_timestamp**|**timestamp**|Représente le cachet temporel de départ d'un remplissage complet. Pour tous les autres types de remplissage, cette valeur est le dernier point de contrôle validé représentant la progression des remplissages.|  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Pour plus d’informations, consultez [gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md).  
  
## <a name="metadata"></a>Métadonnées  
 Pour plus d’informations sur l’état de l’indexation sémantique, interrogez [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant indique comment interroger l'état de remplissage des index de ressemblance de documents pour toutes les tables qui sont associées à un index sémantique :  
  
```  
SELECT * FROM sys.dm_fts_semantic_similarity_population;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
