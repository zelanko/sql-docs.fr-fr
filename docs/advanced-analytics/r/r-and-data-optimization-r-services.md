---
title: Optimisation des performances pour l’optimisation des données - SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b6e25ec0c7bc1ce332514910cdaf5cdf9fdb9e07
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432402"
---
# <a name="performance-for-r-services---data-optimization"></a>Performances pour R Services - optimisation des données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article est le troisième d’une série qui décrit l’optimisation des performances pour R Services selon deux études de cas. Cet article traite des optimisations de performances pour R ou Python scripts qui s’exécutent dans SQL Server. Il décrit également les méthodes que vous pouvez utiliser pour mettre à jour votre code R, pour améliorer les performances et d’éviter les problèmes connus.

## <a name="choosing-a-compute-context"></a>Choix d’un contexte de calcul

Dans SQL Server 2016 et 2017, vous pouvez utiliser la **local** ou **SQL** contexte de calcul lors de l’exécution du script R ou Python.

Lorsque vous utilisez le **local** contexte de calcul, analyse est effectuée sur votre ordinateur et non sur le serveur. Par conséquent, si vous obtenez des données à partir de SQL Server à utiliser dans votre code, les données doivent être extraites sur le réseau. L’impact de ce transfert réseau sur les performances est plus ou moins important selon le volume de données transférées, la vitesse du réseau et les autres transferts réseau simultanés.

Lorsque vous utilisez le **contexte de calcul de SQL Server**, le code est exécuté sur le serveur. Si vous obtenez des données à partir de SQL Server, les données doivent être locales sur le serveur qui exécute l’analyse, et par conséquent aucune surcharge réseau n’est introduite. Si vous avez besoin importer des données provenant d’autres sources, envisagez d’organiser ETL au préalable.

Si vous manipulez des jeux de données volumineux, utilisez toujours le contexte de calcul SQL.

## <a name="factors"></a>Facteurs

Le langage R propose le concept de *facteurs*, qui sont une variable spéciale pour les données catégoriques. Les scientifiques des données souvent des variables factor dans leurs formules, étant donné que la gestion des variables catégorielles comme facteurs garantissant que les données est traité correctement par les fonctions machine learning. Pour plus d’informations, consultez [R pour les nuls : Variables de facteur](https://www.dummies.com/programming/r/how-to-look-at-the-structure-of-a-factor-in-r/).

Par sa conception, les variables de facteur peuvent être convertis à partir de chaînes en entiers et revenez à nouveau pour stockage ou de traitement. R `data.frame` fonction gère toutes les chaînes en tant que variables de facteur, sauf si l’argument *stringsasfactors sur* a la valeur **False**. Cela signifie est que les chaînes sont automatiquement converti en un entier pour le traitement et ensuite mappé à la chaîne d’origine.

Si les données source à des facteurs externes sont stockées sous forme d’entier, les performances peuvent diminuer, car R convertit les entiers facteur en chaînes au moment de l’exécution et qu’il exécute ensuite son propre conversion de chaîne en entier interne.

Pour éviter ces conversions d’exécution, pensez à stocker les valeurs en tant qu’entiers dans la table SQL Server et à l’aide de la _colInfo_ argument pour spécifier les niveaux pour la colonne utilisée comme facteur. La plupart des objets de source de données dans RevoScaleR prennent le paramètre _colInfo_. Ce paramètre vous permet de nommer les variables utilisées par la source de données, spécifiez leur type et définir les niveaux de variables ou des transformations sur les valeurs de colonne.

Par exemple, l’appel de fonction R suivant obtient les entiers 1, 2 et 3 à partir d’une table, mais mappe les valeurs à un facteur avec des niveaux « apple », « orange » et « banana ».

```R
c("fruit" = c(type = "factor", levels=as.character(c(1:3)), newLevels=c("apple", "orange", "banana")))
```

Lors de la colonne source contient des chaînes, c’est plus efficace pour spécifier les niveaux préalable à l’aide de l’heure la _colInfo_ paramètre. Par exemple, le code R suivant traite les chaînes comme des facteurs lors de leur lecture.

```R
c("fruit" = c(type = "factor", levels= c("apple", "orange", "banana")))
```

S’il n’existe aucune différence sémantique dans la génération du modèle, cette dernière approche peut entraîner une amélioration des performances.

## <a name="data-transformations"></a>Transformations de données

Les « scientifiques des données » utilisent souvent des fonctions de transformation écrites en langage R pour leurs analyses. La fonction de transformation est appliquée à chaque ligne récupérée à partir de la table. Dans SQL Server, ces transformations sont appliquées à toutes les lignes récupérées dans un lot, ce qui nécessite la communication entre l’interpréteur R et le moteur analytique. Les données sont transférées de SQL vers le moteur analytique, puis vers le processus de l’interpréteur R, avant d’être renvoyées.

Pour cette raison, l’utilisation de transformations dans le cadre de votre code R peut avoir un effet négatif significatif sur les performances de l’algorithme, selon la quantité de données impliquées.

Il est plus efficace d’avoir toutes les colonnes nécessaires dans la table ou vue avant d’effectuer l’analyse et éviter des transformations lors du traitement. Si vous ne pouvez pas ajouter de colonnes aux tables existantes, créez une autre table ou vue contenant les colonnes transformées, puis utilisez une requête appropriée pour récupérer les données.

## <a name="batch-row-reads"></a>Lit les lignes du lot

Si vous utilisez une source de données SQL Server (`RxSqlServerData`) dans votre code, nous vous recommandons d’essayer en utilisant le paramètre _rowsPerRead_ pour spécifier la taille de lot. Ce paramètre définit le nombre de lignes qui sont interrogées et envoyé au script externe pour traitement. Au moment de l’exécution, l’algorithme voit uniquement le nombre spécifié de lignes dans chaque lot.

La possibilité de contrôler la quantité de données qui sont traitées à la fois peut vous aider à résoudre ou éviter tout problème. Par exemple, si votre jeu de données d’entrée est très large (contenant de nombreuses colonnes), ou si le jeu de données a plusieurs colonnes volumineuses (par exemple, texte libre), vous pouvez réduire la taille de lot pour éviter la pagination des données mémoire insuffisante.

Par défaut, la valeur de ce paramètre est définie sur 50000, pour garantir une performance correcte même sur des ordinateurs avec une mémoire insuffisante. Si le serveur dispose de suffisamment de mémoire disponible, l’augmentation de cette valeur à 500 000, voire à un million peut produire meilleures performances, en particulier pour les tables volumineuses.

Les avantages de l’augmentation de taille de lot deviennent évidents sur un jeu de données volumineux et une tâche qui peut s’exécuter sur plusieurs processus. Toutefois, l’augmentation de cette valeur ne produit pas toujours les meilleurs résultats. Nous vous recommandons de tester avec vos données et l’algorithme permettant de déterminer la valeur optimale.

## <a name="parallel-processing"></a>traitement parallèle

Pour améliorer les performances de **rx** des fonctions d’analyse, vous pouvez exploiter la possibilité d’exécuter des tâches en parallèle à l’aide de cœurs disponibles sur l’ordinateur serveur de SQL Server.

Il existe deux façons de parallélisation avec R dans SQL Server :

-   **Utilisez \@parallèles.** Si vous utilisez la procédure stockée `sp_execute_external_script` pour exécuter un script R, définissez le paramètre `@parallel` à `1`. Ceci est la meilleure méthode si votre script R effectue **pas** utiliser les fonctions RevoScaleR, qui ont d’autres mécanismes pour le traitement. Si votre script utilise les fonctions RevoScaleR (généralement le préfixe « rx »), le traitement parallèle est effectué automatiquement et vous n’avez pas besoin de définir explicitement `@parallel` à `1`.

    Si le script R peut être parallélisé, et si la requête SQL peut être parallélisée, le moteur de base de données crée plusieurs processus parallèles. Le nombre maximal de processus qui peuvent être créées est égal à la **degré maximal de parallélisme** paramètre (MAXDOP) pour l’instance. Tous les processus puis exécutez le même script, mais reçoit uniquement une partie des données.
    
    Par conséquent, cette méthode n’est pas utile avec des scripts qui doivent voir toutes les données, par exemple quand un modèle d’apprentissage. Au contraire, cette méthode est utile pour effectuer certaines tâches, comme la prédiction par lot en parallèle. Pour plus d’informations sur l’utilisation de parallélisme avec `sp_execute_external_script`, consultez le **avancé conseils : traitement parallèle** section de [à l’aide de Code R dans Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

-   **Utiliser numTasks = 1.** Lorsque vous utilisez **rx** fonctions dans un contexte de calcul SQL Server, définissez la valeur de la _numTasks_ paramètre pour le nombre de processus que vous souhaitez créer. Le nombre de processus créés ne peut jamais être plus de **MAXDOP**; Toutefois, le nombre réel de processus créés est déterminé par le moteur de base de données et peut être l’inférieure à vous être demandée.

    Si le script R peut être parallélisé, et si la requête SQL peut être parallélisée, SQL Server crée plusieurs processus parallèles lors de l’exécution des fonctions rx. Le nombre réel de processus créés dépend de divers facteurs tels que la gouvernance des ressources, l’utilisation actuelle des ressources, les autres sessions et le plan d’exécution de requête pour la requête utilisée avec le script R.

## <a name="query-parallelization"></a>Parallélisation de requêtes

Microsoft r, vous pouvez travailler avec des sources de données SQL Server en définissant vos données comme un objet de source de données RxSqlServerData.

Crée une source de données basée sur une table entière ou une vue :

```R
RxSqlServerData(table= "airline", connectionString = sqlConnString)
```

Crée une source de données basée sur une requête SQL :

```R
RxSqlServerData(sqlQuery= "SELECT [ArrDelay],[CRSDepTime],[DayOfWeek] FROM  airlineWithIndex WHERE rowNum <= 100000", connectionString = sqlConnString)
```

> [!NOTE]
> Si une table est spécifiée dans la source de données au lieu d’une requête, R Services utilise l’heuristique interne pour détermine les colonnes nécessaires pour extraire à partir de la table ; Toutefois, cette approche est peu probable que l’exécution parallèle.

Pour vous assurer que les données peuvent être analysées en parallèle, la requête utilisée pour récupérer les données doit être formée de manière à ce que le moteur de base de données peut créer un plan de requête parallèle. Si le code ou l’algorithme utilise des volumes importants de données, assurez-vous que la requête fournie à `RxSqlServerData` est optimisé pour l’exécution parallèle. Une requête qui ne retourne pas de plan d’exécution parallèle peut générer un processus unique pour le calcul.

Si vous avez besoin travailler avec les jeux de données volumineux, utilisez Management Studio ou un autre analyseur de requêtes SQL avant d’exécuter votre code R, pour analyser le plan d’exécution. Prenez ensuite les étapes recommandées pour améliorer les performances de la requête. Par exemple, l’absence d’un index sur une table peut faire augmenter le temps d’exécution d’une requête. Pour plus d’informations, consultez [surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md).

Une autre erreur courante qui peut affecter les performances est qu’une requête récupère plus de colonnes que nécessaire. Par exemple, si une formule est basée sur trois colonnes seulement, mais votre table source possède des 30 colonnes, vous déplacez des données inutilement.

 + Évitez d’utiliser `SELECT *`!
 + Prendre un certain temps pour vérifier les colonnes dans le jeu de données et identifier uniquement celles qui sont nécessaires pour l’analyse
 + Supprimez de vos requêtes de toutes les colonnes qui contiennent des types de données qui ne sont pas compatibles avec le code R, comme les GUID et ROWGUID
 + Recherchez des formats non pris en charge de date et heure
 + Au lieu de charger une table, créer une vue qui sélectionne certaines valeurs ou effectue un cast de colonnes pour éviter les erreurs de conversion

## <a name="optimizing-the-machine-learning-algorithm"></a>Optimisation de l’algorithme d’apprentissage automatique

Cette section fournit des conseils et divers ressources qui sont spécifiques à RevoScaleR et d’autres options dans Microsoft R.

> [!TIP]
> Une description générale de l’optimisation de R est hors de la portée de cet article. Toutefois, si vous avez besoin rendre votre code plus rapide, nous recommandons l’article populaire, [le R Inferno](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf). Il couvre les constructions de programmation en R et les pièges courants dans le langage de diagrammes vivants et les détails et fournit de nombreux exemples spécifiques de techniques de programmation R.

### <a name="optimizations-for-revoscaler"></a>Optimisations de RevoScaleR

De nombreux algorithmes RevoScaleR prennent en charge les paramètres pour contrôler la façon dont le modèle formé est généré. La précision et l’exactitude du modèle est important, les performances de l’algorithme peuvent être tout aussi important. Pour obtenir le juste équilibre entre exactitude et les temps d’apprentissage, vous pouvez modifier les paramètres pour augmenter la vitesse de calcul et dans de nombreux cas, améliorer les performances sans réduire la précision et l’exactitude.

+ [rxDTree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)

    `rxDTree` prend en charge la `maxDepth` paramètre qui contrôle la profondeur de l’arbre de décision. En tant que `maxDepth` est augmentée, performances peuvent se dégrader, il est donc important d’analyser les avantages de l’augmentation de la profondeur et réduit les performances.

    Vous pouvez également contrôler l’équilibre entre la précision de la complexité et de prédiction du temps en ajustant les paramètres `maxNumBins`, `maxDepth`, `maxComplete`, et `maxSurrogate`. L’augmentation de la profondeur au-delà de 10 ou 15 peut rendre le calcul très coûteux.

+ [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)

    Essayez d’utiliser le `cube` argument si la première variable dépendante dans la formule est une variable de facteur.
    
    Lorsque `cube` est défini sur `TRUE`, la régression est effectuée à l’aide d’inverse partitionnée, ce qui peut être plus rapide et utilise moins de mémoire calcul de régression standard. Si la formule contient un grand nombre de variables, le gain de performance peut être significatif.

+ [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)

    Utilisez le `cube` argument si la première variable dépendante est une variable de facteur.
    
    Lorsque `cube` a la valeur `TRUE`, l’algorithme utilise inverse partitionnée, qui peut être plus rapide et utilise moins de mémoire. Si la formule contient un grand nombre de variables, le gain de performance peut être significatif.

Pour obtenir des conseils supplémentaires sur l’optimisation de RevoScaleR, consultez ces articles :

+ Article du support technique : [Options pour rxDForest et rxDTree de réglage des performances](https://support.microsoft.com/kb/3104235)

+ Les méthodes de modèle de contrôle s’intègrent dans un modèle d’arbre de décision optimisé : [Estimation des modèles à l’aide de Gradient stochastique Boosting](https://docs.microsoft.com/r-server/r/how-to-revoscaler-boosting)

+ Vue d’ensemble de la façon dont RevoScaleR déplace et traite les données : [Écrire des algorithmes de segmentation personnalisés de ScaleR](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ Modèle de programmation pour RevoScaleR : [La gestion des threads dans RevoScaleR](https://docs.microsoft.com/r-server/r/how-to-developer-manage-threads)

+ Référence de fonction pour [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

+ Référence de fonction pour [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)

### <a name="use-microsoftml"></a>Utiliser MicrosoftML

Nous vous recommandons également que vous recherchez dans le nouvel **MicrosoftML** package, qui fournit des algorithmes d’apprentissage automatique évolutif qui peuvent utiliser les contextes de calcul et les transformations fournies par RevoScaleR.

+ [Prise en main MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

+ [Comment choisir un algorithme de MicrosoftML](https://docs.microsoft.com/r-server/r/how-to-choose-microsoftml-algorithms-cheatsheet)

### <a name="operationalize-a-solution-using-microsoft-r-server"></a>Faire fonctionner une solution à l’aide de Microsoft R Server

Si votre scénario implique la prédiction rapide à l’aide d’un modèle stocké, ou l’intégration d’apprentissage automatique dans une application, vous pouvez utiliser la [Opérationnalisation](https://docs.microsoft.com/r-server/what-is-operationalization) fonctionnalités dans Microsoft R Server (anciennement appelées DeployR).

+ Comme un **scientifique des données**, utilisez le [package mrsdeploy](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package) partager du code R avec d’autres ordinateurs et d’intégrer l’analytique R à l’intérieur d’applications web, bureau, mobiles et tableau de bord : [Comment publier et gérer les services web de R dans R Server](https://docs.microsoft.com/r-server/operationalize/how-to-deploy-web-service-publish-manage-in-r)

+ Comme un **administrateur**, apprenez à gérer les packages, surveiller les nœuds de site web et les nœuds de calcul et contrôler la sécurité sur les travaux R : [Comment interagir avec et consommer des services web dans R](https://docs.microsoft.com/r-server/operationalize/how-to-consume-web-service-interact-in-r)

## <a name="articles-in-this-series"></a>Articles de cette série

[Performances optimisation pour R - introduction](sql-server-r-services-performance-tuning.md)

[Optimisation des performances pour R - configuration de SQL Server](sql-server-configuration-r-services.md)

[Optimisation des performances pour R - R l’optimisation de code et des données](r-and-data-optimization-r-services.md)

[Paramétrage des performances - résultats de l’étude de cas](performance-case-study-r-services.md)
