---
title: sys.dm_os_waiting_tasks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_waiting_tasks
- sys.dm_os_waiting_tasks_TSQL
- dm_os_waiting_tasks_TSQL
- sys.dm_os_waiting_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_waiting_tasks dynamic management view
ms.assetid: ca5e6844-368c-42e2-b187-6e5f5afc8df3
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9c21fa8cd03079695ddc8b94e9b2dc2ab105b2b5
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmoswaitingtasks-transact-sql"></a>sys.dm_os_waiting_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie les informations sur la file d'attente des tâches en attente de certaines ressources.  
  
> [!NOTE]  
>  Pour appeler cette de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_waiting_tasks**.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**waiting_task_address**|**varbinary(8)**|Adresse de la tâche en attente.|  
|**session_id**|**smallint**|ID de la session associée à la tâche.|  
|**exec_context_id**|**int**|ID du contexte d'exécution associé à la tâche.|  
|**wait_duration_ms**|**bigint**|Temps d'attente total de ce type d'attente (en millisecondes). Ce temps **signal_wait_time**.|  
|**wait_type**|**nvarchar(60)**|Nom du type d'attente.|  
|**resource_address**|**varbinary(8)**|Adresse de la ressource que la tâche attend.|  
|**blocking_task_address**|**varbinary(8)**|Tâche qui mobilise actuellement cette ressource.|  
|**blocking_session_id**|**smallint**|ID de la session qui bloque la demande. Si cette colonne est NULL, la demande n'est pas bloquée, ou les informations de session de la session bloquant la demande ne sont pas disponibles (ou ne peuvent pas être identifiées).<br /><br /> -2 = La ressource qui bloque la demande appartient à une transaction distribuée orpheline.<br /><br /> -3 = La ressource qui bloque la demande appartient à une transaction de récupération différée.<br /><br /> -4 = L'ID de session du propriétaire du verrou qui bloque la demande n'a pas pu être déterminé en raison de transitions d'état de verrou interne.|  
|**blocking_exec_context_id**|**int**|ID du contexte d'exécution de la tâche bloquante.|  
|**resource_description**|**nvarchar(3072)**|Description de la ressource actuellement mobilisée. Pour plus d'informations, consultez la liste ci-dessous.|  
|**pdw_node_id**|**int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur du nœud qui se trouve sur cette distribution.|  
  
## <a name="resourcedescription-column"></a>Colonne resource_description  
 La colonne resource_description a les valeurs possibles suivantes.  
  
 **Propriétaire de ressources de pool de threads :**  
  
-   threadpool id=scheduler\<hex-address>  
  
 **Propriétaire de la ressource requête parallèle :**  
  
-   exchangeEvent id={Port|Pipe}\<hex-address> WaitType=\<exchange-wait-type> nodeId=\<exchange-node-id>  
  
 **Exchange-wait-type:**  
  
-   e_waitNone  
  
-   e_waitPipeNewRow  
  
-   e_waitPipeGetRow  
  
-   e_waitSynchronizeConsumerOpen  
  
-   e_waitPortOpen  
  
-   e_waitPortClose  
  
-   e_waitRange  
  
 **Propriétaire de ressource de verrou :**  
  
-   \<type-specific-description> id=lock\<lock-hex-address> mode=\<mode> associatedObjectId=\<associated-obj-id>  
  
     **\<type-specific-description > peut être :**  
  
    -   Pour la base de données : Databaselock subresource =\<databaselock-subresource > dbid =\<db-id >  
  
    -   Pour le fichier : Filelock fileid =\<fichier-id > subresource =\<filelock-subresource > dbid =\<db-id >  
  
    -   Pour OBJECT : Objectlock lockPartition =\<lock-partition-id > objid =\<obj-id > subresource =\<objectlock-subresource > dbid =\<db-id >  
  
    -   Pour PAGE : Pagelock fileid =\<fichier-id > pageid =\<page-id > dbid =\<db-id > subresource =\<pagelock-subresource >  
  
    -   Pour Key : Keylock hobtid =\<hobt-id > dbid =\<db-id >  
  
    -   Pour EXTENT : Extentlock fileid =\<fichier-id > pageid =\<page-id > dbid =\<db-id >  
  
    -   Pour RID : Ridlock fileid =\<fichier-id > pageid =\<page-id > dbid =\<db-id >  
  
    -   Pour l’APPLICATION : Applicationlock hash =\<hash > databasePrincipalId =\<rôle-id > dbid =\<db-id >  
  
    -   Pour METADATA : Metadatalock subresource =\<métadonnées-subresource > classid =\<metadatalock-description > dbid =\<db-id >  
  
    -   Pour HOBT : Hobtlock hobtid =\<hobt-id > subresource =\<hobt-subresource > dbid =\<db-id >  
  
    -   Pour ALLOCATION_UNIT : Allocunitlock hobtid =\<hobt-id > subresource =\<alloc-unit-subresource > dbid =\<db-id >  
  
     **\<mode > peut être :**  
  
     Sch-S, Sch-M, S, U, X, IS, IU, IX, SIU, SIX, UIX, BU, RangeS-S, RangeS-U, RangeI-N, RangeI-S, RangeI-U, RangeI-X, RangeX-, RangeX-U, RangeX-X  
  
 **Propriétaire de la ressource externe :**  
  
-   Externalressource externe =\<-type d’attente >  
  
 **Propriétaire de ressource générique :**  
  
-   Espace de travail TransactionMutex TransactionInfo =\<-l’id de l’espace de travail >  
  
-   Mutex  
  
-   CLRTaskJoin  
  
-   CLRMonitorEvent  
  
-   CLRRWLockEvent  
  
-   resourceWait  
  
 **Propriétaire de ressource de verrou :**  
  
-   \<db-id>:\<file-id>:\<page-in-file>  
  
-   \<GUID>  
  
-   \<latch-class> (\<latch-address>)  
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   
 
## <a name="example"></a>Exemple
Cet exemple montre comment identifier les sessions bloquées.  Exécutez le [!INCLUDE[tsql](../../includes/tsql-md.md)] de requête dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
```sql
SELECT * FROM sys.dm_os_waiting_tasks 
WHERE blocking_session_id IS NOT NULL; 
``` 
  
## <a name="see-also"></a>Voir aussi  
  [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


