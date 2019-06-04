---
title: sys.query_store_runtime_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/03/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.QUERY_STORE_RUNTIME_STATS_TSQL
- QUERY_STORE_RUNTIME_STATS_TSQL
- SYS.QUERY_STORE_RUNTIME_STATS
- QUERY_STORE_RUNTIME_STATS
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_runtime_stats catalog view
- sys.query_store_runtime_stats catalog view
ms.assetid: ccf7a57c-314b-450c-bd34-70749a02784a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dd25f70c7cf3d34a4411cc15802437d97f5f8190
ms.sourcegitcommit: fa2afe8e6aec51e295f55f8cc6ad3e7c6b52e042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462722"
---
# <a name="sysquerystoreruntimestats-transact-sql"></a>sys.query_store_runtime_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Contient des informations sur les informations de statistiques d’exécution runtime pour la requête.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**runtime_stats_id**|**bigint**|Identificateur de la ligne représentant les statistiques d’exécution pour le **plan_id**, **execution_type** et **runtime_stats_interval_id**. Il est unique seulement pour les intervalles de statistiques de runtime passées. Pour l’intervalle actuellement actif il peut y avoir plusieurs lignes représentant des statistiques d’exécution pour le plan référencé par **plan_id**, avec le type d’exécution représenté par **execution_type**. En règle générale, une ligne représente les statistiques d’exécution qui sont vidés sur le disque, tandis que les autres (s) représentent l’état en mémoire. Par conséquent, pour obtenir l’état réel pour chaque intervalle vous avez besoin d’agréger les mesures, regroupement par **plan_id**, **execution_type** et **runtime_stats_interval_id**.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**plan_id**|**bigint**|Clé étrangère. Joint à [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md).|  
|**runtime_stats_interval_id**|**bigint**|Clé étrangère. Joins to [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md).|  
|**execution_type**|**tinyint**|Détermine le type d’exécution de requête :<br /><br /> 0 - exécution normale (achevée correctement)<br /><br /> 3 - initié par le client annulé l’exécution<br /><br /> 4 - exception abandonnée de l’exécution|  
|**execution_type_desc**|**nvarchar(128)**|Description textuelle du champ de type d’exécution :<br /><br /> 0 - standard<br /><br /> 3 - abandonnée<br /><br /> 4 - exception|  
|**first_execution_time**|**datetimeoffset**|Première heure d’exécution du plan de requête dans l’intervalle d’agrégation. Cela fait référence à l’heure de fin de l’exécution de requête.|  
|**last_execution_time**|**datetimeoffset**|Plan de la dernière exécution de la requête au sein de l’intervalle d’agrégation. Cela fait référence à l’heure de fin de l’exécution de requête.|  
|**count_executions**|**bigint**|Nombre total d’exécutions du plan de requête dans l’intervalle d’agrégation.|  
|**avg_duration**|**float**|Durée du plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes) de la moyenne.|  
|**last_duration**|**bigint**|Plan de la dernière durée de la requête dans l’intervalle d’agrégation (indiqué en microsecondes).|  
|**min_duration**|**bigint**|Durée minimale pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).|  
|**max_duration**|**bigint**|Durée maximale pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).|  
|**stdev_duration**|**float**|Durée écart type pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).|  
|**avg_cpu_time**|**float**|Nombre moyen de temps processeur pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**last_cpu_time**|**bigint**|Dernier temps processeur pour la requête planifier au sein de l’intervalle d’agrégation (indiqué en microsecondes).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**min_cpu_time**|**bigint**|Temps processeur minimal pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**max_cpu_time**|**bigint**|Temps processeur maximal pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**stdev_cpu_time**|**float**|Écart standard du temps processeur pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**avg_logical_io_reads**|**float**|Nombre moyen d’e/s logiques lit du plan de requête dans l’intervalle d’agrégation. (exprimée en nombre de pages de 8 Ko lues).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**last_logical_io_reads**|**bigint**|Dernier nombre d’e/s logiques lit du plan de requête dans l’intervalle d’agrégation. (exprimée en nombre de pages de 8 Ko lues).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**min_logical_io_reads**|**bigint**|Nombre minimal d’e/s logiques lit du plan de requête dans l’intervalle d’agrégation. (exprimée en nombre de pages de 8 Ko lues).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**max_logical_io_reads**|**bigint**|Nombre maximal d’e/s logiques lit du plan de requête dans l’intervalle d’agrégation. (exprimée en nombre de pages de 8 Ko lues).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**stdev_logical_io_reads**|**float**|Nombre d’e/s logiques lit l’écart type pour le plan de requête dans l’intervalle d’agrégation. (exprimée en nombre de pages de 8 Ko lues).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**avg_logical_io_writes**|**float**|Nombre moyen d’e/s logiques écrit pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**last_logical_io_writes**|**bigint**|Dernier nombre d’e/s logiques écrit pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**min_logical_io_writes**|**bigint**|Nombre minimal d’e/s logiques écrit pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**max_logical_io_writes**|**bigint**|Nombre maximal d’e/s logiques écrit pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**stdev_logical_io_writes**|**float**|Nombre d’e/s logiques écritures écart type pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**avg_physical_io_reads**|**float**|Nombre moyen d’e/s physiques lit du plan de requête dans l’intervalle d’agrégation (exprimée en nombre de pages de 8 Ko lues).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**last_physical_io_reads**|**bigint**|Dernier nombre d’e/s physiques lit du plan de requête dans l’intervalle d’agrégation (exprimée en nombre de pages de 8 Ko lues).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**min_physical_io_reads**|**bigint**|Nombre minimal d’e/s physiques lit du plan de requête dans l’intervalle d’agrégation (exprimée en nombre de pages de 8 Ko lues).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**max_physical_io_reads**|**bigint**|Nombre maximal d’e/s physiques lit du plan de requête dans l’intervalle d’agrégation (exprimée en nombre de pages de 8 Ko lues).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**stdev_physical_io_reads**|**float**|Nombre d’e/s physiques lit l’écart type pour le plan de requête dans l’intervalle d’agrégation (exprimée en nombre de pages de 8 Ko lues).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**avg_clr_time**|**float**|CLR temps moyen pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**last_clr_time**|**bigint**|Plan de la dernière durée du CLR pour la requête dans l’intervalle d’agrégation (indiqué en microsecondes).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**min_clr_time**|**bigint**|Durée minimale du CLR pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**max_clr_time**|**bigint**|Durée maximale du CLR pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**stdev_clr_time**|**float**|CLR temps écart type pour le plan de requête dans l’intervalle d’agrégation (indiqué en microsecondes).<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**avg_dop**|**float**|Moyenne DOP (degré de parallélisme) pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**last_dop**|**bigint**|Dernier DOP (degré de parallélisme) pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**min_dop**|**bigint**|DOP (degré de parallélisme) minimale pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**max_dop**|**bigint**|DOP (degré de parallélisme) maximum pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**stdev_dop**|**float**|DOP (degré de parallélisme) écart type pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**avg_query_max_used_memory**|**float**|Allocation de mémoire moyenne (indiquée en tant que le nombre de pages de 8 Ko) pour le plan de requête dans l’intervalle d’agrégation. Toujours 0 pour les requêtes à l’aide en mode natif des procédures de mémoire optimisée compilées.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**last_query_max_used_memory**|**bigint**|Dernière allocation de mémoire (indiquée en tant que le nombre de pages de 8 Ko) pour le plan de requête dans l’intervalle d’agrégation. Toujours 0 pour les requêtes à l’aide en mode natif des procédures de mémoire optimisée compilées.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**min_query_max_used_memory**|**bigint**|Allocation de mémoire minimale (indiquée en tant que le nombre de pages de 8 Ko) pour le plan de requête dans l’intervalle d’agrégation. Toujours 0 pour les requêtes à l’aide en mode natif des procédures de mémoire optimisée compilées.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**max_query_max_used_memory**|**bigint**|Allocation de mémoire maximale (indiquée en tant que le nombre de pages de 8 Ko) pour le plan de requête dans l’intervalle d’agrégation. Toujours 0 pour les requêtes à l’aide en mode natif des procédures de mémoire optimisée compilées.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**stdev_query_max_used_memory**|**float**|Écart type (indiqué en tant que le nombre de pages de 8 Ko) d’allocation de mémoire pour le plan de requête dans l’intervalle d’agrégation. Toujours 0 pour les requêtes à l’aide en mode natif des procédures de mémoire optimisée compilées.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**avg_rowcount**|**float**|Nombre moyen de lignes retournées pour le plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**last_rowcount**|**bigint**|Nombre de lignes retournées par la dernière exécution du plan de requête dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**min_rowcount**|**bigint**|Nombre minimal de lignes retournées pour la requête planifier au sein de l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**max_rowcount**|**bigint**|Nombre maximal de lignes retournées pour la requête planifier au sein de l’intervalle d’agrégation.|  
|**stdev_rowcount**|**float**|Nombre de lignes retournées écart type pour le plan de requête dans l’intervalle d’agrégation.|
|**avg_log_bytes_used**|**float**|Nombre moyen d’octets dans le journal de base de données utilisé par le plan de requête, dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**last_log_bytes_used**|**bigint**|Nombre d’octets dans le journal de base de données utilisée par la dernière exécution du plan de requête, dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**min_log_bytes_used**|**bigint**|Nombre minimal d’octets dans le journal de base de données utilisé par le plan de requête, dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**max_log_bytes_used**|**bigint**|Nombre maximal d’octets dans le journal de base de données utilisé par le plan de requête, dans l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|
|**stdev_log_bytes_used**|**float**|Écart type du nombre d’octets dans le journal de base de données utilisé par un plan de requête, au sein de l’intervalle d’agrégation.<br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|  
|**avg_page_server_io_reads**|**float**|Nombre moyen de page lit les e/s du serveur pour le plan de requête dans l’intervalle d’agrégation. (exprimée en nombre de pages de 8 Ko lues).<br><br/>**Remarque :** S’applique à : Très grande échelle de la base de données SQL Azure</br> Azure SQL Data Warehouse, base de données SQL Azure, MI (non hyperscale) retourne toujours zéro (0).|
|**last_page_server_io_reads**|**bigint**|Dernier nombre d’e/s de pages server lit du plan de requête dans l’intervalle d’agrégation. (exprimée en nombre de pages de 8 Ko lues).<br><br/>**Remarque :** S’applique à : Très grande échelle de la base de données SQL Azure </br> Azure SQL Data Warehouse, base de données SQL Azure, MI (non hyperscale) retourne toujours zéro (0).|
|**min_page_server_io_reads**|**bigint**|Nombre minimal de page lit les e/s du serveur pour le plan de requête dans l’intervalle d’agrégation. (exprimée en nombre de pages de 8 Ko lues).<br><br/>**Remarque :** S’applique à : Très grande échelle de la base de données SQL Azure </br> Azure SQL Data Warehouse, base de données SQL Azure, MI (non hyperscale) retourne toujours zéro (0).|
|**max_page_server_io_reads**|**bigint**|Nombre maximal de page lit les e/s du serveur pour le plan de requête dans l’intervalle d’agrégation. (exprimée en nombre de pages de 8 Ko lues).<br><br/>**Remarque :** S’applique à : Très grande échelle de la base de données SQL Azure </br> Azure SQL Data Warehouse, base de données SQL Azure, MI (non hyperscale) retourne toujours zéro (0).|
|**stdev_page_server_io_reads**|**float**|Nombre de serveur de pages d’e/s lectures écart type pour le plan de requête dans l’intervalle d’agrégation. (exprimée en nombre de pages de 8 Ko lues).<br><br/>**Remarque :** S’applique à : Très grande échelle de la base de données SQL Azure </br> Azure SQL Data Warehouse, base de données SQL Azure, MI (non hyperscale) retourne toujours zéro (0).|
  
## <a name="permissions"></a>Autorisations  
 Nécessite le **VIEW DATABASE STATE** autorisation.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Analyse des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Procédures stockées de Query Store &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
