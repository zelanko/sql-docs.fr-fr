---
title: sys. dm_exec_distributed_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_REQUESTS
- DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- sys.dm_exec_distributed_sql_requests management view
- PolyBase
- dm_exec_distributed_sql_requests management view
ms.assetid: c041d416-d8c6-435e-a563-6a310abd33e3
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 37fd17f17d8b6aa1a30f48d75258d27f4a45561a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68097804"
---
# <a name="sysdm_exec_distributed_requests-transact-sql"></a>sys. dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les demandes actuellement ou récemment actives dans les requêtes Polybase. Elle répertorie une ligne par requête/requête.  
  
 En fonction de l’ID de session et de demande, un utilisateur peut récupérer les requêtes distribuées réelles générées pour être exécutées, via sys. dm_exec_distributed_requests. Par exemple, une requête impliquant des tables SQL et SQL externes régulières sera décomposée en différentes instructions/demandes exécutées sur les différents nœuds de calcul. Pour suivre les étapes distribuées sur tous les nœuds de calcul, nous introduisons un ID d’exécution « global » qui peut être utilisé pour effectuer le suivi de toutes les opérations sur les nœuds de calcul associés à une requête et un opérateur particuliers, respectivement.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|Clé pour cette vue. ID numérique unique associé à la demande.|Unique pour toutes les demandes dans le système.|  
|execution_id|**nvarchar (32**|ID numérique unique associé à la session dans laquelle cette requête a été exécutée.||  
|status|**nvarchar (32**|État actuel de la demande.|« Pending », « Authorization », « AcquireSystemResources », « Initialize », « plan », « Analysis », « AquireResources », « Running », « Canceling », « Completed », « failed », « Cancelled ».|  
|error_id|**nvarchar (36)**|ID unique de l’erreur associée à la demande, le cas échéant.|Affectez la valeur NULL si aucune erreur ne s’est produite.|  
|start_time|**datetime**|Heure à laquelle l’exécution de la requête a été démarrée.|0 pour les demandes mises en file d’attente ; dans le cas contraire, la valeur DateTime valide est inférieure ou égale à l’heure actuelle.|  
|end_time|**datetime**|Heure à laquelle le moteur a terminé la compilation de la requête.|NULL pour les demandes en file d’attente ou actives ; dans le cas contraire, un DateTime valide est plus petit ou égal à l’heure actuelle.|  
|total_elapsed_time|**int**|Temps écoulé durant l’exécution depuis le début de la demande, en millisecondes.|Entre 0 et la différence entre start_time et end_time. Si total_elapsed_time dépasse la valeur maximale d’un entier, total_elapsed_time sera toujours la valeur maximale. Cette condition génère l’avertissement « la valeur maximale a été dépassée ». La valeur maximale en millisecondes est équivalente à 24,8 jours.|  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de Polybase avec les vues de gestion dynamique](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Vues et fonctions de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à la base de données &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
