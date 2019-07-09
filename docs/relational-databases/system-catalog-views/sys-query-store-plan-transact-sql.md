---
title: sys.query_store_plan (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_PLAN_TSQL
- SYS.QUERY_STORE_PLAN
- SYS.QUERY_STORE_PLAN_TSQL
- QUERY_STORE_PLAN
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_plan catalog view
- sys.query_store_plan catalog view
ms.assetid: b4d05439-6360-45db-b1cd-794f4a64935e
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6158df674c90f14a1f77f5e12c18adcb6f8fbc4f
ms.sourcegitcommit: f97394f18f8509aec596179acd4c59d8492a4cd2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2019
ms.locfileid: "67652862"
---
# <a name="sysquerystoreplan-transact-sql"></a>sys.query_store_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Contient des informations sur chaque plan d’exécution associé à une requête.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|
|**plan_id**|**bigint**|Clé primaire.|  
|**query_id**|**bigint**|Clé étrangère. Joint à [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md).|  
|**plan_group_id**|**bigint**|ID du groupe de plan. Les requêtes de curseur nécessitent généralement plusieurs (remplir et fetch) des plans. Remplir et plans d’extraction qui sont compilés ensemble dans le même groupe.<br /><br /> 0 signifie le plan n’est pas dans un groupe.|  
|**engine_version**|**nvarchar(32)**|Version du moteur utilisé pour compiler le plan dans **'major.minor.build.revision'** format.|  
|**compatibility_level**|**smallint**|Niveau de compatibilité de base de données de la base de données référencée dans la requête.|  
|**query_plan_hash**|**binary(8)**|Hachage MD5 du plan individuel.|  
|**query_plan**|**nvarchar(max)**|Showplan XML pour le plan de requête.|  
|**is_online_index_plan**|**bit**|Plan a été utilisé pendant une génération d’index en ligne. <br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|  
|**is_trivial_plan**|**bit**|Plan est un plan trivial (sortie dans l’étape 0 de l’optimiseur de requête). <br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|  
|**is_parallel_plan**|**bit**|Plan est parallèle. <br/>**Remarque :** Azure SQL Data Warehouse retourne toujours un (1).|  
|**is_forced_plan**|**bit**|Plan est marqué comme étant forcé lorsque l’utilisateur exécute la procédure stockée **sys.sp_query_store_force_plan**. Le mécanisme de forçage *ne garantit pas* qu’exactement ce plan sera utilisé pour la requête référencée par **query_id**. Application forcée du plan entraîne la requête doit être compilé à nouveau et généralement produit exactement le plan identiques ou similaire au plan référencé par **plan_id**. Si le forçage de plan n’aboutit pas, **force_failure_count** est incrémenté et **last_force_failure_reason** est rempli avec la raison de l’échec. <br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|  
|**is_natively_compiled**|**bit**|Plan inclut les procédures compilées en mode natif à mémoire optimisée. (0 = FALSE, 1 = TRUE). <br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|  
|**force_failure_count**|**bigint**|Nombre de fois forcer ce plan a échoué. Il peut être incrémenté uniquement lorsque la requête est recompilée (*pas à chaque exécution*). Il est réinitialisé à 0 chaque fois **is_plan_forced** est remplacée par **FALSE** à **TRUE**. <br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|  
|**last_force_failure_reason**|**Int**|Raison de forçage de plan l’échec.<br /><br /> 0 : aucun échec, un sinon numéro d’erreur de l’erreur qui a provoqué l’utilisation forcée Échec<br /><br /> 8637: ONLINE_INDEX_BUILD<br /><br /> 8683: INVALID_STARJOIN<br /><br /> 8684: TIME_OUT<br /><br /> 8689: NO_DB<br /><br /> 8690: HINT_CONFLICT<br /><br /> 8691: SETOPT_CONFLICT<br /><br /> 8694: DQ_NO_FORCING_SUPPORTED<br /><br /> 8698: NO_PLAN<br /><br /> 8712: NO_INDEX<br /><br /> 8713: VIEW_COMPILE_FAILED<br /><br /> \<autre valeur > : GENERAL_FAILURE <br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|  
|**last_force_failure_reason_desc**|**nvarchar(128)**|Description textuelle du last_force_failure_reason_desc.<br /><br /> ONLINE_INDEX_BUILD : requête tente de modifier les données alors que la table cible a un index qui est en cours de génération en ligne<br /><br /> INVALID_STARJOIN : plan contient la spécification de StarJoin non valide<br /><br /> VALEUR : Numéro de l’optimiseur a dépassé d’opérations autorisées lors de la recherche du plan spécifié par le plan forcé<br /><br /> NO_DB: Une base de données spécifiée dans le plan n’existe pas<br /><br /> HINT_CONFLICT : Impossible de compiler la requête, car le plan est en conflit avec un indicateur de requête<br /><br /> DQ_NO_FORCING_SUPPORTED : Impossible d’exécuter la requête, car le plan est en conflit avec l’utilisation de la requête distribuée ou opérations de recherche en texte intégral.<br /><br /> NO_PLAN : Processeur de requêtes ne peut pas produire de plan de requête, car le plan forcé n’a pas pu être vérifié pour être valide pour la requête<br /><br /> NO_INDEX : L’index spécifié dans le plan n’est plus existe<br /><br /> VIEW_COMPILE_FAILED : Impossible de forcer le plan de requête en raison d’un problème dans une vue indexée référencée dans le plan<br /><br /> GENERAL_FAILURE : erreur générale forçage (non couvert avec raisons ci-dessus) <br/>**Remarque :** Azure SQL Data Warehouse retournera toujours *NONE*.|  
|**count_compiles**|**bigint**|Planifier les statistiques de compilation.|  
|**initial_compile_start_time**|**datetimeoffset**|Planifier les statistiques de compilation.|  
|**last_compile_start_time**|**datetimeoffset**|Planifier les statistiques de compilation.|  
|**last_execution_time**|**datetimeoffset**|Dernier temps d’exécution fait référence à la dernière heure de fin du plan de requête /.|  
|**avg_compile_duration**|**float**|Planifier les statistiques de compilation. <br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|  
|**last_compile_duration**|**bigint**|Planifier les statistiques de compilation. <br/>**Remarque :** Azure SQL Data Warehouse retourne toujours zéro (0).|  
|**plan_forcing_type**|**Int**|Planifier le forçage de type.<br /><br />0 : Aucune<br /><br />1 : MANUAL<br /><br />2 : AUTO|  
|**plan_forcing_type_desc**|**nvarchar(60)**|Description textuelle de plan_forcing_type.<br /><br />NONE : Aucune application forcée du plan<br /><br />MANUELLE : Plan forcé par l’utilisateur<br /><br />AUTO : Plan forcé par le réglage automatique|  

## <a name="plan-forcing-limitations"></a>Limitations de forçage de plan
Le Magasin des requêtes a un mécanisme qui permet de forcer l’optimiseur de requête à utiliser un certain plan d’exécution. Toutefois, il existe certaines limitations qui peuvent empêcher l’application d’un plan. 

Premièrement, si le plan contient les constructions suivantes :
* Instruction Insert bulk.
* Référence à une table externe
* Requête distribuée ou opérations de recherche en texte intégral
* Utilisation de requêtes globales 
* Curseurs dynamiques ou jeu de clés (application forcée du plan est pris en charge pour les curseurs statiques et avance rapide)
* Spécification de jointure en étoile non valide 

Deuxièmement, quand les objets sur lesquels s’appuie le plan ne sont plus disponibles :
* Base de données (si la base de données d'où provient le plan n’existe plus)
* Index (absent ou désactivé)

Enfin, s’il y a des problèmes avec le plan lui-même :
* Non conforme pour la requête
* L’optimiseur de requête a dépassé le nombre d’opérations autorisées
* Code XML du plan incorrect

## <a name="permissions"></a>Autorisations  
 Nécessite le **VIEW DATABASE STATE** autorisation.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Analyse des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Procédures stockées de Query Store &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
