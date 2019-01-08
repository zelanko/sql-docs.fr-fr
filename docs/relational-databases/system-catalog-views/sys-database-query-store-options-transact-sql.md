---
title: Sys.database_query_store_options (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DATABASE_QUERY_STORE_OPTIONS_TSQL
- DATABASE_QUERY_STORE_OPTIONS
- SYS.DATABASE_QUERY_STORE_OPTIONS_TSQL
- SYS.DATABASE_QUERY_STORE_OPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- database_query_store_options catalog view
- sys.database_query_store_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cef670e97387c2eb4b9493fc1303e36a742f89bc
ms.sourcegitcommit: 1e7ec3b11f25d469163bdc9096a475411eacf79a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53265924"
---
# <a name="sysdatabasequerystoreoptions-transact-sql"></a>Sys.database_query_store_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Retourne les options de requête Store pour cette base de données.  
  
**S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|Indique le mode de fonctionnement souhaité de Query Store, définissez explicitement par l’utilisateur.<br /> 0 = désactivé <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**nvarchar(60)**|Description textuelle du mode de fonctionnement souhaité de Query Store :<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|Indique le mode d’opération de requête Store. En plus de la liste des États souhaités requis par l’utilisateur, état réel peut être un état d’erreur.<br /> 0 = désactivé <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = ERREUR|  
|**actual_state_desc**|**nvarchar(60)**|Description textuelle du mode de fonctionnement réel du Store de la requête.<br />OFF<br />READ_ONLY<br />READ_WRITE<br />d’erreur<br /><br /> Il existe des situations lors de l’état effectif est différent de l’état souhaité :<br /><br /> Requête Store peuvent fonctionner en mode lecture seule même si en lecture-écriture a été spécifié par l’utilisateur. Par exemple, cela peut se produire si la base de données est en mode en lecture seule ou si la taille du Store de la requête a dépassé le quota.<br /><br /> Très rarement, Query Store peut finir dans un état d’erreur en raison d’erreurs internes. Si cela se produit, la requête Store a pu être récupéré en exécutant **sp_query_store_consistency_check** une procédure stockée dans la base de données concernée.|  
|**readonly_reason**|**Int**|Lorsque le **desired_state_desc** est READ_WRITE et **actual_state_desc** est en lecture seule, **readonly_reason** retourne mapper un peu à indiquer pourquoi le Store de la requête se trouve dans mode lecture seule.<br /><br /> 1 - base de données est en mode lecture seule<br /><br /> 2 - base de données est en mode mono-utilisateur<br /><br /> 4 - base de données est en mode d’urgence<br /><br /> 8 - base de données est le réplica secondaire (s’applique à Always On et Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)] géo-réplication). Cette valeur peut être efficacement observée uniquement sur **lisible** réplicas secondaires<br /><br /> 65536 - le Store de la requête a atteint la limite de taille définie par l’option MAX_STORAGE_SIZE_MB.<br /><br /> 131072 - le nombre d’instructions différentes dans le Store de la requête a atteint la limite de mémoire interne. Envisagez les requêtes que vous n’avez pas besoin de suppression ou la mise à niveau vers un niveau de service supérieur pour activer le transfert de Store de la requête en mode lecture-écriture.<br />S'applique uniquement à [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br /> 262144 - taille des éléments en mémoire en attente d’être rendues persistantes sur disque a atteint la limite de mémoire interne. Requête Store sera en mode en lecture seule jusqu'à ce que les éléments en mémoire sont conservées sur le disque. <br />S'applique uniquement à [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br />524288 - base de données a atteint la limite de taille de disque. Store de la requête fait partie de base de données utilisateur, donc si l’espace n’est disponible pour une base de données, ce qui signifie qu’est Store de la requête ne peut pas croître plus.<br />S'applique uniquement à [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. <br /> <br /> Pour basculer les opérations de requête Store arrière en mode lecture-écriture, consultez **Vérifiez Query Store est collecte les données de requête en continu** section de [recommandé avec la requête Store](../../relational-databases/performance/best-practice-with-the-query-store.md).|  
|**current_storage_size_mb**|**bigint**|Taille de la requête Store sur le disque en mégaoctets.|  
|**flush_interval_seconds**|**bigint**|Définit la période pour le vidage régulière des données de requête Store sur le disque. Valeur par défaut est 900 (15 minutes).<br /><br /> Modification à l’aide de la `ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)` instruction.|  
|**interval_length_minutes**|**bigint**|L’intervalle d’agrégation de statistiques. Des valeurs arbitraires ne sont pas autorisés. Utilisez une des opérations suivantes : 1, 5, 10, 15, 30, 60 et 1440 minutes. La valeur par défaut est 60 minutes.|  
|**max_storage_size_mb**|**bigint**|Taille maximale de disque pour le Store de la requête. Valeur par défaut est 100 Mo.<br />Pour [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] édition Premium, par la valeur par défaut est de 1 Go et pour [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] édition De base, elle est de 10 Mo.<br /><br /> Modification à l’aide de la `ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)` instruction.|  
|**stale_query_threshold_days**|**bigint**|Nombre de jours pendant lesquels les requêtes avec aucun paramètre de stratégie sont conservés dans le Store de la requête. Valeur par défaut est 30. La valeur 0 pour désactiver la stratégie de rétention.<br />Pour l’édition [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] de base, la valeur par défaut est 7 jours.<br /><br /> Modification à l’aide de la `ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )` instruction.|  
|**max_plans_per_query**|**bigint**|Limite le nombre maximal de plans stockées. Valeur par défaut est 200. Si la valeur maximale est atteinte, Query Store arrête la capture de nouveaux plans de cette requête. 0 au paramètre supprime la limitation en ce qui concerne le nombre de plans capturées.<br /><br /> Modification à l’aide de la `ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)` instruction.|  
|**query_capture_mode**|**smallint**|Le mode de capture de requête actuellement active :<br /><br /> 1 = ALL : toutes les requêtes sont capturées. C’est la valeur de la configuration par défaut pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> 2 = AUTO - capturer les requêtes pertinentes en fonction de l’exécution du nombre et consommation de ressources. C’est la valeur de la configuration par défaut pour [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].<br /><br /> 3 = NONE : cesser de capturer les nouvelles requêtes. Le magasin de requêtes continuera à recueillir des statistiques de compilation et d’exécution pour les requêtes qui ont déjà été capturées. Utilisez cette configuration avec précaution, car vous risquez de manquer pour capturer les requêtes importantes.|  
|**query_capture_mode_desc**|**nvarchar(60)**|Description textuelle du mode de capture de requête Store :<br /><br /> Toutes les (valeur par défaut pour [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)])<br /><br /> AUTOMATIQUE (par défaut pour [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)])<br /><br /> Aucune|  
|**size_based_cleanup_mode**|**smallint**|Contrôle si le nettoyage est activé automatiquement quand la quantité totale de données approche de la taille maximale :<br /><br /> 0 = OFF - taille en fonction de nettoyage n’est pas activé automatiquement.<br /><br /> 1 = AUTO - taille en fonction de nettoyage est activé automatiquement quand la taille sur disque atteint 90 % de **max_storage_size_mb**. Il s’agit de la valeur de configuration par défaut.<br /><br />Le nettoyage basée sur la taille supprime les requêtes les moins coûteuses et les plus anciennes en premier. Il s’arrête à environ 80 % de max_storage_size_mb.|  
|**size_based_cleanup_mode_desc**|**nvarchar(60)**|Description textuelle du mode de nettoyage basée sur la taille de requête Store :<br /><br /> OFF <br /><br /> AUTOMATIQUE (par défaut)|  
|**wait_stats_capture_mode**|**smallint**|Contrôle si Store de requête exécute une capture de statistiques d’attente : <br /><br /> 0 = désactivé <br /><br /> 1 = activé<br /> **S'applique à**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|
|**wait_stats_capture_mode_desc**|**nvarchar(60)**|Description textuelle du mode de capture de statistiques attente réel : <br /><br /> OFF <br /><br /> (Par défaut)<br /> **S'applique à**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
  
## <a name="permissions"></a>Autorisations  
 Nécessite le **VIEW DATABASE STATE** autorisation.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [Sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Analyse des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)   
 [Procédures stockées de Query Store &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
