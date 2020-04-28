---
title: Analyse des performances à l’aide du Magasin des requêtes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e06344a4-22a5-4c67-b6c6-a7060deb5de6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 192c38bc189928cf980ab0141e53ab12f37d805c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175866"
---
# <a name="monitoring-performance-by-using-the-query-store"></a>Analyse des performances à l'aide du magasin de requêtes
  La fonctionnalité de magasin de requêtes fournit aux administrateurs de bases de données des informations sur le choix de plan de requête et les performances. Elle simplifie la résolution des problèmes de performances en vous permettant de trouver rapidement les différences de performances provoquées par un changement de plan de requête. La fonctionnalité capture automatiquement l'historique des requêtes, des plans et des statistiques d'exécution et les conserve à des fins de consultation. Elle sépare les données en périodes, ce qui vous permet de voir les modèles d'utilisation de base de données et de comprendre à quel moment le changement de plan de requête a eu lieu sur le serveur. Le magasin de requêtes peut être configuré à l'aide de l'option [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) .

||
|-|
|**S’applique à**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] (l'[obtient](http://azure.micosoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).|

> [!IMPORTANT]
>  Il s'agit actuellement d'une fonctionnalité d'aperçu. Pour utiliser le magasin de requêtes, vous devez reconnaître et accepter que l'implémentation du magasin de requêtes est soumise aux termes de la version d'évaluation dans votre contrat de licence (par exemple, Contrat Entreprise, Contrat Microsoft Azure ou Contrat d'abonnement à Microsoft Online), ainsi qu'à toutes les [Conditions d'Utilisation Supplémentaires relatives aux Évaluations Microsoft Azure](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).

##  <a name="enabling-the-query-store"></a><a name="Enabling"></a> Activation du magasin de requêtes
 Le magasin de requêtes n'est pas actif par défaut pour les nouvelles bases de données.

#### <a name="by-using-the-query-store-page-in-management-studio"></a>En utilisant la page Magasin de requêtes dans Management Studio

1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur une base de données, puis sur **Propriétés**. (Nécessite la version [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2016 de [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].)

2.  Dans la boîte de dialogue **Propriétés de la base de données** , sélectionnez la page **Magasin de requêtes** .

3.  Dans la case **Activer** , sélectionnez **True**.

#### <a name="by-using-transact-sql-statements"></a>En utilisant des instructions Transact-SQL

1.  Utilisez l’instruction `ALTER DATABASE` pour activer le magasin de requêtes. Par exemple :

    ```
    ALTER DATABASE AdventureWorks2012 SET QUERY_STORE = ON;
    ```

     Pour obtenir d’autres options de syntaxe relatives au magasin de requêtes, consultez [options ALTER DATABASE SET &#40;&#41;Transact-SQL ](/sql/t-sql/statements/alter-database-transact-sql-set-options).

> [!NOTE]
>  Vous ne pouvez pas activer le magasin de requêtes pour la base de données MASTER.



##  <a name="information-in-the-query-store"></a><a name="About"></a> Informations sur le Magasin des requêtes
 Les plans d’exécution d’une requête spécifique dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] évoluent généralement au fil du temps pour un certain nombre de raisons, telles que les modifications des statistiques, les modifications de schémas, la création/suppression d’index, etc. Le cache de procédures (où sont stockés les plans de requête mis en cache) stocke uniquement le dernier plan d'exécution. Les plans sont également supprimés du cache du plan en raison de la sollicitation de la mémoire. Par conséquent, les régressions des performances de requête provoquées par des modifications du plan d'exécution peuvent être significatives et longues à résoudre.

 Comme le magasin de requêtes conserve plusieurs plans d'exécution par requête, il peut appliquer des stratégies pour indiquer au processeur de requêtes d'utiliser un plan d'exécution spécifique pour une requête. On parle alors de forçage de plan. Le forçage de plan dans un magasin de requêtes est fourni à l'aide d'un mécanisme semblable à l’indicateur de requête [USE PLAN](/sql/t-sql/queries/hints-transact-sql-query) , mais il ne nécessite pas d’apporter des modifications dans les applications utilisateur. Le forçage de plan peut résoudre une régression des performances de requête provoquée par une modification du plan dans un délai très court.

 Voici des scénarios courants pour l'utilisation de la fonctionnalité de magasin de requêtes :

-   Recherchez et corrigez rapidement une régression des performances du plan en forçant l’application du plan de requête précédent. Résolvez les requêtes qui ont récemment rencontré une régression des performances suite à la modification du plan d'exécution.

-   Déterminez le nombre de fois où une requête a été exécutée dans une fenêtre de temps donnée, en aidant un administrateur de base de données à résoudre les problèmes liés aux ressources de performances.

-   Identifiez les *n* requêtes les plus importantes (en termes de temps d’exécution, de consommation de mémoire, etc.) au cours des *x* dernières heures.

-   Auditez l'historique des plans de requête pour une requête donnée.

-   Analysez les ressources (UC, E/S et mémoire) des modèles d'utilisation pour une base de données spécifique.

 Le magasin de requêtes contient deux magasins : un **magasin de plans** pour rendre persistantes les informations du plan d'exécution et un **magasin des statistiques d'exécution** pour rendre persistantes les informations sur les statistiques d'exécution. Le nombre de plans uniques pouvant être stockés pour une requête dans le magasin de plans est limité par l'option de configuration `max_plans_per_query`. Pour améliorer les performances, les informations sont écrites dans les deux magasins de façon asynchrone. Pour optimiser l'espace, les statistiques d'exécution du runtime du magasin de statistiques du runtime sont agrégées sur une période fixe. Les informations contenues dans ces magasins sont visibles en interrogeant les affichages de catalogue du magasin de requêtes.

 La requête suivante retourne des informations sur les requêtes et plans du magasin de requêtes.

```
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
FROM sys.query_store_plan AS Pl
JOIN sys.query_store_query AS Qry
    ON Pl.query_id = Qry.query_id
JOIN sys.query_store_query_text AS Txt
    ON Qry.query_text_id = Txt.query_text_id ;
```



## <a name="using-the-regressed-queries-feature"></a>Utilisation de la fonctionnalité de régression des requêtes
 Après avoir activé le magasin de requêtes, actualisez la partie base de données du volet de l’Explorateur d’objets pour ajouter la section **magasin des requêtes** .

 ![QueryStore](../../database-engine/media/querystore.PNG "QueryStore")

 Sélectionnez **Requêtes en régression**pour ouvrir le volet **Requêtes en régression** dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]. Le volet Requêtes en régression affiche les requêtes et les plans du magasin de requêtes. Les listes déroulantes situées en haut vous permettent de sélectionner les requêtes selon différents critères. Sélectionnez un plan pour afficher le plan de requête sous forme graphique. Des boutons permettent d'afficher la requête source, de forcer un plan de requête et d’annuler son application forcée, ainsi que d'actualiser l'affichage.

 ![RegressedQueries](../../database-engine/media/regressedqueries.PNG "RegressedQueries")

 Pour forcer un plan, sélectionnez une requête et un plan, puis cliquez sur **forcer le plan.** Vous pouvez uniquement forcer des plans qui ont été enregistrés par la fonctionnalité de plan de requête et sont toujours conservés dans le cache du plan de requête.



##  <a name="configuration-options"></a><a name="Options"></a> Options de configuration
 OPERATION_MODE peut être READ_WRITE ou READ_ONLY.

 CLEANUP_POLICY configurez l’argument STALE_QUERY_THRESHOLD_DAYS pour spécifier le nombre de jours pendant lesquels les données doivent être conservées dans le magasin des requêtes.

 DATA_FLUSH_INTERVAL_SECONDS détermine la fréquence à laquelle les données écrites sur le magasin des requêtes sont conservées sur le disque. Pour optimiser les performances, les données collectées par le magasin de requête sont écrites de façon asynchrone sur le disque. La fréquence à laquelle ce transfert asynchrone se produit est configurée via DATA_FLUSH_INTERVAL_SECONDS.

 MAX_SIZE_MB configure la taille maximale du magasin de requêtes. Si la taille des données du magasin de requêtes atteint la limite MAX_SIZE_MB, le magasin de requêtes fait passer automatiquement l'état de Lecture-écriture à Lecture seule et arrête la collecte de nouvelles données.

 INTERVAL_LENGTH_MINUTES détermine l’intervalle de temps auquel les données des statistiques d’exécution du runtime sont agrégées dans le magasin des requêtes. Pour optimiser l'espace, les statistiques d'exécution du runtime du magasin de statistiques du runtime sont agrégées sur une période fixe. Cette période fixe est configurée via INTERVAL_LENGTH_MINUTES.

 Interrogez l'affichage `sys.database_query_store_options` pour déterminer les options actuelles du magasin de requêtes.

 Pour plus d'informations sur la définition des options à l'aide d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] , consultez [Gestion des options](#OptionMgmt).

 

##  <a name="related-views-functions-and-procedures"></a><a name="Related"></a> Vues, fonctions et procédures associées
 Le magasin de requêtes peut être affiché et géré via [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] ou en utilisant les vues et les procédures suivantes.

-   [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql)

### <a name="query-store-catalog-views"></a>Affichages catalogue de magasin de requête
 Sept affichages catalogue présentent des informations sur le magasin de requêtes.

-   [sys.database_query_store_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql)

-   [sys.query_context_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-query-context-settings-transact-sql)

-   [sys.query_store_plan &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-query-store-plan-transact-sql)

-   [sys.query_store_query &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-query-store-query-transact-sql)

-   [sys.query_store_query_text &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql)

-   [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql)

-   [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql)

### <a name="query-store-stored-procedures"></a>Procédures stockées du magasin de requêtes
 Six procédures stockées configurent le magasin de requêtes.

-   [sp_query_store_flush_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql)

-   [sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql)

-   [sp_query_store_force_plan &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql)

-   [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql)

-   [sp_query_store_remove_plan &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql)

-   [sp_query_store_remove_query &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql)



##  <a name="key-usage-scenarios"></a><a name="Scenarios"></a> Principaux scénarios d’utilisation

###  <a name="option-management"></a><a name="OptionMgmt"></a> Gestion des options
 Cette section fournit des instructions sur la gestion de la fonctionnalité de magasin de requête proprement dite.

 **Le magasin de requêtes est-il actuellement actif ?**

 Le magasin de requêtes stocke ses données dans la base de données utilisateur. C’est pourquoi sa taille est limitée (`MAX_STORAGE_SIZE_MB`). Si les données du magasin de requêtes atteignent cette limite, le magasin de requêtes fait passer automatiquement l'état de Lecture-écriture à Lecture seule et arrête la collecte de nouvelles données.

 Exécutez le script suivant pour déterminer si le magasin de requêtes est actuellement actif et s'il collecte actuellement des statistiques d'exécution.

```
DECLARE @x nvarchar(100) = CAST(newid() AS nvarchar(100));
DECLARE @query nvarchar(max) = 
N'IF EXISTS
(
    SELECT * 
    FROM sys.query_store_query_text 
    WHERE query_sql_text LIKE ''%' + @x + N'%''
)
SELECT ''Query Store is active'' ;
ELSE SELECT ''Query Store is NOT active''' ;
EXEC sp_executesql @query;
```

 **Accès aux options du magasin de requêtes**

 Pour trouver des informations détaillées sur l'état du magasin de requêtes, exécutez ce qui suit dans une base de données utilisateur.

```
SELECT * FROM sys.database_query_store_options;
```

 **Définition de l’intervalle du magasin de requêtes**

 Vous pouvez remplacer l'intervalle d'agrégation des statistiques d'exécution de requête (la valeur par défaut est 60 minutes).

```

      USE master;
GO

ALTER DATABASE <database_name> 
SET QUERY_STORE (INTERVAL_LENGTH_MINUTES = 15);
```

 Notez que les valeurs arbitraires ne sont pas autorisées. Vous devez utiliser une des valeurs suivantes : 1, 5, 10, 15, 30 et 60.

 La nouvelle valeur de l'intervalle est exposée via l'affichage `sys.database_query_store_options`.

 Si le stockage du magasin de requêtes est saturé, utilisez l'instruction suivante pour l’étendre.

```
ALTER DATABASE <database_name> 
SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <new_size>);
```

 **Définition de toutes les options du magasin de requêtes**

 Vous pouvez définir simultanément plusieurs options de magasin de requêtes avec l'instruction ALTER DATABASE.

```
ALTER DATABASE <database name> 
SET QUERY_STORE (
    OPERATION_MODE = READ_WRITE,
    CLEANUP_POLICY = 
    (STALE_QUERY_THRESHOLD_DAYS = 30),
    DATA_FLUSH_INTERVAL_SECONDS = 3000,
    MAX_STORAGE_SIZE_MB = 500,
    INTERVAL_LENGTH_MINUTES = 15
);
```

 **Nettoyage de l’espace**

 Les tables internes du magasin de requêtes sont créées dans le groupe de fichiers PRIMARY lors de la création de la base de données. Cette configuration ne peut pas être modifiée ultérieurement. Si vous manquez d'espace, vous pouvez effacer les anciennes données du magasin de requêtes à l'aide de l'instruction suivante.

```
ALTER DATABASE <db_name> SET QUERY_STORE CLEAR;
```

 Vous pouvez également effacer uniquement les données de requête ad hoc, car elles sont moins pertinentes pour les optimisations de requête et l'analyse du plan, mais utilisent autant d'espace.

 **Supprimer des requêtes ad-hoc** Cette opération supprime les requêtes qui ont été exécutées une seule fois et qui datent de plus de 24 heures.

```
DECLARE @id int
DECLARE adhoc_queries_cursor CURSOR 
FOR 
SELECT q.query_id
FROM sys.query_store_query_text AS qt
JOIN sys.query_store_query AS q 
    ON q.query_text_id = qt.query_text_id
JOIN sys.query_store_plan AS p 
    ON p.query_id = q.query_id
JOIN sys.query_store_runtime_stats AS rs 
    ON rs.plan_id = p.plan_id
GROUP BY q.query_id
HAVING SUM(rs.count_executions) < 2 
AND MAX(rs.last_execution_time) < DATEADD (hour, -24, GETUTCDATE())
ORDER BY q.query_id ;

OPEN adhoc_queries_cursor ;
FETCH NEXT FROM adhoc_queries_cursor INTO @id;
WHILE @@fetch_status = 0
    BEGIN 
        PRINT @id
        EXEC sp_query_store_remove_query @id
        FETCH NEXT FROM adhoc_queries_cursor INTO @id
    END 
CLOSE adhoc_queries_cursor ;
DEALLOCATE adhoc_queries_cursor;
```

 Vous pouvez définir votre propre procédure avec une logique différente pour effacer les données qui ne sont plus importantes pour vous.

 L'exemple ci-dessus utilise la procédure stockée étendue `sp_query_store_remove_query` pour supprimer les données inutiles. Vous pouvez également utiliser deux autres procédures.

-   `sp_query_store_reset_exec_stats`-effacer les statistiques d’exécution pour un plan donné.

-   `sp_query_store_remove_plan`-supprime un seul plan.



###  <a name="performance-auditing-and-troubleshooting"></a><a name="Peformance"></a> Audit et résolution des problèmes de performances
 Étant donné que le magasin de requêtes conserve l'historique de compilation et les mesures d'exécution de l'ensemble des exécutions de requête, il permet de répondre facilement aux nombreuses questions que vous pouvez vous poser concernant votre charge de travail.

 ***N* dernières requêtes exécutées sur la base de données.**

```
SELECT TOP 10 qt.query_sql_text, q.query_id, 
    qt.query_text_id, p.plan_id, rs.last_execution_time
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
ORDER BY rs.last_execution_time DESC;
```

 **Nombre d’exécutions pour chaque requête.**

```
SELECT q.query_id, qt.query_text_id, qt.query_sql_text, 
    SUM(rs.count_executions) AS total_execution_count
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
GROUP BY q.query_id, qt.query_text_id, qt.query_sql_text
ORDER BY total_execution_count DESC;
```

 **Nombre de requêtes avec la durée moyenne d’exécution la plus longue au cours de la dernière heure.**

```
SELECT TOP 10 rs.avg_duration, qt.query_sql_text, q.query_id,
    qt.query_text_id, p.plan_id, GETUTCDATE() AS CurrentUTCTime, 
    rs.last_execution_time 
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
WHERE rs.last_execution_time > DATEADD(hour, -1, GETUTCDATE())
ORDER BY rs.avg_duration DESC;
```

 **Nombre de requêtes ayant la plus grande moyenne de lectures d’e/s physiques au cours des dernières 24 heures, avec le nombre moyen de lignes et le nombre d’exécutions correspondants.**

```
SELECT TOP 10 rs.avg_physical_io_reads, qt.query_sql_text, 
    q.query_id, qt.query_text_id, p.plan_id, rs.runtime_stats_id, 
    rsi.start_time, rsi.end_time, rs.avg_rowcount, rs.count_executions
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi 
    ON rsi.runtime_stats_interval_id = rs.runtime_stats_interval_id
WHERE rsi.start_time >= DATEADD(hour, -24, GETUTCDATE()) 
ORDER BY rs.avg_physical_io_reads DESC;
```

 **Requêtes avec plusieurs plans.** Ces requêtes sont particulièrement intéressantes, car elles sont adaptées aux régressions dues à un changement de plan. La requête suivante identifie ces requêtes, ainsi que tous les plans :

```
WITH Query_MultPlans
AS
(
    SELECT COUNT(*) AS cnt, q.query_id 
    FROM sys.query_store_query_text AS qt
    JOIN sys.query_store_query AS q
        ON qt.query_text_id = q.query_text_id
    JOIN sys.query_store_plan AS p
        ON p.query_id = q.query_id
    GROUP BY q.query_id
    HAVING COUNT(distinct plan_id) > 1
)

SELECT q.query_id, object_name(object_id) AS ContainingObject, query_sql_text,
plan_id, p.query_plan AS plan_xml,
p.last_compile_start_time, p.last_execution_time
FROM Query_MultPlans AS qm
JOIN sys.query_store_query AS q
    ON qm.query_id = q.query_id
JOIN sys.query_store_plan AS p
    ON q.query_id = p.query_id
JOIN sys.query_store_query_text qt 
    ON qt.query_text_id = q.query_text_id
ORDER BY query_id, plan_id;
```

 **Requêtes ayant récemment régressé les performances (en comparant un point dans le temps différent).** L'exemple de requête suivant retourne toutes les requêtes dont le temps d'exécution a doublé au cours des dernières 48 heures suite à un changement de plan. La requête compare tous les intervalles de statistiques d'exécution côte à côte.

```
SELECT 
    qt.query_sql_text, 
    q.query_id, 
    qt.query_text_id, 
    rs1.runtime_stats_id AS runtime_stats_id_1,
    rsi1.start_time AS interval_1, 
    p1.plan_id AS plan_1, 
    rs1.avg_duration AS avg_duration_1, 
    rs2.avg_duration AS avg_duration_2,
    p2.plan_id AS plan_2, 
    rsi2.start_time AS interval_2, 
    rs2.runtime_stats_id AS runtime_stats_id_2
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p1 
    ON q.query_id = p1.query_id 
JOIN sys.query_store_runtime_stats AS rs1 
    ON p1.plan_id = rs1.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi1 
    ON rsi1.runtime_stats_interval_id = rs1.runtime_stats_interval_id 
JOIN sys.query_store_plan AS p2 
    ON q.query_id = p2.query_id 
JOIN sys.query_store_runtime_stats AS rs2 
    ON p2.plan_id = rs2.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi2 
    ON rsi2.runtime_stats_interval_id = rs2.runtime_stats_interval_id
WHERE rsi1.start_time > DATEADD(hour, -48, GETUTCDATE()) 
    AND rsi2.start_time > rsi1.start_time 
    AND p1.plan_id <> p2.plan_id
    AND rs2.avg_duration > 2*rs1.avg_duration
ORDER BY q.query_id, rsi1.start_time, rsi2.start_time;
```

 Si vous souhaitez voir toutes les régressions de performances (pas uniquement celles liées au changement de plan), supprimez simplement la condition `AND p1.plan_id <> p2.plan_id` de la requête précédente.

 **Les requêtes qui ont récemment régressé les performances (en comparant les exécutions récentes et historiques).** La requête suivante compare l'exécution des requête en fonction des périodes d'exécution. Dans cet exemple particulier, la requête compare l'exécution lors d'une période récente (1 heure) et l'exécution lors d'une période historique (la veille), puis identifie celles qui ont introduit une charge de travail supplémentaire. Cette mesure est calculée comme suit : différence entre la moyenne des exécutions récentes et la moyenne des exécutions historiques, multipliée par le nombre d'exécutions récentes. Elle représente en fait la durée supplémentaire introduite dans les exécutions récentes en comparaison avec les exécutions historiques :

```
--- "Recent" workload - last 1 hour
DECLARE @recent_start_time datetimeoffset;
DECLARE @recent_end_time datetimeoffset;
SET @recent_start_time = DATEADD(hour, -1, SYSUTCDATETIME());
SET @recent_end_time = SYSUTCDATETIME();

--- "History" workload
DECLARE @history_start_time datetimeoffset;
DECLARE @history_end_time datetimeoffset;
SET @history_start_time = DATEADD(hour, -24, SYSUTCDATETIME());
SET @history_end_time = SYSUTCDATETIME();

WITH
hist AS
(
    SELECT 
        p.query_id query_id, 
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration, 
        SUM(rs.count_executions) count_executions,
        COUNT(distinct p.plan_id) num_plans 
     FROM sys.query_store_runtime_stats AS rs
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id
    WHERE  (rs.first_execution_time >= @history_start_time AND rs.last_execution_time < @history_end_time)
        OR (rs.first_execution_time <= @history_start_time AND rs.last_execution_time > @history_start_time)
        OR (rs.first_execution_time <= @history_end_time AND rs.last_execution_time > @history_end_time)
    GROUP BY p.query_id
),
recent AS
(
    SELECT 
        p.query_id query_id, 
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration, 
        SUM(rs.count_executions) count_executions,
        COUNT(distinct p.plan_id) num_plans 
    FROM sys.query_store_runtime_stats AS rs
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id
    WHERE  (rs.first_execution_time >= @recent_start_time AND rs.last_execution_time < @recent_end_time)
        OR (rs.first_execution_time <= @recent_start_time AND rs.last_execution_time > @recent_start_time)
        OR (rs.first_execution_time <= @recent_end_time AND rs.last_execution_time > @recent_end_time)
    GROUP BY p.query_id
)
SELECT 
    results.query_id query_id,
    results.query_text query_text,
    results.additional_duration_workload additional_duration_workload,
    results.total_duration_recent total_duration_recent,
    results.total_duration_hist total_duration_hist,
    ISNULL(results.count_executions_recent, 0) count_executions_recent,
    ISNULL(results.count_executions_hist, 0) count_executions_hist 
FROM
(
    SELECT
        hist.query_id query_id,
        qt.query_sql_text query_text,
        ROUND(CONVERT(float, recent.total_duration/recent.count_executions-hist.total_duration/hist.count_executions)*(recent.count_executions), 2) AS additional_duration_workload,
        ROUND(recent.total_duration, 2) total_duration_recent, 
        ROUND(hist.total_duration, 2) total_duration_hist,
        recent.count_executions count_executions_recent,
        hist.count_executions count_executions_hist   
    FROM hist 
        JOIN recent 
            ON hist.query_id = recent.query_id 
        JOIN sys.query_store_query AS q 
            ON q.query_id = hist.query_id
        JOIN sys.query_store_query_text AS qt 
            ON q.query_text_id = qt.query_text_id    
) AS results
WHERE additional_duration_workload > 0
ORDER BY additional_duration_workload DESC
OPTION (MERGE JOIN);
```



###  <a name="maintaining-query-performance-stability"></a><a name="Stability"></a>Maintien de la stabilité des performances des requêtes
 Pour les requêtes exécutées plusieurs fois, vous pouvez remarquer que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a utilisé différents plans, ce qui a entraîné une utilisation des ressources et une durée différentes. Le magasin de requêtes permet de facilement détecter le moment où les performances des requêtes ont régressé et de déterminer le plan optimal dans un délai donné. Ensuite, vous pouvez forcer l'application de ce plan optimal pour l'exécution des requêtes ultérieures.

 Vous pouvez également identifier les performances de requêtes incohérentes avec des paramètres (définis manuellement ou automatiquement). Parmi les différents plans, vous pouvez identifier le plan qui est suffisamment rapide et optimal pour la totalité ou la plupart des valeurs de paramètre et forcer ce plan, en maintenant ainsi des performances prévisibles pour l'ensemble plus large de scénarios utilisateur.

 **Forcer un plan pour une requête (appliquer une stratégie de forçage).** Lorsqu'un plan est forcé pour une requête donnée, chaque fois qu'une requête est exécutée, elle l'est avec le plan forcé.

```
EXEC sp_query_store_force_plan @query_id = 48, @plan_id = 49;
```

 Lorsque vous utilisez `sp_query_store_force_plan`, vous pouvez uniquement forcer des plans qui ont été enregistrés par le magasin de requêtes en tant que plan pour cette requête. En d'autres termes, les plans disponibles pour une requête sont uniquement ceux qui ont déjà été utilisés pour exécuter Q1 lorsque le magasin de requêtes était actif.

 **Supprimer le forçage de plan pour une requête.** Pour vous appuyer à nouveau [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur l’optimiseur de requête pour calculer le plan de `sp_query_store_unforce_plan` requête optimal, utilisez pour annuler l’application du plan sélectionné pour la requête.

```
EXEC sp_query_store_unforce_plan @query_id = 48, @plan_id = 49;
```



## <a name="see-also"></a>Voir aussi
 [Surveiller et régler les performances de performance outils de](../performance/monitor-and-tune-for-performance.md) [surveillance et de paramétrage](../performance/performance-monitoring-and-tuning-tools.md) [ouvrir le moniteur d’activité &#40;SQL Server Management Studio](../performance-monitor/open-activity-monitor-sql-server-management-studio.md) le [moniteur d’activité](../performance-monitor/activity-monitor.md)&#41;


