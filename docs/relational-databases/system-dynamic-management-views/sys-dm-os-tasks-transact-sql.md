---
title: sys. dm_os_tasks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_tasks
- sys.dm_os_tasks_TSQL
- dm_os_tasks_TSQL
- dm_os_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_tasks dynamic management view
ms.assetid: 180a3c41-e71b-4670-819d-85ea7ef98bac
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 086065aa79ca6fba7ad84e5b7e7f99f6f462f7dd
ms.sourcegitcommit: f018eb3caedabfcde553f9a5fc9c3e381c563f1a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164899"
---
# <a name="sysdm_os_tasks-transact-sql"></a>sys.dm_os_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une ligne pour chaque tâche active dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Une tâche est l’unité d’exécution de base dans SQL Server. Voici quelques exemples de tâches : une requête, une connexion, une déconnexion et des tâches système telles que l’activité de nettoyage des fichiers fantômes, l’activité de point de contrôle, l’enregistreur de journal, l’activité de restauration parallèle. Pour plus d’informations sur les tâches, consultez le [Guide d’architecture des threads et des tâches](../../relational-databases/thread-and-task-architecture-guide.md).
  
> [!NOTE]  
> Pour l’appeler à partir de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys. dm_pdw_nodes_os_tasks**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Adresse mémoire de l'objet.|  
|**task_state**|**nvarchar(60)**|État de la tâche. Il peut s'agir de l'un des états suivants :<br /><br /> PENDING : En attente d'un thread de travail.<br /><br /> RUNNABLE : Exécutable, mais en attente d'un quantum.<br /><br /> RUNNING : En cours d'exécution sur le planificateur.<br /><br /> SUSPENDED : Doté d'un processus de travail, mais en attente d'un événement.<br /><br /> DONE : Terminé.<br /><br /> SPINLOOP : Bloqué dans une boucle.|  
|**context_switches_count**|**int**|Nombre de commutateurs de contexte de planificateur exécutés par cette tâche.|  
|**pending_io_count**|**int**|Nombre d'E/S physiques qui sont effectuées par cette tâche.|  
|**pending_io_byte_count**|**bigint**|Nombre total d'octets d'E/S qui sont traités par cette tâche.|  
|**pending_io_byte_average**|**int**|Nombre moyen d'octets d'E/S qui sont traités par cette tâche.|  
|**scheduler_id**|**int**|ID du planificateur parent. Handle pointant vers les informations de planification associées à cette tâche. Pour plus d’informations, consultez [sys. &#40;DM_OS_SCHEDULERS Transact-&#41;SQL](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|**session_id**|**smallint**|ID de la session qui est associée à la tâche.|  
|**exec_context_id**|**int**|ID du contexte d'exécution qui est associé à la tâche.|  
|**request_id**|**int**|ID de la demande de la tâche. Pour plus d’informations, consultez [sys. &#40;DM_EXEC_REQUESTS Transact-&#41;SQL](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|**worker_address**|**varbinary(8)**|Adresse mémoire du processus de travail qui exécute la tâche.<br /><br /> NULL = La tâche est en attente d'un processus de travail pour s'exécuter ou son exécution vient de se terminer.<br /><br /> Pour plus d’informations, consultez [sys. &#40;DM_OS_WORKERS Transact-&#41;SQL](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|**host_address**|**varbinary(8)**|Adresse mémoire de l'hôte.<br /><br /> 0 = Aucun hôte n'a été utilisé pour créer la tâche. Cela permet d'identifier l'hôte utilisé pour créer cette tâche.<br /><br /> Pour plus d’informations, consultez [sys. &#40;DM_OS_HOSTS Transact-&#41;SQL](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md).|  
|**parent_task_address**|**varbinary(8)**|Adresse mémoire de la tâche qui est le parent de l'objet.|  
|**pdw_node_id**|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="permissions"></a>Autorisations
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` autorisation.   
Sur les niveaux [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium, requiert l’autorisation `VIEW DATABASE STATE` dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   

## <a name="examples"></a>Exemples  
  
### <a name="a-monitoring-parallel-requests"></a>A. Surveillance des demandes parallèles  
 Pour les requêtes exécutées en parallèle, plusieurs lignes s’affichent pour la même combinaison de (\<**session_id**>, \<**request_id**>). Utilisez la requête suivante pour trouver l' [option de configuration de serveur configurer l’option max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) pour toutes les demandes actives.  
  
> [!NOTE]  
>  Une **request_id** est unique au sein d’une session.  
  
```  
SELECT  
    task_address,  
    task_state,  
    context_switches_count,  
    pending_io_count,  
    pending_io_byte_count,  
    pending_io_byte_average,  
    scheduler_id,  
    session_id,  
    exec_context_id,  
    request_id,  
    worker_address,  
    host_address  
  FROM sys.dm_os_tasks  
  ORDER BY session_id, request_id;  
```  
  
### <a name="b-associating-session-ids-with-windows-threads"></a>B. Association d'ID de session à des threads Windows  
 Vous pouvez utiliser la requête suivante pour associer une valeur d'ID de session à un ID de thread Windows. Vous pouvez ensuite surveiller les performances du thread dans l'Analyseur de performances Windows. La requête suivante ne renvoie pas d'informations pour les sessions en veille.  
  
```  
SELECT STasks.session_id, SThreads.os_thread_id  
  FROM sys.dm_os_tasks AS STasks  
  INNER JOIN sys.dm_os_threads AS SThreads  
    ON STasks.worker_address = SThreads.worker_address  
  WHERE STasks.session_id IS NOT NULL  
  ORDER BY STasks.session_id;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
[SQL Server les &#40;vues de gestion dynamique liées au système d'&#41; exploitation   Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
[Guide d’architecture de thread et de tâche](../../relational-databases/thread-and-task-architecture-guide.md)     
  


