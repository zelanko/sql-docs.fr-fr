---
title: sys. dm_exec_query_resource_semaphores (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_query_resource_semaphores_TSQL
- dm_exec_query_resource_semaphores_TSQL
- sys.dm_exec_query_resource_semaphores
- dm_exec_query_resource_semaphores
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_resource_semaphores dynamic management view
ms.assetid: e43a2aa9-dd52-4c89-911e-1a7d05f7ffbb
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 026c13a461d6b4efe7244a08a9f3cdbe117deee9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68255285"
---
# <a name="sysdm_exec_query_resource_semaphores-transact-sql"></a>sys.dm_exec_query_resource_semaphores (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne les informations relatives à l'état actuel du sémaphore de ressource de requête dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **sys. dm_exec_query_resource_semaphores** fournit l’état général de la mémoire d’exécution des requêtes et vous permet de déterminer si le système peut accéder à suffisamment de mémoire. Cette vue complète les informations de mémoire obtenues à partir de [sys. dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md) pour fournir une image complète de l’état de la mémoire du serveur. **sys. dm_exec_query_resource_semaphores** retourne une ligne pour le sémaphore de ressource ordinaire et une autre ligne pour le sémaphore de ressource de petite requête. Deux conditions sont requises pour un sémaphore de petite requête :  
  
-   L’allocation de mémoire demandée doit être inférieure à 5 Mo  
  
-   Le coût de la requête doit être inférieur à 3 unités de coût  
  
> [!NOTE]  
>  Pour appeler cette valeur [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] à [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]partir de ou, utilisez le nom **sys. dm_pdw_nodes_exec_query_resource_semaphores**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**resource_semaphore_id**|**smallint**|ID non unique du sémaphore de ressource. 0 pour le sémaphore de ressource ordinaire et 1 pour le sémaphore de ressource de petites requêtes.|  
|**target_memory_kb**|**bigint**|Cible d'allocation d'utilisation en kilo-octets.|  
|**max_target_memory_kb**|**bigint**|Cible maximale potentielle en kilo-octets. NULL pour le sémaphore de ressource de petites requêtes.|  
|**total_memory_kb**|**bigint**|Mémoire détenue par le sémaphore de ressource, en kilo-octets. Si le système est soumis à une sollicitation de la mémoire ou si la mémoire minimale forcée est allouée fréquemment, cette valeur peut être supérieure à la **target_memory_kb** ou **max_target_memory_kb** valeurs. La mémoire totale est la somme de la mémoire disponible et de la mémoire allouée.|  
|**available_memory_kb**|**bigint**|Mémoire disponible pour une nouvelle allocation, en kilo-octets.|  
|**granted_memory_kb**|**bigint**|Mémoire totale allouée, en kilo-octets.|  
|**used_memory_kb**|**bigint**|Partie de la mémoire allouée utilisée physiquement, en kilo-octets.|  
|**grantee_count**|**int**|Nombre de requêtes actives dont l'allocation est satisfaite.|  
|**waiter_count**|**int**|Nombre de requêtes attendant que leur allocation soit satisfaite.|  
|**timeout_error_count**|**bigint**|Nombre total d'erreurs de dépassement de délai d'attente depuis le démarrage du serveur. NULL pour le sémaphore de ressource de petites requêtes.|  
|**forced_grant_count**|**bigint**|Nombre total d'allocations de mémoire minimale forcées depuis le démarrage du serveur. NULL pour le sémaphore de ressource de petites requêtes.|  
|**pool_id**|**int**|ID du pool de ressources auquel ce sémaphore de ressource appartient.|  
|**pdw_node_id**|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="permissions"></a>Autorisations  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` l’autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   
  
## <a name="remarks"></a>Notes  
 Les requêtes qui utilisent des vues de gestion dynamiques qui incluent ORDER BY ou des fonctions d'agrégation peuvent accroître la consommation de mémoire et par conséquent contribuer au problème qu'elles tentent de résoudre.  
  
 Utilisez **sys. dm_exec_query_resource_semaphores** pour la résolution des problèmes, mais ne l’incluez pas dans les applications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]qui utiliseront les futures versions de.  
  
 La fonctionnalité Gouverneur de ressources permet à un administrateur de base de données de répartir des ressources serveur entre plusieurs pools de ressources (64 pools au maximum). Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et les versions ultérieures, chaque pool se comporte comme une petite instance de serveur indépendante et requiert 2 sémaphores.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique liées à l’exécution &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
  
  


