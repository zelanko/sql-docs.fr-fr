---
title: syscollector_execution_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: bca1d879c0988ffb48eb5ae2fd080b1133e24339
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060329"
---
# <a name="syscollector_execution_stats-transact-sql"></a>syscollector_execution_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur l'exécution d'une tâche pour un jeu d'éléments de collecte ou package.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**log_id**|**bigint**|Identifie chaque exécution de jeu d'éléments de collecte. Utilisé pour joindre cette vue à d'autres journaux détaillés. N'accepte pas la valeur NULL.|  
|**task_name**|**nvarchar(128)**|Nom de la tâche du jeu d'éléments de collecte ou package à laquelle ces informations sont destinées. N'accepte pas la valeur NULL.|  
|**execution_row_count_in**|**int**|Nombre de lignes traitées au début du flux de données. Autorise la valeur NULL.|  
|**execution_row_count_out**|**int**|Nombre de lignes traitées à la fin du flux de données. Autorise la valeur NULL.|  
|**execution_row_count_errors**|**int**|Nombre de lignes qui ont échoué pendant le flux de données. Autorise la valeur NULL.|  
|**execution_time_ms**|**int**|Intervalle de temps, en millisecondes, requis pour que la tâche se termine. Autorise la valeur NULL.|  
|**log_time**|**DATETIME**|Heure d'enregistrement de ces informations. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation SELECT pour **dc_operator**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Vues du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)  
  
  
