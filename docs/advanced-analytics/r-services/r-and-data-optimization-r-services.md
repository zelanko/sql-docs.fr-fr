---
title: "R et optimisation des donn&#233;es (Services de R) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6104878-ed19-47a7-ac37-21e4d6e2a1af
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# R et optimisation des donn&#233;es (Services de R)
Cette rubrique décrit les méthodes de mise à jour de votre code R pour améliorer les performances et d’éviter les problèmes connus.

## Contexte de calcul

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] peut utiliser le __local__ ou __SQL__ contexte de calcul lors de l’analyse. Lorsque vous utilisez le __local__ contexte de calcul, analyse est effectuée sur l’ordinateur client et les données doivent être extraites à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sur le réseau. Le gain de performance générés pour ce transfert réseau dépend de la taille des données transférées, la vitesse du réseau et autres transferts réseau se produisant simultanément.

Si le contexte de calcul est __SQL Server__, puis les fonctions analytiques sont exécutées dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Les données étant locales à la tâche d’analyse, aucun frais de réseau n’est introduite. 

Lorsque vous travaillez avec de grands jeux de données, vous devez toujours utiliser le contexte de calcul SQL.

## Facteurs

Le langage R convertit des chaînes à partir des tables en facteurs. Prennent de nombreux objets de source de données `colInfo` en tant que paramètre pour contrôler la manière dont les colonnes sont traitées. Par exemple, `c(“fruit” = c(type = “factor”, levels=as.character(c(1:3)), newLevels=c(“apple”, “orange”, “banana”)))` sera consommer des entiers de 1, 2 et 3 à partir d’une table et les traiter comme des facteurs avec des niveaux de `apple`, `orange`, et `banana`. 

Scientifiques de données utilisent souvent des variables facteur dans leur formule ; Toutefois, à l’aide de facteurs lorsque la source de données est un entier entraîne une baisse des performances lorsqu’entiers sont convertis en chaînes au moment de l’exécution. Toutefois, si la colonne contient les chaînes, vous pouvez spécifier les niveaux d’avance en utilisant `colInfo`. Dans ce cas, l’instruction équivalente serait  `c(“fruit” = c(type = “factor”, levels= c(“apple”, “orange”, “banana”)))`, qui traite les chaînes comme facteurs lors de leur lecture. 

Pour éviter les conversions d’exécution, envisagez le stockage des niveaux en tant qu’entiers dans la table et leur utilisation comme décrit dans le premier exemple de formule. S’il n’existe aucune différence sémantique entre la génération du modèle, cette approche peut entraîner une amélioration des performances.

## Transformation des données

Scientifiques de données utilisent souvent des fonctions de transformation écrites en langage R dans le cadre de l’analyse. Les fonctions de transformation doivent être appliquées à chaque ligne extraite de la table. Dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], cette transformation se produit en mode batch et implique la communication entre l’interpréteur R et le moteur analytique. Pour effectuer la transformation, les données sont déplacées à partir de SQL vers le moteur analytique, puis vers le processus de l’interpréteur R et inversement. Par conséquent, à l’aide de transformations peut avoirune sérieuse incidence négative sur les performances de l’algorithme, selon la quantité de données impliqués.

Il est plus efficace d’avoir toutes les colonnes nécessaires dans la table ou la vue avant d’effectuer l’analyse, car cela évite les transformations au cours du calcul. Si elle n’est pas possible d’ajouter des colonnes aux tables existantes, envisagez de créer une autre table ou vue avec les colonnes transformées et utiliser une requête appropriée pour extraire les données.

## Traitement par lot

La source de données SQL (`RxSqlServerData`) a une option pour indiquer la taille du lot à l’aide du paramètre `rowsPerRead`. Ce paramètre spécifie le nombre de lignes à traiter à la fois. Au moment de l’exécution, les algorithmes lira numérotés de lignes dans chaque lot spécifié. Par défaut, la valeur de ce paramètre est définie à 50 000, pour vous assurer que les algorithmes peuvent effectuer bien, même sur les ordinateurs avec une mémoire insuffisante. Si l’ordinateur dispose de suffisamment de mémoire, l’augmentation de cette valeur à 500 000 ou même un million génèrent meilleures performances, en particulier pour les grandes tables. 

L’augmentation de cette valeur peut ne pas produire toujours les meilleurs résultats et peut nécessiter des tests pour déterminer la valeur optimale. Les avantages de ce sera plus apparent sur un jeu de données volumineux avec plusieurs processus (`numTasks` définie sur une valeur supérieure à `1`).

## Traitement parallèle

Pour améliorer les performances de l’exécution des fonctions analytiques dans rx [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] s’appuie sur le traitement en parallèle à l’aide du nombre de cœurs disponibles sur le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] machine. Il existe deux façons d’atteindre la parallélisation avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]:

* Lorsque vous utilisez la `sp_execute_external_script` définir une procédure stockée à exécuter un script R, le `@parallel` paramètre `1`. Cela est utile pour les scripts R qui n’utilisent pas les fonctions RevoScaleR, qui sont généralement précédées de « réception ». Si le script utilise les fonctions RevoScaleR, traitement parallèle est géré automatiquement, et vous ne devez pas définir `@parallel` à `1`.

    Si le script R peut être parallélisé et si le [!INCLUDE[tsql_md](../../includes/tsql-md.md)] requête peut être parallélisée, puis [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] créera plusieurs traitements parallèles (jusqu'à la __max degré de parallélisme MAXDOP__ paramètre [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)],) et exécuter le même script sur tous les processus. Chaque processus reçoit uniquement une partie des données, cela n’est pas utile pour les scripts qui doivent consulter toutes les données, tel que lors de l’apprentissage d’un modèle. Toutefois, il est utile lorsque vous effectuez des tâches telles que la prédiction par lot en parallèle. Pour plus d’informations sur l’utilisation de parallélisme avec [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), consultez la __conseils avancée : traitement parallèle__ section de [à l’aide de Code R dans Transact-SQL](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md).

* Lorsque vous utilisez des fonctions de réception avec un contexte de calcul de SQL Server, `numTasks` au nombre de processus que vous souhaitez créer. Le nombre réel de processus créé est déterminé par [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], et peut être inférieure que vous avez demandé. Le nombre de processus créé ne peut jamais être plus __MAXDOP__.

    Si le script R peut être parallélisé et si le [!INCLUDE[tsql_md](../../includes/tsql-md.md)] requête peut être parallélisée, puis [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] créera plusieurs processus parallèles lors de l’exécution des fonctions rx.

Le nombre de processus qui sera créé dépend de divers facteurs tels que la gestion des ressources, l’utilisation actuelle des ressources, les autres sessions et le plan d’exécution pour la requête utilisée par le script R. 

### Parallélisation de la requête

Pour vous assurer que les données peuvent être analysées en parallèle, la requête utilisée pour récupérer les données doit être définie de manière à ce qu’il puisse afficher pour l’exécution parallèle. 

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] prend en charge l’utilisation de sources de données SQL à l’aide de `RxSqlServerData` pour spécifier la source. La source peut être une table ou une requête. Par exemple, les exemples de code suivants que définissent tous deux un objet de source de données R basé sur une requête SQL :
~~~~
RxSqlServerData(table=”airline”, connectionString = sqlConnString)
~~~~

~~~~
RxSqlServerData(sqlquery=”select [ArrDelay],[CRSDepTime],[DayOfWeek] from airlineWithIndex where rowNum <= 100000”, connectionString = sqlConnString)
~~~~ 

Comme les algorithmes analytique tirer de grands volumes de données à partir des tables, il est important de vérifier que la requête fournie pour `RxSqlServerData` est optimisé pour l’exécution en parallèle. Une requête qui n’entraîne pas un plan d’exécution parallèle peut entraîner un processus unique pour le calcul.

[!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] peut être utilisé pour analyser le plan d’exécution et améliorer les performances de la requête. Par exemple, un index manquant sur une table peut affecter le temps nécessaire pour exécuter une requête. Consultez [surveillance et réglage des performances](../../relational-databases/performance/monitor-and-tune-for-performance.md) Pour plus d’informations.

Un autre contrôle qui peut affecter les performances est lorsque la requête extrait plus de colonnes que nécessaire. Par exemple, si une formule est basée sur les colonnes uniquement 3 et la table contient des 30 colonnes, n’utilisez pas une requête comme `select *` ou qui sélectionne le plus de colonnes que nécessaire.

> [!NOTE]
> Si une table est spécifiée dans la source de données au lieu d’une requête, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] en interne détermine les colonnes nécessaires pour récupérer à partir de la table ; Toutefois, cette approche est peu susceptible d’engendrer l’exécution en parallèle.

## Paramètres d'algorithme

De nombreux algorithmes d’apprentissage rx prend en charge les paramètres pour contrôler la façon dont le modèle d’apprentissage est généré. La précision et l’exactitude du modèle est important, les performances de l’algorithme peuvent être tout aussi important. Vous pouvez modifier les paramètres de formation de modèle packageLe pour augmenter la vitesse de calcul et dans de nombreux cas, vous pourrez peut-être améliorer les performances sans réduire la précision ou l’exactitude. 

Par exemple, `rxDTree` prend en charge la `maxDepth` paramètre qui contrôle la profondeur d’arborescence maximale. En tant que `maxDepth` est augmentée, performances peuvent se dégrader, il est donc important d’analyser les avantages de l’augmentation de la profondeur et l’impact sur les performances. 

L’un des paramètres qui peuvent être utilisés avec `rxLinMod` et `rxLogit` est le `cube` argument. Cet argument peut être utilisé lors de la première variable dépendante de la formule est une variable facteur. Si `cube` est défini sur `TRUE`, la régression s’effectue à l’aide d’un inverse partitionnée, il peut plus rapide et utilise moins de mémoire que le calcul de régression standard. Si la formule comporte un grand nombre de variables, le gain de performances peut être significatif.

Le [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) le guide comporte des informations utiles pour contrôler le modèle adaptés à différents algorithmes. Par exemple, avec `rxDTree` vous pouvez contrôler l’équilibre entre la précision de la complexité et la prédiction de temps en ajustant les paramètres tels que `maxNumBins`, `maxDepth`, `maxComplete`, et `maxSurrogate`. Augmenter la profondeur à au-delà de 10 ou 15 peut rendre le calcul très coûteuse.

Pour plus d’informations sur le réglage des performances pour `rxDForest` et `rxDTree`, consultez [options de rxDForest/rxDTree de réglage des performances](https://support.microsoft.com/kb/3104235).

## Modèle et prédiction

Une fois la formation terminée et le meilleur modèle sélectionné, nous vous recommandons de stocker le modèle dans la base de données afin qu’il soit disponible immédiatement pour les prévisions. Pour le traitement transactionnel en ligne qui nécessite la prédiction, charger le modèle précalculé à partir de la base de données pour la prédiction est très efficace. Les exemples de scripts utilisent cette approche pour sérialiser et stocker le modèle dans une table de base de données. Pour la prédiction, le modèle est désérialisé à partir de la base de données.

Certains modèles générés par des algorithmes tels que lm ou glm peuvent être assez volumineux, surtout lorsque utilisée sur un jeu de données volumineux. Il existe des limitations de taille pour les données qui peuvent être stockées dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Vous devez nettoyer le modèle avant de le stocker dans la base de données.

> [!NOTE] Si la prédiction rapide à l’aide d’un modèle stocké et l’intégration de l’analytique dans une application est un scénario important, nous vous recommandons __DeployR__. Il peut être utilisé pour intégrer facilement analytique R dans les applications web, bureau, mobile et du tableau de bord. En particulier, il convient pour le stockage d’un modèle et sur la réalisation de prédiction de ligne unique à l’aide du modèle stocké. Pour plus d’informations, consultez [sur DeployR](https://msdn.microsoft.com/microsoft-r/rserver/deployr-about).

## Voir aussi
[Gestion des ressources](../../advanced-analytics/r-services/resource-governance-for-r-services.md)
[le gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md)

[CRÉER LE POOL DE RESSOURCES EXTERNES](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

 [Guide de réglage de performances SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
 [Configuration de SQL Server pour les Services de R](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
 
 [Étude de cas de performances](../../advanced-analytics/r-services/performance-case-study-r-services.md)
 