---
title: sys.dm_exec_distributed_requests (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 539bf6f6e4df5860977fdd0703a9bc11a5923d31
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecdistributedrequests-transact-sql"></a>sys.dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les demandes récemment ou actuellement actives dans les requêtes PolyBase. Il répertorie une ligne par/requête de la demande.  
  
 Basé sur session et demander des ID, un utilisateur peut ensuite extraire les requêtes distribuées réels générées de façon à être exécutées – via sys.dm_exec_distributed_requests. Par exemple, une requête impliquant une régulier SQL et les tables SQL externes sera être décomposée en différentes instructions/requêtes exécutées sur les différents nœuds de calcul. Pour suivre les étapes distribuées à tous les nœuds de calcul, nous introduisons un ID d’exécution 'global' qui peut être utilisé pour effectuer le suivi de toutes les opérations sur les nœuds de calcul associés à une demande particulière et opérateur, respectivement.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|Clé pour cette vue. Id numérique unique associé à la demande.|Le point d’entrée unique pour toutes les demandes dans le système.|  
|execution_id|**nvarchar(32**|Id numérique unique associé à la session dans laquelle cette requête a été exécutée.||  
|status|**nvarchar(32**|État actuel de la demande.|'Pending', 'Authorizing', 'AcquireSystemResources', 'Initializing', 'Plan', 'Parsing', 'AquireResources', 'Running', 'Cancelling', 'Complete', 'Failed', 'Cancelled'.|  
|error_id|**nvarchar(36)**|Id unique de l’erreur associée à la demande, le cas échéant.|La valeur NULL si aucune erreur ne s’est produite.|  
|start_time|**datetime**|Heure de début de l’exécution de la demande.|0 pour les demandes en file d’attente ; Sinon, valide datetime inférieure ou égale à l’heure actuelle.|  
|end_time|**datetime**|Heure à laquelle le moteur a terminé la compilation de la demande.|NULL pour les demandes en file d’attente ou actives ; Sinon, une dateheure valide inférieure ou égale à l’heure actuelle.|  
|total_elapsed_time|**int**|Temps écoulé dans l’exécution, car la requête a été lancée, en millisecondes.|Comprise entre 0 et la différence entre start_time et heure_fin. Si total_elapsed_time dépasse la valeur maximale pour un entier, total_elapsed_time continueront à être la valeur maximale. Cette condition génère l’avertissement « la valeur maximale a été dépassée. » La valeur maximale, en millisecondes est équivalente à 24.8 jours.|  
  
## <a name="see-also"></a>Voir aussi  
 [PolyBase, résolution des problèmes avec les vues de gestion dynamique](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Base de données associés des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
