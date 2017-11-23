---
title: Sys.dm_pdw_diag_processing_stats (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 05dc9dc5854b970dd97227672f5f75eecbb34718
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>Sys.dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Affiche des informations relatives à tous les événements de diagnostic internes qui peut être incorporés dans des sessions de diagnostic définies par l’administrateur. Interroger cette vue pour comprendre les statistiques derrière les sous-systèmes de gestion des événements et de diagnostic que le remplissage de toutes les autres vues DMV le lecteur. Il existe un groupe de files d’attente pour chaque processus sur chaque nœud.  
  
|Nom de la colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Nœud d’équipement que provient ce journal.|  
|**ID de processus**|**int**|Identificateur du processus en cours d’exécution soumettant cette statistique.|  
|**target_name**|**nvarchar(255)**|Nom de la file d'attente.|  
|**queue_size**|**int**|Le nombre d’éléments dans la file d’attente de processus. La taille de la file d’attente est généralement 0. Un nombre positif indique que le système est sous tension et qu’il est de génération d’événements. Un nombre positif dans les autres colonnes signifie système ont été endommagé pour cette file d’attente particulière et les vues DMV liées aux.|  
|**lost_events_count**|**bigint**|Le nombre d’événements perdus.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de gestion dynamique de l’entrepôt de données en parallèle &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
