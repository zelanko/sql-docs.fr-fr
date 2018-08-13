---
title: Sys.dm_exec_background_job_queue (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_background_job_queue
- sys.dm_exec_background_job_queue_TSQL
- dm_exec_background_job_queue_TSQL
- sys.dm_exec_background_job_queue
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_background_job_queue dynamic management function
ms.assetid: 05d9884f-b74c-4e3c-a23b-c90c1ea5ef02
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 6b04f500b1603df57eace3b2d58fb158bda3f945
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39550539"
---
# <a name="sysdmexecbackgroundjobqueue-transact-sql"></a>sys.dm_exec_background_job_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une ligne pour chaque travail du processeur de requêtes qui est planifié pour s'exécuter de façon asynchrone (en arrière-plan).  
  
> **REMARQUE** À appeler à partir **[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]** ou **[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]**, utilisez le nom **sys.dm_pdw_nodes_exec_background_job_queue**.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**time_queued**|**datetime**|Moment auquel le travail a été ajouté à la file d'attente.|  
|**job_id**|**Int**|Identificateur du travail.|  
|**database_id**|**Int**|Base de données sur laquelle le travail doit s'exécuter.|  
|**object_id1**|**Int**|Cette valeur dépend du type de travail. Pour plus d'informations, consultez la section Notes.|  
|**object_id2**|**Int**|Cette valeur dépend du type de travail. Pour plus d'informations, consultez la section Notes.|  
|**object_id3**|**Int**|Cette valeur dépend du type de travail. Pour plus d'informations, consultez la section Notes.|  
|**object_id4**|**Int**|Cette valeur dépend du type de travail. Pour plus d'informations, consultez la section Notes.|  
|**error_code**|**Int**|Code d'erreur si le travail a été réinséré à cause d'une erreur. NULL si le travail a été suspendu, n'a pas été récupéré ou est terminé.|  
|**request_type**|**smallint**|Type de demande du travail.|  
|**retry_count**|**smallint**|Nombre de fois où le travail a été récupéré et réinséré dans la file d'attente pour cause de manque de ressources ou pour d'autres raisons.|  
|**in_progress**|**smallint**|Indique si l'exécution du travail a commencé.<br /><br /> 1 = Démarré<br /><br /> 0 = en attente|  
|**session_id**|**smallint**|Identificateur de la session.|  
|**pdw_node_id**|**Int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
## <a name="permissions"></a>Permissions

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   
  
## <a name="remarks"></a>Notes  
 Seules les informations pour les travaux de mise à jour des statistiques asynchrone apparaissent dans cette vue. Pour plus d’informations sur la mise à jour asynchrone des statistiques, consultez [statistiques](../../relational-databases/statistics/statistics.md).  
  
 Les valeurs de **object_id1** via **object_id4** varient selon le type de la demande de travail. Le tableau suivant récapitule la signification de ces colonnes pour différents types de travaux.  
  
|Type de demande|object_id1|object_id2|object_id3|object_id4|  
|------------------|-----------------|-----------------|-----------------|-----------------|  
|Statistiques de mises à jour asynchrones|Identificateur de table ou de vue|Identificateur de statistiques|Non utilisée|Non utilisée|  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne le nombre de travaux asynchrones actifs dans la file d'attente en arrière plan pour chaque base de données dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT DB_NAME(database_id) AS [Database], COUNT(*) AS [Active Async Jobs]  
FROM sys.dm_exec_background_job_queue  
WHERE in_progress = 1  
GROUP BY database_id;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique liées à l’exécution &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Statistiques](../../relational-databases/statistics/statistics.md)   
 [KILL STATS JOB &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-stats-job-transact-sql.md)  
  
  



