---
title: syscollector_execution_stats (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syscollector_execution_stats
- syscollector_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscollector_execution_stats view
- data collector view
ms.assetid: 23e35ac5-fbbf-4922-970c-f4fac44c1263
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e08a724fa5186a6615a73bb288e6005b40b8f5a3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="syscollectorexecutionstats-transact-sql"></a>syscollector_execution_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur l'exécution d'une tâche pour un jeu d'éléments de collecte ou package.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**log_id**|**bigint**|Identifie chaque exécution de jeu d'éléments de collecte. Utilisé pour joindre cette vue à d'autres journaux détaillés. N'accepte pas la valeur NULL.|  
|**nom_tâche**|**nvarchar(128)**|Nom de la tâche du jeu d'éléments de collecte ou package à laquelle ces informations sont destinées. N'accepte pas la valeur NULL.|  
|**execution_row_count_in**|**int**|Nombre de lignes traitées au début du flux de données. Autorise la valeur NULL.|  
|**execution_row_count_out**|**int**|Nombre de lignes traitées à la fin du flux de données. Autorise la valeur NULL.|  
|**execution_row_count_errors**|**int**|Nombre de lignes qui ont échoué pendant le flux de données. Autorise la valeur NULL.|  
|**execution_time_ms**|**int**|Intervalle de temps, en millisecondes, requis pour que la tâche se termine. Autorise la valeur NULL.|  
|**log_time**|**datetime**|Heure d'enregistrement de ces informations. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l’autorisation SELECT pour **dc_operator**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Vues du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)  
  
  
