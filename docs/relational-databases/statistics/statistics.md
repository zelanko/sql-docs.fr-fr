---
title: Statistiques | Microsoft Docs
ms.custom: 
ms.date: 04/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-statistics
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statistical information [SQL Server], query optimization
- query performance [SQL Server], statistics
- query optimization statistics [SQL Server]
- statistical information [SQL Server], database options
- query optimization statistics [SQL Server], about query optimization statistics
- statistical information [SQL Server], guidelines
- statistical information [SQL Server]
- using statistics [SQL Server]
- statistical information [SQL Server], indexes
- index statistics [SQL Server]
- query optimizer [SQL Server], statistics
- statistics [SQL Server]
ms.assetid: b86a88ba-4f7c-4e19-9fbd-2f8bcd3be14a
caps.latest.revision: 70
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e098a8f837d216f18bb1310db3164b57f24575ba
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="statistics"></a>Statistiques
  L'optimiseur de requête utilise des statistiques dans l'optique de créer des plans de requête qui améliorent les performances des requêtes. Pour la plupart des requêtes, l'optimiseur de requête génère déjà les statistiques utiles à un plan de requête de haute qualité ; dans certains cas, vous devez créer des statistiques supplémentaires ou modifier la conception des requêtes pour obtenir des résultats optimaux. Cette rubrique traite des concepts de statistiques et fournit des instructions pour vous permettre d'utiliser efficacement les statistiques d'optimisation de requête.  
  
##  <a name="DefinitionQOStatistics"></a> Composants et concepts  
 Statistiques  
 Les statistiques utilisées dans le cadre de l'optimisation de requête sont des objets qui contiennent des informations statistiques sur la distribution des valeurs dans une ou plusieurs colonnes d'une table ou d'une vue indexée. L'optimiseur de requête utilise ces statistiques pour estimer le nombre de lignes, également appelé *cardinalité*, dans le résultat de la requête. Ces *estimations de cardinalité* permettent à l’optimiseur de requête de créer un plan de requête de haute qualité. Par exemple, l'optimiseur de requête peut utiliser des estimations de cardinalité pour choisir l'opérateur de recherche d'index plutôt que l'opérateur d'analyse d'index, plus vorace en ressources, contribuant ainsi à améliorer les performances des requêtes.  
  
 Chaque objet de statistiques est créé dans une liste constituée d'une ou de plusieurs colonnes de table et comprend un histogramme présentant la distribution des valeurs dans la première colonne. Les objets de statistiques sur plusieurs colonnes stockent également des informations statistiques sur la corrélation des valeurs entre les colonnes. Ces statistiques de corrélation, également appelées *densités*, sont dérivées du nombre de lignes distinctes de valeurs de colonne. Pour plus d’informations sur les objets de statistiques, consultez [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md).  
  
 Statistiques filtrées  
 Les statistiques filtrées peuvent améliorer les performances des requêtes qui effectuent des sélections dans des sous-ensembles bien définis de données. Les statistiques filtrées utilisent un prédicat de filtre pour sélectionner le sous-ensemble de données qui est inclus dans les statistiques. Les statistiques filtrées correctement conçues peuvent améliorer le plan d'exécution de requête par rapport aux statistiques de table complète. Pour plus d’informations sur le prédicat de filtre, consultez [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md). Pour plus d'informations sur l'opportunité de créer des statistiques filtrées, consultez la section [Quand créer des statistiques](#UpdateStatistics) . Pour une étude de cas, consultez l’entrée de blog [Using Filtered Statistics with Partitioned Tables](http://go.microsoft.com/fwlink/?LinkId=178505)sur le site web SQLCAT.  
  
 Options de statisques  
 Il existe trois options que vous pouvez définir qui affectent quand et comment les statistiques sont créées et mises à jour. Ces options sont définies au niveau de la base de données uniquement.  
  
 Option AUTO_CREATE_STATISTICS  
 Lorsque l'option de création automatique de statistiques AUTO_CREATE_STATISTICS est activée, l'optimiseur de requête crée des statistiques sur les colonnes individuelles du prédicat de requête, le cas échéant, pour améliorer les estimations de cardinalité pour le plan de requête. Ces statistiques de colonne unique sont créées sur les colonnes où ne figure pas déjà un histogramme au niveau d'un objet de statistiques existant. L'option AUTO_CREATE_STATISTICS ne détermine pas si les statistiques sont créées pour des index. De même, cette option ne génère pas de statistiques filtrées. Elle s'applique exclusivement aux statistiques de colonne unique pour la table entière.  
  
 Lorsque l'optimiseur de requête crée des statistiques suite à l'utilisation de l'option AUTO_CREATE_STATISTICS, le nom des statistiques commence par `_WA`. Vous pouvez utiliser la requête suivante pour déterminer si l'optimiseur de requête a créé des statistiques pour une colonne de prédicat de requête.  
  
```  
SELECT OBJECT_NAME(s.object_id) AS object_name,  
    COL_NAME(sc.object_id, sc.column_id) AS column_name,  
    s.name AS statistics_name  
FROM sys.stats AS s JOIN sys.stats_columns AS sc  
    ON s.stats_id = sc.stats_id AND s.object_id = sc.object_id  
WHERE s.name like '_WA%'  
ORDER BY s.name;  
```  
  
 Option AUTO_UPDATE_STATISTICS  
 Lorsque l'option de mise à jour automatique des statistiques AUTO_UPDATE_STATISTICS est activée, l'optimiseur de requête détermine si les statistiques sont obsolètes et les met éventuellement à jour lorsqu'elles sont utilisées par une requête. Les statistiques deviennent obsolètes après que des opérations d'insertion, de mise à jour, de suppression ou de fusion ont modifié la distribution des données dans la table ou la vue indexée. L'optimiseur de requête détermine si les statistiques sont obsolètes en comptant le nombre de modifications de données depuis la dernière mise à jour des statistiques et en comparant le nombre de modifications à un seuil. Ce seuil est basé sur le nombre de lignes contenues dans la table ou la vue indexée.  
  
-   SQL Server (2014 et les versions antérieures) utilise un seuil reposant sur le pourcentage de lignes modifiées. Cette valeur est indépendante du nombre de lignes figurant dans la table.  
  
-   SQL Server (à partir de la version 2016 et avec un niveau de compatibilité de 130) utilise un seuil qui s’ajuste en fonction du nombre de lignes contenues dans la table. Du fait de cette modification, les statistiques sur des tables volumineuses sont mises à jour plus fréquemment.  
  
 L'optimiseur de requête vérifie s'il existe des statistiques obsolètes avant de compiler une requête et avant d'exécuter un plan de requête mis en cache. Avant de compiler une requête, l'optimiseur de requête utilise les colonnes, les tables et les vues indexées du prédicat de requête pour identifier les statistiques susceptibles d'être obsolètes. Avant d'exécuter un plan de requête mis en cache, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] vérifie que le plan de requête fait référence à des statistiques à jour.  
  
 L’option AUTO_UPDATE_STATISTICS s’applique aux objets de statistiques créés pour les index, aux colonnes uniques contenues dans les prédicats de requête et aux statistiques créées à l’aide de l’instruction [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) . Cette option s'applique également aux statistiques filtrées.  
  
 AUTO_UPDATE_STATISTICS_ASYNC  
 L'option de mise à jour asynchrone des statistiques AUTO_UPDATE_STATISTICS_ASYNC détermine si l'optimiseur de requête utilise des mises à jour de statistiques synchrones ou asynchrones. Par défaut, l'option de mise à jour asynchrone des statistiques est désactivée, et l'optimiseur de requête met à jour les statistiques en mode synchrone. L’option AUTO_UPDATE_STATISTICS_ASYNC s’applique aux objets de statistiques créés pour les index, aux colonnes uniques contenues dans les prédicats de requête et aux statistiques créées à l’aide de l’instruction [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) .  
  
 La mise à jour des statistiques peut être synchrone (par défaut) ou asynchrone. Dans le cas de la mise à jour synchrone des statistiques, les requêtes sont systématiquement compilées et exécutées avec des statistiques à jour ; si les statistiques sont obsolètes, l'optimiseur de requête attend que les statistiques soient mises à jour avant de compiler et d'exécuter les requêtes. Dans le cas de la mise à jour asynchrone des statistiques, les requêtes sont compilées avec les statistiques existantes, même si celles-ci sont obsolètes ; l'optimiseur de requête peut très bien choisir un plan de requête non optimal si les statistiques sont obsolètes au moment où les requêtes sont compilées. Les requêtes compilées à l'issue d'une mise à jour asynchrone ont l'avantage d'utiliser des statistiques mises à jour.  
  
 Envisagez d'utiliser des statistiques synchrones lorsque vous effectuez des opérations qui modifient la distribution des données, telles que la troncation d'une table ou une mise à jour en bloc d'un fort pourcentage de lignes. Si vous ne mettez pas à jour les statistiques à l'issue de l'opération, l'utilisation de statistiques synchrones vous garantira que les statistiques sont à jour avant d'exécuter des requêtes sur les données modifiées.  
  
 Envisagez d'utiliser des statistiques asynchrones pour obtenir des temps de réponse des requêtes plus prévisibles pour les scénarios suivants :  
  
-   Votre application exécute régulièrement la même requête, des requêtes similaires ou des plans de requête mis en cache similaires. Il se peut que les temps de réponse de vos requêtes soient plus prévisibles avec des mises à jour de statistiques asynchrones qu'avec des mises à jour de statistiques synchrones, car l'optimiseur de requête peut exécuter les requêtes entrantes sans attendre la mise à jour des statistiques. Cela évite de retarder certaines requêtes et pas les autres.  
  
-   Votre application a connu des expirations de délai de demandes clientes causées par une ou plusieurs requêtes en attente de statistiques mises à jour. Dans certains cas, l'attente de statistiques synchrones peut entraîner l'échec des applications dont les délais d'expiration sont agressifs.  
  
 INCREMENTAL STATS  
 Si la valeur ON est définie, les statistiques sont créées par partition. Si la valeur est OFF, l'arborescence des statistiques est supprimée et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recalcule les statistiques. La valeur par défaut est OFF. Ce paramètre remplace la propriété INCREMENTAL de niveau base de données.  
  
 Lorsque de nouvelles partitions sont ajoutées à une table volumineuse, les statistiques doivent être mises à jour afin d'inclure les nouvelles partitions. Cependant, la durée nécessaire pour analyser la table entière (option FULLSCAN ou SAMPLE) peut être assez longue. En outre, l'analyse la table entière n'est pas nécessaire car seules les statistiques sur les nouvelles partitions peuvent être requises. L'option incrémentielle crée et stocke des statistiques par partition, et une fois la mise à jour terminée, seules sont actualisées les statistiques sur les partitions qui ont besoin de nouvelles statistiques  
  
 Si les statistiques par partition ne sont pas prises en charge, l'option est ignorée et un avertissement est généré. Les statistiques incrémentielles ne sont pas prises en charge pour les types de statistiques suivants :  
  
-   statistiques créées avec des index qui ne sont pas alignés sur les partitions avec la table de base ;  
  
-   statistiques créées sur les bases de données secondaires lisibles Always On ;  
  
-   statistiques créées sur les bases de données en lecture seule ;  
  
-   statistiques créées sur les index filtrés ;  
  
-   statistiques créées sur les vues ;  
  
-   statistiques créées sur les tables internes ;  
  
-   Statistiques créées avec les index spatiaux ou les index XML.  
  
||  
|-|  
|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
  
##  <a name="CreateStatistics"></a> Quand créer des statistiques  
 L'optimiseur de requête crée déjà des statistiques selon les méthodes suivantes :  
  
1.  L'optimiseur de requête crée des statistiques pour les index de tables ou de vues lors de la création des index. Ces statistiques sont créées sur les colonnes de clés de l'index. Si l'index est un index filtré, l'optimiseur de requête crée des statistiques filtrées sur le même sous-ensemble de lignes spécifié pour l'index filtré. Pour plus d’informations sur les index filtrés, consultez [Créer des index filtrés](../../relational-databases/indexes/create-filtered-indexes.md) et [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
2.  L'optimiseur de requête crée des statistiques pour les colonnes uniques des prédicats de requête lorsque l'option AUTO_CREATE_STATISTICS est activée.  
  
 Pour la plupart des requêtes, ces deux méthodes de création de statistiques sont l’assurance de disposer d’un plan de requête de haute qualité. Dans certains cas, vous pouvez améliorer les plans de requête en créant des statistiques supplémentaires à l’aide de l’instruction [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) . Ces statistiques supplémentaires peuvent capturer des corrélations statistiques dont l'optimiseur de requête ne tient pas compte lorsqu'il crée des statistiques pour des index ou des colonnes uniques. Il se peut que votre application présente des corrélations statistiques supplémentaires dans les données de table qui, si elles sont calculées dans un objet de statistiques, peuvent permettre à l'optimiseur de requête d'améliorer les plans de requête. Par exemple, les statistiques filtrées sur un sous-ensemble de lignes de données ou les statistiques multicolonnes sur des colonnes de prédicat de requête sont susceptibles d'améliorer le plan de requête.  
  
 Dans le cadre de la création de statistiques à l'aide de l'instruction CREATE STATISTICS, nous vous recommandons de maintenir l'option AUTO_CREATE_STATISTICS activée de sorte que l'optimiseur de requête continue de créer de manière régulière des statistiques de colonne unique pour les colonnes de prédicat de requête. Pour plus d’informations sur les prédicats de requête, consultez [Condition de recherche &#40;Transact-SQL&#41;](../../t-sql/queries/search-condition-transact-sql.md).  
  
 Envisagez de créer des statistiques avec l'instruction CREATE STATISTICS dans l'un des cas suivants :  
  
-   l'Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] suggère de créer des statistiques ;  
  
-   le prédicat de requête contient plusieurs colonnes corrélées qui ne figurent pas déjà dans le même index ;  
  
-   la requête effectue une sélection dans un sous-ensemble de données ;  
  
-   il manque des statistiques pour la requête.  
  
### <a name="query-predicate-contains-multiple-correlated-columns"></a>Le prédicat de requête contient plusieurs colonnes corrélées  
 Lorsqu'un prédicat de requête contient plusieurs colonnes ayant entre elles des relations et des dépendances, des statistiques sur les différentes colonnes peuvent améliorer le plan de requête. Les statistiques sur plusieurs colonnes contiennent des statistiques de corrélation entre les colonnes appelées *densités*, qui ne sont pas disponibles dans les statistiques de colonne unique. Les densités peuvent améliorer les estimations de cardinalité lorsque les résultats de requête dépendent des relations de données entre plusieurs colonnes.  
  
 Si les colonnes figurent déjà dans le même index, l'objet de statistiques multicolonnes existe déjà et il n'est pas nécessaire de le créer manuellement. Si les colonnes ne figurent pas déjà dans le même index, vous pouvez créer des statistiques multicolonnes en créant un index sur les colonnes ou en utilisant l'instruction CREATE STATISTICS. Un index exige davantage de ressources système qu'un objet de statistiques. Ainsi, si l'application n'a pas besoin de l'index multicolonne, vous pouvez économiser des ressources système en créant l'objet de statistiques sans créer l'index.  
  
 Lors de la création de statistiques multicolonnes, l'ordre des colonnes dans la définition de l'objet de statistiques a une incidence sur l'efficacité des densités lorsqu'il s'agit de réaliser des estimations de cardinalité. L'objet de statistiques stocke des densités pour chaque préfixe de colonnes de clés contenu dans la définition de l'objet de statistiques. Pour plus d’informations sur les densités, consultez [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md).  
  
 Pour créer des densités utiles aux estimations de cardinalité, les colonnes du prédicat de requête doivent correspondre à l'un des préfixes de colonnes contenus dans la définition de l'objet de statistiques. Par exemple, le code suivant crée un objet de statistiques multicolonnes sur les colonnes `LastName`, `MiddleName`et `FirstName`.  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.stats  
    WHERE name = 'LastFirst'  
    AND object_ID = OBJECT_ID ('Person.Person'))  
DROP STATISTICS Person.Person.LastFirst;  
GO  
CREATE STATISTICS LastFirst ON Person.Person (LastName, MiddleName, FirstName);  
GO  
```  
  
 Dans cet exemple, l'objet de statistiques `LastFirst` comprend des densités pour les préfixes de colonne suivants : (`LastName`), (`LastName, MiddleName`) et (`LastName, MiddleName, FirstName`). La densité n'est pas disponible pour (`LastName, FirstName`). Si la requête utilise `LastName` et `FirstName` sans utiliser `MiddleName`, la densité n'est pas disponible pour les estimations de cardinalité.  
  
### <a name="query-selects-from-a-subset-of-data"></a>La requête effectue une sélection dans un sous-ensemble de données  
 Lorsque l'optimiseur de requête crée des statistiques pour des colonnes et des index uniques, il crée les statistiques pour les valeurs contenues dans toutes les lignes. Lorsque les requêtes effectuent une sélection dans un sous-ensemble de lignes et que ce sous-ensemble de lignes présente une distribution de données unique, des statistiques filtrées peuvent améliorer les plans de requête. Vous pouvez créer des statistiques filtrées à l'aide de l'instruction CREATE STATISTICS avec la clause WHERE pour définir l'expression de prédicat de filtre.  
  
 Par exemple, dans [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], chaque produit de la table Production.Product appartient à l'une des quatre catégories de la table Production.ProductCategory : Bikes, Components, Clothing et Accessories. Chacune de ces catégories présente une distribution de données différente pour le poids (Weight) : le poids des bicyclettes (Bikes) varie de 13,77 à 30,0, le poids des composants (Components) varie de 2,12 à 1 050,00 avec quelques valeurs NULL, le poids des vêtements (Clothing) est toujours NULL et le poids des accessoires (Accessories) est également toujours NULL.  
  
 Si l'on prend la catégorie Bikes pour exemple, les statistiques filtrées sur tous les poids de bicyclettes fournissent des statistiques plus précises à l'optimisateur de requête et peuvent améliorer la qualité du plan de requête par rapport aux statistiques de table entière ou aux statistiques inexistantes de la colonne Weight (Poids). Si la colonne où figure le poids des bicyclettes constitue un candidat valable pour les statistiques filtrées, tel n'est pas forcément le cas pour un index filtré si le nombre de recherches de poids est relativement faible. Les gains en performances offerts par un index filtré lors des recherches risquent de ne pas compenser les coûts de maintenance et de stockage supplémentaires liés à l'ajout d'un index filtré à la base de données.  
  
 L'instruction suivante crée les statistiques filtrées `BikeWeights` sur toutes les sous-catégories de bicyclettes (Bikes). L'expression de prédicat filtré définit les bicyclettes en énumérant toutes les sous-catégories de bicyclettes à l'aide de la comparaison `Production.ProductSubcategoryID IN (1,2,3)`. Le prédicat ne peut pas utiliser le nom de catégorie Bikes car il est stocké dans la table Production.ProductCategory, et toutes les colonnes spécifiées dans l'expression de filtre doivent se trouver dans la même table.  
  
 [!code-sql[StatisticsDDL#FilteredStats2](../../relational-databases/statistics/codesnippet/tsql/statistics_1.sql)]  
  
 L'optimiseur de requête peut utiliser les statistiques filtrées `BikeWeights` pour améliorer le plan de requête de la requête suivante qui sélectionne toutes les bicyclettes dont le poids est supérieur à `25`.  
  
```  
SELECT P.Weight AS Weight, S.Name AS BikeName  
FROM Production.Product AS P  
    JOIN Production.ProductSubcategory AS S   
    ON P.ProductSubcategoryID = S.ProductSubcategoryID  
WHERE P.ProductSubcategoryID IN (1,2,3) AND P.Weight > 25  
ORDER BY P.Weight;  
GO  
```  
  
### <a name="query-identifies-missing-statistics"></a>La requête identifie les statistiques manquantes  
 Si une erreur ou tout autre événement empêche l'optimiseur de requête de créer des statistiques, il crée le plan de requête sans utiliser de statistiques. L'optimiseur de requête indique que les statistiques sont manquantes et tente de les régénérer à la prochaine exécution de la requête.  
  
 Les statistiques manquantes sont indiquées comme des avertissements (nom de la table en rouge) lorsque le plan d'exécution d'une requête est affiché sous forme graphique à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. D'autre part, le **permet de surveiller la classe d'événements** Missing Column Statistics [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et d'être tenu informé lorsque des statistiques manquent. Pour plus d’informations, consultez [Catégorie d’événement Erreurs et avertissements &#40;moteur de base de données&#41;](../../relational-databases/event-classes/errors-and-warnings-event-category-database-engine.md).  
  
 S'il manque des statistiques, procédez comme suit :  
  
-   vérifiez que les options AUTO_CREATE_STATISTICS et AUTO_UPDATE_STATISTICS sont activées ;  
  
-   vérifiez que la base de données n'est pas en lecture seule. Si la base de données est en lecture seule, l'optimiseur de requête ne peut pas enregistrer les statistiques ;  
  
-   créez les statistiques manquantes à l'aide de l'instruction CREATE STATISTICS.  
  
 Lorsque les statistiques sur une base de données en lecture seule ou un instantané en lecture seule sont absentes ou obsolètes, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] crée et gère les statistiques temporaires dans **tempdb**. Lorsque le [!INCLUDE[ssDE](../../includes/ssde-md.md)] crée des statistiques temporaires, le nom des statistiques est ajouté avec le suffixe _readonly_database_statistic pour différencier les statistiques temporaires des statistiques permanentes. Le suffixe _readonly_database_statistic est réservé pour les statistiques générées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Des scripts pour les statistiques temporaires peuvent être créés et reproduits sur une base de données en lecture-écriture. Le cas échéant, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] remplace le suffixe du nom des statistiques _readonly_database_statistic par _readonly_database_statistic_scripted.  
  
 Seul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut créer et mettre à jour les statistiques temporaires. Toutefois, vous pouvez supprimer des statistiques temporaires et analyser les propriétés des statistiques en utilisant les mêmes outils que ceux que vous utilisez pour les statistiques permanentes :  
  
-   Supprimez les statistiques temporaires à l’aide de l’instruction [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md) .  
  
-   Analysez les statistiques à l’aide des affichages catalogue **sys.stats** et **sys.stats_columns** . **sys_stats** inclut la colonne **is_temporary** pour indiquer les statistiques permanentes et temporaires.  
  
 Étant donné que les statistiques temporaires sont stockées dans **tempdb**, un redémarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provoque la disparition de toutes les statistiques temporaires.  
  
  
##  <a name="UpdateStatistics"></a> Quand mettre à jour des statistiques  
 L'optimiseur de requête détermine si les statistiques sont obsolètes et les met éventuellement à jour lorsqu'elles sont requises par un plan de requête. Dans certains cas, vous pouvez améliorer le plan de requête et donc les performances des requêtes en mettant à jour les statistiques de façon plus régulière que lorsque l'option AUTO_UPDATE_STATISTICS est activée. Vous pouvez mettre à jour les statistiques à l'aide de l'instruction UPDATE STATISTICS ou de la procédure stockée sp_updatestats.  
  
 La mise à jour des statistiques est l'assurance que les requêtes sont compilées avec des statistiques à jour. Toutefois, la mise à jour des statistiques entraîne une recompilation des requêtes. À ce titre, il est déconseillé de mettre à jour les statistiques de façon trop régulière eu égard aux performances. Un compromis doit être trouvé entre le souhait d'améliorer les plans de requête et le temps nécessaire à la recompilation des requêtes. Ce compromis peut varier en fonction de votre application.  
  
 Dans le cadre d'une mise à jour des statistiques avec UPDATE STATISTICS ou sp_updatestats, nous vous recommandons de maintenir l'option AUTO_UPDATE_STATISTICS activée (valeur ON) de sorte que l'optimiseur de requête continue de mettre à jour les statistiques de façon régulière. Pour plus d’informations sur la façon de mettre à jour les statistiques sur une colonne, un index, une table ou une vue indexée, consultez [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md). Pour plus d’informations sur la mise à jour des statistiques pour toutes les tables définies par l’utilisateur et les tables internes de la base de données, consultez la procédure stockée [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md).  
  
 Pour déterminer la date de la dernière mise à jour des statistiques, utilisez la fonction [STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md) .  
  
 Envisagez de mettre à jour les statistiques dans les cas suivants :  
  
-   lenteur d'exécution des requêtes ;  
  
-   opérations d'insertion appliquées à des colonnes de clés triées par ordre croissant ou décroissant ;  
  
-   opérations de maintenance fraîchement effectuées.  
  
### <a name="query-execution-times-are-slow"></a>Lenteur d'exécution des requêtes  
 Si les temps de réponse des requêtes sont longs ou imprévisibles, assurez-vous que les requêtes disposent de statistiques à jour avant d'exécuter d'autres procédures de dépannage.  
  
### <a name="insert-operations-occur-on-ascending-or-descending-key-columns"></a>Opérations d'insertion appliquées à des colonnes de clés triées par ordre croissant ou décroissant  
 Les statistiques sur les colonnes de clés triées par ordre croissant ou décroissant, telles que les colonnes IDENTITY ou les colonnes de type timestamp en temps réel, peuvent nécessiter des mises à jour plus régulières que celles effectuées par l'optimiseur de requête. Les opérations d'insertion ajoutent de nouvelles valeurs aux colonnes triées par ordre croissant ou décroissant. Le nombre de lignes ajoutées peut s'avérer trop faible pour déclencher une mise à jour des statistiques. Si les statistiques ne sont pas à jour et que les requêtes sélectionnent des lignes récemment ajoutées, les statistiques actuelles ne comporteront pas d'estimations de cardinalité pour ces nouvelles valeurs. Cela peut se traduire par des estimations de cardinalité imprécises et des performances de requêtes en retrait.  
  
 Par exemple, une requête qui sélectionne des dates de commande parmi les plus récentes présentera des estimations de cardinalité imprécises si les statistiques ne sont pas mises à jour pour inclure les estimations de cardinalité des dates de commande les plus récentes.  
  
### <a name="after-maintenance-operations"></a>Opérations de maintenance fraîchement effectuées  
 Envisagez de mettre à jour les statistiques après avoir exécuté des procédures de maintenance qui modifient la distribution des données, telles que la troncation d'une table ou l'exécution d'une insertion en bloc d'un fort pourcentage de lignes. Vous éviterez ainsi des retards dans le traitement ultérieur des requêtes du fait de l'attente des mises à jour automatiques des statistiques.  
  
 Les opérations de reconstruction, de défragmentation ou de réorganisation d'index ne modifient pas la distribution des données. Par conséquent, vous n'avez pas besoin de mettre à jour les statistiques après avoir effectué des opérations ALTER INDEX REBUILD, DBCC REINDEX, DBCC INDEXDEFRAG ou ALTER INDEX REORGANIZE. Si l'optimiseur de requête met effectivement à jour les statistiques lors de la reconstruction d'un index sur une table ou une vue via ALTER INDEX REBUILD ou DBCC DBREINDEX, cette mise à jour des statistiques est une conséquence de la recréation de l'index. L'optimiseur de requête ne met pas à jour les statistiques suite à des opérations DBCC INDEXDEFRAG ou ALTER INDEX REORGANIZE.  
  
  
##  <a name="DesignStatistics"></a> Requêtes pour une utilisation efficace des statistiques  
 Certaines implémentations de requête, telles que les variables locales et les expressions complexes contenues dans le prédicat de requête, peuvent produire des plans de requête non optimaux. Cela peut s'éviter en suivant les recommandations en matière de conception de requêtes pour une utilisation efficace des statistiques. Pour plus d’informations sur les prédicats de requête, consultez [Condition de recherche &#40;Transact-SQL&#41;](../../t-sql/queries/search-condition-transact-sql.md).  
  
 Vous pouvez améliorer les plans de requête en appliquant les recommandations en matière de conception de requêtes pour une utilisation efficace des statistiques. Les *estimations de cardinalité* relatives aux expressions, aux variables et aux fonctions utilisées dans les prédicats de requête s'en trouveront améliorées. Lorsque l'optimiseur de requête ne connaît pas la valeur d'une expression, d'une variable ou d'une fonction, il ne sait pas quelle valeur rechercher dans l'histogramme et ne peut donc pas extraire la meilleure estimation de cardinalité de l'histogramme. Au lieu de cela, l'optimiseur de requête base l'estimation de cardinalité sur le nombre moyen de lignes par valeur distincte pour toutes les lignes échantillonnées dans l'histogramme. Il en résulte des estimations de cardinalité non optimales et une altération potentielle des performances des requêtes.  
  
 Les recommandations suivantes indiquent comment écrire les requêtes pour améliorer les plans de requête à travers l'amélioration des estimations de cardinalité.  
  
### <a name="improving-cardinality-estimates-for-expressions"></a>Amélioration des estimations de cardinalité pour les expressions  
 Pour améliorer les estimations de cardinalité pour les expressions, respectez les principes suivants :  
  
-   Dans la mesure du possible, simplifiez les expressions en y intégrant des constantes. L'optimiseur de requête n'évalue pas toutes les fonctions et les expressions contenant des constantes avant de déterminer les estimations de cardinalité. Par exemple, simplifiez l'expression ABS(`-100) to 100`.  
  
-   Si l'expression utilise plusieurs variables, songez à créer une colonne calculée pour l'expression, puis créez des statistiques ou un index sur la colonne calculée. Par exemple, le prédicat de requête `WHERE PRICE + Tax > 100` bénéficiera peut-être d'une meilleure estimation de cardinalité si vous créez une colonne calculée pour l'expression `Price + Tax`.  
  
### <a name="improving-cardinality-estimates-for-variables-and-functions"></a>Amélioration des estimations de cardinalité pour les variables et les fonctions  
 Pour améliorer les estimations de cardinalité pour les variables et les fonctions, respectez les principes suivants :  
  
-   Si le prédicat de requête utilise une variable locale, envisagez de réécrire la requête de sorte qu'elle utilise un paramètre au lieu d'une variable locale. La valeur d'une variable locale n'est pas connue au moment où l'optimiseur de requête crée le plan d'exécution de requête. Lorsqu'une requête utilise un paramètre, l'optimiseur de requête utilise l'estimation de cardinalité pour la première valeur effective du paramètre qui est transmise à la procédure stockée.  
  
-   Envisagez d'utiliser une table standard ou une table temporaire pour consigner les résultats de fonctions table à instructions multiples. L'optimiseur de requête ne crée pas de statistiques pour les fonctions table à instructions multiples. Du fait de cette approche, l'optimiseur de requête peut créer des statistiques sur les colonnes de table et s'en servir pour créer un meilleur plan de requête.  
  
-   Envisagez d'utiliser une table standard ou une table temporaire en remplacement de variables de table. L'optimiseur de requête ne crée pas de statistiques pour les variables de table. Du fait de cette approche, l'optimiseur de requête peut créer des statistiques sur les colonnes de table et s'en servir pour créer un meilleur plan de requête. Il convient de peser le pour et le contre au moment d'opter pour une table temporaire ou une variable de table : les variables de table utilisées dans les procédures stockées aboutissent à moins de recompilations de ces dernières que les tables temporaires. Selon l'application, l'utilisation d'une table temporaire à la place d'une variable de table n'améliorera pas forcément les performances.  
  
-   Si une procédure stockée contient une requête qui utilise un paramètre transmis, évitez de modifier la valeur du paramètre dans la procédure stockée avant de l'utiliser dans la requête. Les estimations de cardinalité de la requête sont basées sur la valeur du paramètre transmis et non sur la valeur mise à jour. Pour éviter de modifier la valeur du paramètre, vous pouvez réécrire la requête de sorte qu'elle utilise deux procédures stockées.  
  
     Par exemple, la procédure stockée suivante `Sales.GetRecentSales` modifie la valeur du paramètre `@date` lorsque `@date is NULL`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    IF OBJECT_ID ( 'Sales.GetRecentSales', 'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetRecentSales;  
    GO  
    CREATE PROCEDURE Sales.GetRecentSales (@date datetime)  
    AS BEGIN  
        IF @date is NULL  
            SET @date = DATEADD(MONTH, -3, (SELECT MAX(ORDERDATE) FROM Sales.SalesOrderHeader))  
        SELECT * FROM Sales.SalesOrderHeader h, Sales.SalesOrderDetail d  
        WHERE h.SalesOrderID = d.SalesOrderID  
        AND h.OrderDate > @date  
    END  
    GO  
    ```  
  
     Si le premier appel à la procédure stockée `Sales.GetRecentSales` transmet une valeur NULL pour le paramètre `@date` , l'optimiseur de requête compilera la procédure stockée avec l'estimation de cardinalité de `@date = NULL` même si le prédicat de requête n'est pas appelé avec `@date = NULL`. Il se peut que cette estimation de cardinalité soit sensiblement différente du nombre de lignes présenté dans le résultat réel de la requête. En conséquence, l'optimiseur de requête risque de choisir un plan de requête non optimisé. Pour éviter cela, vous pouvez réécrire la procédure stockée dans deux procédures comme dans l'exemple suivant :  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    IF OBJECT_ID ( 'Sales.GetNullRecentSales', 'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetNullRecentSales;  
    GO  
    CREATE PROCEDURE Sales.GetNullRecentSales (@date datetime)  
    AS BEGIN  
        IF @date is NULL  
            SET @date = DATEADD(MONTH, -3, (SELECT MAX(ORDERDATE) FROM Sales.SalesOrderHeader))  
        EXEC Sales.GetNonNullRecentSales @date;  
    END  
    GO  
    IF OBJECT_ID ( 'Sales.GetNonNullRecentSales', 'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetNonNullRecentSales;  
    GO  
    CREATE PROCEDURE Sales.GetNonNullRecentSales (@date datetime)  
    AS BEGIN  
        SELECT * FROM Sales.SalesOrderHeader h, Sales.SalesOrderDetail d  
        WHERE h.SalesOrderID = d.SalesOrderID  
        AND h.OrderDate > @date  
    END  
    GO  
    ```  
  
### <a name="improving-cardinality-estimates-with-query-hints"></a>Amélioration des estimations de cardinalité au moyen d'indicateurs de requête  
 Pour améliorer les estimations de cardinalité des variables locales, vous pouvez utiliser les indicateurs de requête OPTIMIZE FOR ou OPTIMIZE FOR UNKNOWN avec RECOMPILE. Pour plus d’informations, consultez [Indicateurs de requête &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md).  
  
 Pour certaines applications, la recompilation de la requête à chacune de ses exécutions peu prendre trop de temps. L'indicateur de requête OPTIMIZER FOR peut s'avérer utile même si vous n'utilisez pas l'option RECOMPILE. Par exemple, vous pouvez ajouter une option OPTIMIZER FOR à la procédure stockée Sales.GetRecentSales pour spécifier une date précise. L'exemple suivant ajoute l'option OPTIMIZER FOR à la procédure Sales.GetRecentSales.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'Sales.GetRecentSales', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.GetRecentSales;  
GO  
CREATE PROCEDURE Sales.GetRecentSales (@date datetime)  
AS BEGIN  
    IF @date is NULL  
        SET @date = DATEADD(MONTH, -3, (SELECT MAX(ORDERDATE) FROM Sales.SalesOrderHeader))  
    SELECT * FROM Sales.SalesOrderHeader h, Sales.SalesOrderDetail d  
    WHERE h.SalesOrderID = d.SalesOrderID  
    AND h.OrderDate > @date  
    OPTION ( OPTIMIZE FOR ( @date = '2004-05-01 00:00:00.000'))  
END;  
GO  
```  
  
### <a name="improving-cardinality-estimates-with-plan-guides"></a>Amélioration des estimations de cardinalité au moyen de repères de plan  
 Pour certaines applications, les recommandations en matière de conception de requêtes peuvent ne pas s'appliquer, soit parce que vous ne pouvez pas modifier la requête, soit parce que l'utilisation de l'indicateur de requête RECOMPILE peut entraîner un nombre trop important de recompilations. Vous pouvez utiliser des repères de plan pour spécifier d'autres indicateurs, tels que USE PLAN, dans le but de contrôler le comportement de la requête, en attendant de trouver une solution avec l'éditeur de l'application. Pour plus d'informations sur les repères de plan, consultez [Plan Guides](../../relational-databases/performance/plan-guides.md).  
  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [Créer des index filtrés](../../relational-databases/indexes/create-filtered-indexes.md)  
  
  

