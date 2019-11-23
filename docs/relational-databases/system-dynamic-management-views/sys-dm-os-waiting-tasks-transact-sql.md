---
title: sys. dm_os_waiting_tasks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c0a89a48fa960812ee955cd3b7ecb30069161f61
ms.sourcegitcommit: aece9f7db367098fcc0c508209ba243e05547fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72260378"
---
# <a name="sysdm_os_waiting_tasks-transact-sql"></a>sys.dm_os_waiting_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie les informations sur la file d'attente des tâches en attente de certaines ressources. Pour plus d’informations sur les tâches, consultez le [Guide d’architecture des threads et des tâches](../../relational-databases/thread-and-task-architecture-guide.md).
   
> [!NOTE]  
>  Pour l’appeler à partir de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys. dm_pdw_nodes_os_waiting_tasks**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**waiting_task_address**|**varbinary(8)**|Adresse de la tâche en attente.|  
|**session_id**|**smallint**|ID de la session associée à la tâche.|  
|**exec_context_id**|**int**|ID du contexte d'exécution associé à la tâche.|  
|**wait_duration_ms**|**bigint**|Temps d'attente total de ce type d'attente (en millisecondes). Cette heure est comprise entre **signal_wait_time**.|  
|**wait_type**|**nvarchar(60)**|Nom du type d'attente.|  
|**resource_address**|**varbinary(8)**|Adresse de la ressource que la tâche attend.|  
|**blocking_task_address**|**varbinary(8)**|Tâche qui mobilise actuellement cette ressource.|  
|**blocking_session_id**|**smallint**|ID de la session qui bloque la demande. Si cette colonne est NULL, la demande n'est pas bloquée, ou les informations de session de la session bloquant la demande ne sont pas disponibles (ou ne peuvent pas être identifiées).<br /><br /> -2 = La ressource qui bloque la demande appartient à une transaction distribuée orpheline.<br /><br /> -3 = La ressource qui bloque la demande appartient à une transaction de récupération différée.<br /><br /> -4 = L'ID de session du propriétaire du verrou qui bloque la demande n'a pas pu être déterminé en raison de transitions d'état de verrou interne.|  
|**blocking_exec_context_id**|**int**|ID du contexte d'exécution de la tâche bloquante.|  
|**resource_description**|**nvarchar(3072)**|Description de la ressource actuellement mobilisée. Pour plus d'informations, consultez la liste ci-dessous.|  
|**pdw_node_id**|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="resource_description-column"></a>Colonne resource_description  
 Les valeurs possibles de la colonne resource_description sont les suivantes.  
  
 **Propriétaire de la ressource du pool de threads :**  
  
-   threadpool id=scheduler\<hex-address>  
  
 **Propriétaire de la ressource de requête parallèle :**  
  
-   exchangeEvent id={Port|Pipe}\<hex-address> WaitType=\<exchange-wait-type> nodeId=\<exchange-node-id>  
  
 **Exchange-Wait-type :**  
  
-   e_waitNone  
  
-   e_waitPipeNewRow  
  
-   e_waitPipeGetRow  
  
-   e_waitSynchronizeConsumerOpen  
  
-   e_waitPortOpen  
  
-   e_waitPortClose  
  
-   e_waitRange  
  
 **Verrouiller le propriétaire de la ressource :**  
  
-   \<type-specific-description> id=lock\<lock-hex-address> mode=\<mode> associatedObjectId=\<associated-obj-id>  
  
     **\<> de description spécifique au type peut être :**  
  
    -   Pour la base de données : databaselock Resource =\<databaselock-Resource > dbid =\<DB-ID >  
  
    -   Pour le fichier : filelock fileid =\<fichier-ID > sous-ressource =\<filelock-Resource > dbid =\<DB-ID >  
  
    -   Pour Object : objectlock lockPartition =\<Lock-partition-ID > objid =\<obj-ID > Resource =\<objectlock-Resource > dbid =\<DB-ID >  
  
    -   Pour page : PageLock fileid =\<fichier-ID > pageid =\<page-ID > dbid =\<DB-ID > Resource =\<PageLock-subressource >  
  
    -   Clé : Keylock hobtid =\<HoBT-ID > dbid =\<DB-ID >  
  
    -   Pour extent : extentlock fileid =\<fichier-ID > pageid = ID de page de\<> dbid =\<DB-ID >  
  
    -   Pour RID : ridlock fileid =\<fichier-ID > pageid = ID de page de\<> dbid =\<DB-ID >  
  
    -   Pour APPLICATION : applicationlock Hash =\<hachage > databasePrincipalId =\<Role-ID > dbid =\<DB-ID >  
  
    -   Pour les métadonnées : metadatalock Resource =\<métadonnées-Resource > ClassID =\<metadatalock-Description > dbid =\<DB-ID >  
  
    -   Pour HoBT : hobtlock hobtid =\<HoBT-ID > Resource =\<HoBT-Resource > dbid =\<DB-ID >  
  
    -   Pour ALLOCATION_UNIT : allocunitlock hobtid =\<HoBT-ID > Resource =\<Alloc-Unit-Resource > dbid =\<DB-ID >  
  
     **le mode de \<> peut être :**  
  
     Sch-S, Sch-M, S, U, X, IS, IU, IX, SIU, SIX, UIX, BU, RangeS-S, RangeS-U, RangeI-N, RangeI-S, RangeI-U, RangeI-X, RangeX-, RangeX-U, RangeX-X  
  
 **Propriétaire de la ressource externe :**  
  
-   Externalressource externe =\<Wait-type >  
  
 **Propriétaire de la ressource générique :**  
  
-   TransactionMutex TransactionInfo Workspace =\<Workspace-ID >  
  
-   Mutex  
  
-   CLRTaskJoin  
  
-   CLRMonitorEvent  
  
-   CLRRWLockEvent  
  
-   resourceWait  
  
 **Propriétaire de la ressource de verrou :**  
  
-   \<db-id>:\<file-id>:\<page-in-file>  
  
-   GUID de \<>  
  
-   \<latch-class> (\<latch-address>)  
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` autorisation.   
Sur les niveaux [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium, requiert l’autorisation `VIEW DATABASE STATE` dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   
 
## <a name="example"></a>Exemple
Cet exemple identifie les sessions bloquées. Exécutez la requête [!INCLUDE[tsql](../../includes/tsql-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

```sql
SELECT * FROM sys.dm_os_waiting_tasks 
WHERE blocking_session_id IS NOT NULL; 
``` 
  
## <a name="see-also"></a>Voir aussi  
[SQL Server les &#40;vues de gestion dynamique liées au système d'&#41; exploitation     Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
[Guide d’architecture de thread et de tâche](../../relational-databases/thread-and-task-architecture-guide.md)     
   
 
