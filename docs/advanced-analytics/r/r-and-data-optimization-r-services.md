---
title: Réglage des performances pour l’optimisation des données
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a8143bae69e85ecf0056dcb9433707a681a69077
ms.sourcegitcommit: 2f56848ec422845ee81fb84ed321a716c677aa0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71271892"
---
# <a name="performance-for-r-services---data-optimization"></a>Performances pour R services-optimisation des données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article est le troisième d’une série qui décrit l’optimisation des performances pour R services sur la base de deux études de cas. Cet article traite des optimisations de performances pour les scripts R ou python qui s’exécutent dans SQL Server. Elle décrit également les méthodes que vous pouvez utiliser pour mettre à jour votre code R afin d’améliorer les performances et d’éviter les problèmes connus.

## <a name="choosing-a-compute-context"></a>Choix d’un contexte de calcul

Dans SQL Server 2016 et 2017, vous pouvez utiliser le contexte de calcul **local** ou **SQL** lors de l’exécution d’un script R ou python.

Lorsque vous utilisez le contexte de calcul **local** , l’analyse est effectuée sur votre ordinateur et non sur le serveur. Par conséquent, si vous obtenez des données de SQL Server à utiliser dans votre code, les données doivent être récupérées sur le réseau. L’impact de ce transfert réseau sur les performances est plus ou moins important selon le volume de données transférées, la vitesse du réseau et les autres transferts réseau simultanés.

Lorsque vous utilisez le **contexte de calcul SQL Server**, le code est exécuté sur le serveur. Si vous obtenez des données à partir de SQL Server, les données doivent être locales sur le serveur qui exécute l’analyse, et par conséquent, aucune surcharge du réseau n’est introduite. Si vous devez importer des données à partir d’autres sources, envisagez d’organiser ETL au préalable.

Si vous manipulez des jeux de données volumineux, utilisez toujours le contexte de calcul SQL.

## <a name="factors"></a>Facteurs

Le langage R présente le concept de *facteurs*, qui sont des variables spéciales pour les données catégoriques. Les scientifiques des données utilisent souvent des variables de facteur dans leur formule, car la gestion des variables catégoriques en tant que facteurs permet de s’assurer que les données sont traitées correctement par Machine Learning fonctions. Pour plus d’informations, [consultez R pour les fantômes: Variables](https://www.dummies.com/programming/r/how-to-look-at-the-structure-of-a-factor-in-r/)de facteur.

Par défaut, les variables de facteur peuvent être converties de chaînes en entiers, puis de nouveau pour le stockage ou le traitement. La fonction `data.frame` R gère toutes les chaînes en tant que variables de facteur, sauf si l’argument *stringsAsFactors* est défini sur **false**. Cela signifie que les chaînes sont automatiquement converties en un entier à traiter, puis remappées à la chaîne d’origine.

Si les données sources des facteurs sont stockées sous la forme d’un entier, les performances peuvent en pâtir, car R convertit les entiers de facteur en chaînes au moment de l’exécution, puis effectue sa propre conversion de chaîne en entier interne.

Pour éviter de telles conversions au moment de l’exécution, envisagez de stocker les valeurs comme des entiers dans la table SQL Server et d’utiliser l’argument _colInfo_ pour spécifier les niveaux de la colonne utilisée comme facteur. La plupart des objets de source de données dans RevoScaleR prennent le paramètre _colInfo_. Vous utilisez ce paramètre pour nommer les variables utilisées par la source de données, spécifier leur type et définir les niveaux de variables ou les transformations sur les valeurs de colonne.

Par exemple, l’appel de fonction R suivant obtient les entiers 1, 2 et 3 d’une table, mais mappe les valeurs à un facteur avec les niveaux «Apple», «orange» et «Banana».

```R
c("fruit" = c(type = "factor", levels=as.character(c(1:3)), newLevels=c("apple", "orange", "banana")))
```

Lorsque la colonne source contient des chaînes, il est toujours plus efficace de spécifier les niveaux à l’avance à l’aide du paramètre _colInfo_ . Par exemple, le code R suivant traite les chaînes comme des facteurs tels qu’ils sont lus.

```R
c("fruit" = c(type = "factor", levels= c("apple", "orange", "banana")))
```

S’il n’existe aucune différence sémantique dans la génération du modèle, cette dernière approche peut améliorer les performances.

## <a name="data-transformations"></a>Transformations de données

Les « scientifiques des données » utilisent souvent des fonctions de transformation écrites en langage R pour leurs analyses. La fonction de transformation est appliquée à chaque ligne extraite de la table. Dans SQL Server, ces transformations sont appliquées à toutes les lignes récupérées dans un lot, ce qui nécessite une communication entre l’interpréteur R et le moteur d’analyse. Les données sont transférées de SQL vers le moteur analytique, puis vers le processus de l’interpréteur R, avant d’être renvoyées.

Pour cette raison, l’utilisation de transformations dans le cadre de votre code R peut avoir un effet négatif significatif sur les performances de l’algorithme, en fonction de la quantité de données impliquées.

Il est plus efficace d’avoir toutes les colonnes nécessaires dans la table ou la vue avant d’effectuer l’analyse et d’éviter les transformations pendant le calcul. Si vous ne pouvez pas ajouter de colonnes aux tables existantes, créez une autre table ou vue contenant les colonnes transformées, puis utilisez une requête appropriée pour récupérer les données.

## <a name="batch-row-reads"></a>Lectures de lignes par lot

Si vous utilisez une source de données SQL Server`RxSqlServerData`() dans votre code, nous vous recommandons d’essayer d’utiliser le paramètre _rowsPerRead_ pour spécifier la taille du lot. Ce paramètre définit le nombre de lignes interrogées, puis envoyées au script externe pour traitement. Au moment de l’exécution, l’algorithme ne voit que le nombre spécifié de lignes dans chaque lot.

La possibilité de contrôler la quantité de données traitées à la fois peut vous aider à résoudre ou à éviter les problèmes. Par exemple, si votre jeu de données d’entrée est très large (comporte de nombreuses colonnes), ou si le jeu de données comporte quelques colonnes de grande taille (par exemple, du texte libre), vous pouvez réduire la taille du lot afin d’éviter la pagination des données en mémoire.

Par défaut, la valeur de ce paramètre est définie sur 50000 pour garantir des performances correctes même sur les ordinateurs avec une mémoire insuffisante. Si le serveur dispose de suffisamment de mémoire disponible, le fait d’augmenter cette valeur à 500 000 ou même un million peut offrir de meilleures performances, en particulier pour les tables volumineuses.

Les avantages de l’amélioration de la taille des lots deviennent évidents sur un jeu de données volumineux et dans une tâche qui peut s’exécuter sur plusieurs processus. Toutefois, l’augmentation de cette valeur ne produit pas toujours les meilleurs résultats. Nous vous recommandons d’expérimenter vos données et algorithmes pour déterminer la valeur optimale.

## <a name="parallel-processing"></a>Traitement parallèle

Pour améliorer les performances des fonctions analytiques **RX** , vous pouvez tirer parti de la capacité des SQL Server à exécuter des tâches en parallèle à l’aide de cœurs disponibles sur l’ordinateur serveur.

Il existe deux façons d’effectuer la parallélisation avec R dans SQL Server:

-   **Utilisez \@Parallel.** Si vous utilisez la procédure stockée `sp_execute_external_script` pour exécuter un script R, définissez le paramètre `@parallel` à `1`. Il s’agit de la meilleure méthode si votre script R n’utilise **pas** de fonctions RevoScaleR, qui ont d’autres mécanismes de traitement. Si votre script utilise des fonctions RevoScaleR (généralement préfixé avec «RX»), le traitement parallèle est effectué automatiquement et vous n’avez pas besoin de `@parallel` définir `1`explicitement sur.

    Si le script R peut être parallélisée et que la requête SQL peut être parallélisée, le moteur de base de données crée plusieurs processus parallèles. Le nombre maximal de processus qui peuvent être créés est égal au paramètre de **degré maximal de parallélisme** (MAXDOP) pour l’instance. Tous les processus exécutent ensuite le même script, mais ne reçoivent qu’une partie des données.
    
    Par conséquent, cette méthode n’est pas utile avec les scripts qui doivent voir toutes les données, par exemple lors de l’apprentissage d’un modèle. Au contraire, cette méthode est utile pour effectuer certaines tâches, comme la prédiction par lot en parallèle. Pour plus d’informations sur l’utilisation du `sp_execute_external_script`parallélisme avec, consultez la section **conseils avancés: traitement parallèle** de [à l’aide de code R dans Transact-SQL](../tutorials/quickstart-r-create-script.md).

-   **Utilisez numTasks = 1.** Lorsque vous utilisez des fonctions **RX** dans un contexte de calcul SQL Server, définissez la valeur du paramètre _numTasks_ sur le nombre de processus que vous souhaitez créer. Le nombre de processus créés ne peut jamais être supérieur à **MAXDOP**; Toutefois, le nombre réel de processus créés est déterminé par le moteur de base de données et peut être inférieur à celui que vous avez demandé.

    Si le script R peut être parallélisée, et si la requête SQL peut être parallélisée, SQL Server crée plusieurs processus parallèles lors de l’exécution des fonctions RX. Le nombre réel de processus créés dépend de divers facteurs, tels que la gouvernance des ressources, l’utilisation actuelle des ressources, les autres sessions et le plan d’exécution de requête pour la requête utilisée avec le script R.

## <a name="query-parallelization"></a>Parallélisation des requêtes

Dans Microsoft R, vous pouvez utiliser SQL Server sources de données en définissant vos données en tant qu’objet de source de données RxSqlServerData.

Crée une source de données basée sur une table ou une vue entière:

```R
RxSqlServerData(table= "airline", connectionString = sqlConnString)
```

Crée une source de données basée sur une requête SQL:

```R
RxSqlServerData(sqlQuery= "SELECT [ArrDelay],[CRSDepTime],[DayOfWeek] FROM  airlineWithIndex WHERE rowNum <= 100000", connectionString = sqlConnString)
```

> [!NOTE]
> Si une table est spécifiée dans la source de données au lieu d’une requête, R Services utilise l’heuristique interne pour déterminer les colonnes nécessaires à l’extraction de la table. Toutefois, cette approche est peu susceptible d’entraîner une exécution parallèle.

Pour vous assurer que les données peuvent être analysées en parallèle, la requête utilisée pour récupérer les données doit être encadrée de telle sorte que le moteur de base de données puisse créer un plan de requête parallèle. Si le code ou l’algorithme utilise de grands volumes de données, assurez-vous `RxSqlServerData` que la requête donnée à est optimisée pour une exécution en parallèle. Une requête qui ne retourne pas de plan d’exécution parallèle peut générer un processus unique pour le calcul.

Si vous avez besoin de travailler avec des jeux de données volumineux, utilisez Management Studio ou un autre analyseur de requêtes SQL avant d’exécuter votre code R pour analyser le plan d’exécution. Ensuite, prenez les mesures recommandées pour améliorer les performances de la requête. Par exemple, l’absence d’un index sur une table peut faire augmenter le temps d’exécution d’une requête. Pour plus d’informations, consultez [surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md).

Une autre erreur courante qui peut affecter les performances est qu’une requête récupère plus de colonnes que nécessaire. Par exemple, si une formule est basée sur uniquement trois colonnes, mais que votre table source comporte 30 colonnes, vous déplacez des données inutilement.

 + Évitez d' `SELECT *`utiliser!
 + Prenez le temps de passer en revue les colonnes du jeu de données et d’identifier uniquement celles qui sont nécessaires à l’analyse
 + Supprimez de vos requêtes toutes les colonnes qui contiennent des types de données qui ne sont pas compatibles avec le code R, comme les GUID et rowguid
 + Vérifier les formats de date et d’heure non pris en charge
 + Au lieu de charger une table, créez une vue qui sélectionne certaines valeurs ou convertit des colonnes pour éviter les erreurs de conversion

## <a name="optimizing-the-machine-learning-algorithm"></a>Optimisation de l’algorithme de Machine Learning

Cette section fournit des conseils et des ressources divers propres à RevoScaleR et à d’autres options de Microsoft R.

> [!TIP]
> La description générale de l’optimisation de R n’est pas abordée dans cet article. Toutefois, si vous avez besoin de rendre votre code plus rapide, nous vous recommandons l’article populaire, [Inferno R](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf). Il aborde les constructions de programmation en R et les pièges courants dans le langage et les détails vif, et fournit de nombreux exemples spécifiques de techniques de programmation R.

### <a name="optimizations-for-revoscaler"></a>Optimisations pour RevoScaleR

De nombreux algorithmes RevoScaleR prennent en charge les paramètres pour contrôler la façon dont le modèle formé est généré. Bien que l’exactitude et l’exactitude du modèle soient importantes, les performances de l’algorithme peuvent être tout aussi importantes. Pour bénéficier d’un juste équilibre entre la précision et le temps de formation, vous pouvez modifier les paramètres pour augmenter la vitesse de calcul et, dans de nombreux cas, améliorer les performances sans réduire la précision ou l’exactitude.

+ [rxDTree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)

    `rxDTree`prend en `maxDepth` charge le paramètre, qui contrôle la profondeur de l’arbre de décision. En `maxDepth` augmentant, les performances peuvent se dégrader. il est donc important d’analyser les avantages liés à l’augmentation de la profondeur et à l’impact sur les performances.

    Vous pouvez également contrôler l’équilibre entre la complexité du temps et la précision de la prédiction `maxNumBins`en `maxDepth`réglant des `maxSurrogate`paramètres tels que `maxComplete`,, et. L’augmentation de la profondeur au-delà de 10 ou 15 peut rendre le calcul très coûteux.

+ [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)

    Essayez d’utiliser `cube` l’argument si la première variable dépendante de la formule est une variable facteur.
    
    Lorsque `cube` a la `TRUE`valeur, la régression est effectuée à l’aide d’un inverse partitionné, ce qui peut être plus rapide et utiliser moins de mémoire que le calcul de régression standard. Si la formule contient un grand nombre de variables, le gain de performance peut être significatif.

+ [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)

    Utilisez l' `cube` argument si la première variable dépendante est une variable facteur.
    
    Lorsque `cube` a la `TRUE`valeur, l’algorithme utilise un inverse partitionné, ce qui peut être plus rapide et utiliser moins de mémoire. Si la formule contient un grand nombre de variables, le gain de performance peut être significatif.

Pour obtenir des conseils supplémentaires sur l’optimisation de RevoScaleR, consultez les articles suivants:

+ Article de support: [Options de réglage des performances pour rxDForest et rxDTree](https://support.microsoft.com/kb/3104235)

+ Méthodes de contrôle de l’ajustement du modèle dans un modèle d’arborescence augmentée: [Estimation des modèles à l’aide de l’accélération du dégradé stochastique](https://docs.microsoft.com/r-server/r/how-to-revoscaler-boosting)

+ Vue d’ensemble de la façon dont RevoScaleR déplace et traite les données: [Écrire des algorithmes de segmentation personnalisés dans Scaler](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ Modèle de programmation pour RevoScaleR: [Gestion des threads dans RevoScaleR](https://docs.microsoft.com/r-server/r/how-to-developer-manage-threads)

+ Référence de fonction pour [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

+ Référence de fonction pour [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)

### <a name="use-microsoftml"></a>Utiliser MicrosoftML

Nous vous recommandons également d’examiner le nouveau package **MicrosoftML** , qui fournit des algorithmes de machine learning évolutifs qui peuvent utiliser les contextes de calcul et les transformations fournis par RevoScaleR.

+ [Prise en main de MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

+ [Comment choisir un algorithme MicrosoftML](https://docs.microsoft.com/r-server/r/how-to-choose-microsoftml-algorithms-cheatsheet)

### <a name="operationalize-a-solution-using-microsoft-r-server"></a>Rendre une solution opérationnelle à l’aide de Microsoft R Server

Si votre scénario implique une prédiction rapide à l’aide d’un modèle stocké, ou l’intégration d’Machine Learning dans une application, vous pouvez utiliser les fonctionnalités de la fonctionnalité de [fonctionnement](https://docs.microsoft.com/r-server/what-is-operationalization) de Microsoft R Server (anciennement déployeur).

+ En tant que **scientifique des données**, utilisez le [package mrsdeploy](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package) pour partager du code r avec d’autres ordinateurs et intégrer r Analytics dans des applications Web, de bureau, mobiles et de tableau de bord: [Comment publier et gérer des services Web R dans R Server](https://docs.microsoft.com/r-server/operationalize/how-to-deploy-web-service-publish-manage-in-r)

+ En tant qu' **administrateur**, Découvrez comment gérer des packages, surveiller des nœuds Web et des nœuds de calcul, et contrôler la sécurité sur les travaux R: [Comment interagir avec les services Web et les utiliser dans R](https://docs.microsoft.com/r-server/operationalize/how-to-consume-web-service-interact-in-r)

## <a name="articles-in-this-series"></a>Articles de cette série

[Réglage des performances pour R-introduction](sql-server-r-services-performance-tuning.md)

[Réglage des performances pour la configuration de R-SQL Server](sql-server-configuration-r-services.md)

[Réglage des performances pour le code R-R et l’optimisation des données](r-and-data-optimization-r-services.md)

[Réglage des performances-résultats de l’étude de cas](performance-case-study-r-services.md)
