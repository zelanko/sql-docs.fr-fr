---
title: Sys.dm_clr_tasks (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_tasks
- sys.dm_clr_tasks_TSQL
- dm_clr_tasks
- dm_clr_tasks_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_clr_tasks dynamic management view
ms.assetid: 462b9061-09fa-4858-9707-03d6cc19c769
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 45aad56182dd79b9b5787e78964b23d7469344d0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmclrtasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour toutes les tâches CLR (Common Language Runtime) en cours d'exécution. Un traitement [!INCLUDE[tsql](../../includes/tsql-md.md)] qui contient une référence à une routine CLR crée une tâche distincte pour exécuter l'ensemble du code managé de ce traitement. Les diverses instructions du traitement qui nécessitent l'exécution de code managé utilisent la même tâche CLR. Cette tâche CLR est chargée de tenir à jour les objets et les états liés à l'exécution du code managé, mais aussi les transitions entre l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le CLR.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary (8)**|Adresse de la tâche CLR.|  
|**sos_task_address**|**varbinary (8)**|Adresse de la tâche du traitement [!INCLUDE[tsql](../../includes/tsql-md.md)] sous-jacent.|  
|**appdomain_address**|**varbinary (8)**|Adresse du domaine d'application dans lequel cette tâche s'exécute.|  
|**état**|**nvarchar (128)**|État actuel de la tâche.|  
|**abort_state**|**nvarchar (128)**|État actuel de la procédure d'annulation (si la tâche a été annulée). L'abandon d'une tâche passe par plusieurs états.|  
|**type**|**nvarchar (128)**|Type de tâche.|  
|**affinity_count**|**int**|Affinité de la tâche.|  
|**forced_yield_count**|**int**|Nombre de fois où la tâche a dû être abandonnée.|  
  
## <a name="permissions"></a>Permissions  
 Sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert l’autorisation VIEW SERVER STATE sur le serveur.  
  
 Sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] niveaux Premium requiert l’autorisation VIEW DATABASE STATE dans la base de données. Sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard et les niveaux de base nécessite le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] compte d’administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Common Language Runtime relatives des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

