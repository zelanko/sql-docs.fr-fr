---
title: Sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL) | Microsoft Docs
description: Retourne l’état actuel des sémaphores de ressources utilisé pour limiter l’optimisation des requêtes simultanées
ms.custom: ''
ms.date: 04/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: language-reference
f1_keywords:
- dm_exec_query_optimizer_memory_gateways_TSQL
- dm_exec_query_optimizer_memory_gateways
- sys.dm_exec_query_optimizer_memory_gateways_TSQL
- sys.dm_exec_query_optimizer_memory_gateways
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_optimizer_memory_gateways dynamic management view
author: josack
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7ebd9b778f48e42c9200e7586983aba801b52e4c
ms.sourcegitcommit: ddb682c0061c2a040970ea88c051859330b8ac00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51570718"
---
# <a name="sysdmexecqueryoptimizermemorygateways-transact-sql"></a>sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Retourne l’état actuel des sémaphores de ressources utilisé pour limiter l’optimisation des requêtes simultanées.

|colonne|Type|Description|  
|----------|---------------|-----------------|  
|**pool_id**|**Int**|ID du pool de ressources sous le gouverneur de ressources|  
|**nom**|**sysname**|Compiler porte nom (petite passerelle, moyenne, grande passerelle)|
|**max_count**|**Int**|Le nombre maximal configuré de compilations simultanées|
|**active_count**|**Int**|Le nombre actuellement actif des compile dans cette porte|
|**waiter_count**|**Int**|Le nombre d’objets waiter dans cette porte|
|**threshold_factor**|**bigint**|Facteur de seuil qui définit la portion de mémoire maximale utilisée par l’optimisation des requêtes.  Pour la petite passerelle, threshold_factor indique l’utilisation de mémoire d’optimiseur maximale en octets pour une seule requête avant qu’il soit nécessaire pour obtenir un accès dans la petite passerelle.  Pour la passerelle de taille moyenne et grande threshold_factor montre la partie de la mémoire totale du serveur disponible pour cette porte. Il est utilisé en tant que diviseur lors du calcul du seuil d’utilisation de mémoire pour la porte.|
|**seuil**|**bigint**|Mémoire du seuil suivante en octets.  La requête est nécessaire pour accéder à cette passerelle si sa consommation de mémoire atteint ce seuil.  « -1 » si la requête n’est pas requise pour avoir un accès à cette passerelle.|
|**is_active**|**bit**|Indique si la requête est nécessaire pour passer de la porte en cours ou non.|


## <a name="permissions"></a>Permissions  
SQL Server requiert l’autorisation VIEW SERVER STATE sur le serveur.

Base de données SQL Azure nécessite l’autorisation VIEW DATABASE STATE dans la base de données.


## <a name="remarks"></a>Notes  
SQL Server utilise une approche de passerelle à plusieurs niveaux pour limiter le nombre de compilations simultanées autorisées.  Trois passerelles sont utilisées, y compris de petite, moyenne et quelle que soit leur. Passerelles d’éviter l’épuisement des ressources de mémoire globale par les consommateurs de nécessiter de mémoire supérieure de compilation.

Attend sur un résultat de la passerelle dans la compilation différée. En plus des retards dans la compilation, demandes limitées aura un RESOURCE_SEMAPHORE_QUERY_COMPILE associé et attendre l’accumulation de type. Le type d’attente RESOURCE_SEMAPHORE_QUERY_COMPILE peut indiquer que les requêtes utilisent une grande quantité de mémoire pour la compilation et que la mémoire a été épuisée, ou sinon il est suffisamment de mémoire disponible en général, les unités toutefois disponibles dans un spécifique passerelle ont été épuisés. La sortie de **sys.dm_exec_query_optimizer_memory_gateways** peut être utilisé pour résoudre les scénarios où la mémoire était insuffisante pour compiler un plan d’exécution de requête.  

## <a name="examples"></a>Exemples  

### <a name="a-viewing-statistics-on-resource-semaphores"></a>A. Affichage des statistiques sur les sémaphores de ressources  
Quelles sont les statistiques de passerelle optimiseur mémoire actuelle pour cette instance de SQL Server ?

```  
SELECT [pool_id], [name], [max_count], [active_count],
       [waiter_count], [threshold_factor], [threshold],
       [is_active]
FROM sys.dm_exec_query_optimizer_memory_gateways;   

```  

## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](./system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique relatives aux exécutions &#40;Transact-SQL&#41;](./execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[L’utilisation de la commande DBCC MEMORYSTATUS pour surveiller l’utilisation de mémoire sur SQL Server 2005](https://support.microsoft.com/help/907877/how-to-use-the-dbcc-memorystatus-command-to-monitor-memory-usage-on-sql-server-2005)
[attend de compilation de requête de grande taille sur RESOURCE_SEMAPHORE_QUERY_COMPILE dans SQL Server 2014](https://support.microsoft.com/help/3024815/large-query-compilation-waits-on-resource-semaphore-query-compile-in-sql-server-2014)
