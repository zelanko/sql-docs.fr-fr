---
title: "Afficher et synthétiser des données à l’aide de R (procédure pas à pas) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/08/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 358e1431-8f47-4d32-a02f-f90e519eef49
caps.latest.revision: 22
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 8d94b671e88eb512cd763dc7660df6d3ac986370
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---
# <a name="view-and-summarize-data-using-r"></a>Afficher et synthétiser des données à l’aide de R

Maintenant nous allons travailler avec les mêmes données à l’aide de code R. Dans cette leçon, vous apprenez à utiliser les fonctions dans le **RevoScaleR** package.

Un script R est fourni avec cette procédure pas à pas, dans lequel se trouve tout le code nécessaire pour créer l’objet de données, générer des résumés et créer des modèles. Le fichier de script R, **RSQL_RWalkthrough.R**, se trouve à l’emplacement auquel vous avez installé les fichiers de script.

+ Si vous êtes familiarisé avec R, vous pouvez exécuter le script en entier.
+ Pour apprendre à utiliser les RevoScaleR de personnes, ce didacticiel est installé via le script ligne par ligne.
+ Pour exécuter des lignes individuelles du script, vous pouvez mettre en surbrillance une ou plusieurs lignes dans le fichier et appuyer sur Ctrl + Entrée.

> [!TIP]
> Enregistrez votre espace de travail R au cas où vous souhaiteriez effectuer le reste de la procédure pas à pas ultérieurement.  Les objets de données et d’autres variables de cette façon sont prêts pour une réutilisation.

## <a name="define-a-sql-server-compute-context"></a>Définir un contexte de calcul de SQL Server

Microsoft R vous facilite la tâche obtenir des données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser dans votre code R. Le processus est le suivant :
  
- Créer une connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
- Définir une requête qui contient les données dont vous avez besoin, ou spécifier une table ou une vue
- Définir un ou plusieurs contextes de calcul à utiliser lors de l’exécution du code R
- Si vous le souhaitez, définissent les transformations qui sont appliquées à la source de données lors de la lecture de la source

Les étapes suivantes sont toutes les parties du code R et doivent être exécutés dans un environnement R. Nous avons utilisé le Client Microsoft R, car il inclut tous les packages RevoScaleR, ainsi qu’un ensemble de base et léger des outils R.

1. Si le **RevoScaleR** package n'est pas déjà chargé, exécutez cette ligne de code R :

    ```R
    library("RevoScaleR")
    ```

     Les guillemets sont facultatifs, dans ce cas, bien que recommandée.
     
     Si vous obtenez une erreur, assurez-vous que votre environnement de développement R est à l’aide d’une bibliothèque qui inclut le package RevoScaleR. Utilisez une commande comme `.libPaths()` pour afficher le chemin de bibliothèque en cours.

2. Créer la chaîne de connexion pour SQL Server et l’enregistrer dans une variable de R, _connStr_.
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=Your_Database_Name;Uid=Your_User_Name;Pwd=Your_Password"
    ```

    Pour le nom du serveur, vous ne pourrez pas utiliser le nom d’instance, ou vous devrez peut-être qualifier complètement le nom, en fonction de votre réseau.

    Pour l’authentification Windows, la syntaxe est un peu différente :
    
    ```R
    connStrWin <- "Driver=SQL Server;Server=SQL_instance_name;Database=database_name;Trusted_Connection=Yes"
    ```

    Le script R disponible en téléchargement utilise uniquement des connexions SQL. En règle générale, nous vous recommandons d’utiliser l’authentification Windows lorsque cela est possible, pour éviter d’enregistrer les mots de passe dans votre code R. Toutefois, pour vous assurer que le code de ce didacticiel correspond au code téléchargé à partir de Github, nous allons utiliser une connexion SQL pour le reste de la procédure pas à pas.

3. Définir des variables à utiliser pour créer un nouveau _contexte de calcul_. Après avoir créé l’objet de contexte de calcul, vous pouvez l’utiliser pour exécuter le code R sur l’instance de SQL Server.

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - R utilise un répertoire temporaire pour la sérialisation bidirectionnelle des objets R entre votre station de travail et l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez spécifier le répertoire local qui est utilisé en tant que *sqlShareDir*ou accepter la valeur par défaut.
  
    - Utilisez *sqlWait* pour indiquer si vous souhaitez R pour attendre les résultats à partir du serveur.  Pour en savoir plus sur en attente et sans attente travaux, consultez [distribué et le calcul parallèle avec ScaleR dans Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).
  
    - Utilisez l’argument *sqlConsoleOutput* pour indiquer que vous ne souhaitez pas voir la sortie de la console R.


4. Vous appelez le [RxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) constructeur pour créer l’objet de contexte de calcul avec les variables et les chaînes de connexion déjà définies et enregistrez le nouvel objet dans la variable R *sqlcc*.
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. Par défaut, le contexte de calcul est local, vous devez définir explicitement la *active* contexte de calcul.

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + `rxSetComputeContext` retourne sans le montrer le contexte de calcul précédemment actif afin que vous puissiez l’utiliser.
    + `rxGetComputeContext` retourne le contexte de calcul actif.
    
    Notez que le contexte de calcul spécifié affecte uniquement les opérations qui utilisent les fonctions disponibles dans le package **RevoScaleR** ; il n’affecte pas la façon dont les opérations R open source sont effectuées.

## <a name="create-a-data-source-using-rxsqlserver"></a>Créer une source de données à l’aide de RxSqlServer

Dans Microsoft R, un *source de données* est un objet que vous créez à l’aide de fonctions RevoScaleR. L’objet de source de données spécifie un jeu de données que vous souhaitez utiliser pour une tâche, par exemple d’extraction de formation ou d’une fonctionnalité de modèle. Vous pouvez obtenir des données à partir de diverses sources ; Pour obtenir la liste de sources actuellement prises en charge, consultez [RxDataSource](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource).

Version antérieure vous définie par une chaîne de connexion et enregistrer ces informations dans une variable de R. Vous pouvez réutiliser ces informations de connexion pour spécifier les données que vous souhaitez obtenir.

1. Enregistrer une requête SQL en tant qu’une variable de chaîne. La requête définit les données d’apprentissage du modèle.

    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

2. Passez la définition de la requête comme argument à la fonction [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata).

    ```R
    inDataSource <- RxSqlServerData(
      sqlQuery = sampleDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )
    ```
    
    + L’argument  *colClasses* spécifie les types de colonne à utiliser pour le déplacement des données entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et R. Cela est important, car par rapport à R, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des types de données différents et plus nombreux. Pour plus d’informations, consultez [les Types de données et les bibliothèques R](../r/r-libraries-and-data-types.md).
  
    + L’argument *rowsPerRead* est important pour la gestion de l’utilisation de mémoire et les calculs efficace.  La plupart des fonctions analytiques améliorées dans[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] traitent les données en segments et accumulent les résultats intermédiaires. Elles retournent les calculs finaux une fois que toutes les données ont été lues.  En ajoutant le *rowsPerRead* paramètre, vous pouvez contrôler le nombre de lignes de données est lues dans chaque bloc pour le traitement.  Si la valeur de ce paramètre est trop grande, l’accès aux données peut être lent, car vous n’avez pas suffisamment de mémoire pour traiter efficacement un segment de données aussi volumineux.  Sur certains systèmes, en définissant *rowsPerRead* à une valeur trop petite peut également fournir la baisse des performances.

3. À ce stade, vous avez créé le *inDataSource* objet, mais il ne contient pas de données. Les données non extraite à partir de la requête SQL dans l’environnement local jusqu'à ce que vous exécutez une fonction comme [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) ou [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary).

    Toutefois, maintenant que vous avez défini les objets de données, vous pouvez l’utiliser comme argument à d’autres fonctions.

## <a name="use-the-sql-server-data-in-r-summaries"></a>Utiliser les données de SQL Server dans des résumés de R

Dans cette section, vous allez essayer plusieurs des fonctions fournies dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] distantes prise en charge des contextes de calcul. En appliquant des fonctions R à la source de données, vous pouvez Explorer, synthétiser et de graphique le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données.

1. Appelez la fonction [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) pour obtenir la liste des variables dans la source de données et leurs types de données.

    **rxGetVarInfo** est une fonction pratique ; vous pouvez l’appeler sur n’importe quelle image de données, ou sur un jeu de données dans un objet de données à distance, pour obtenir des informations telles que les valeurs maximale et minimale des valeurs, le type de données et le nombre de niveaux dans les colonnes de facteur.
    
    Envisagez d’exécuter cette fonction après tout type d’entrée de données, de transformation de caractéristique ou d’ingénierie de caractéristiques. En procédant ainsi, vous pouvez vous assurer que toutes les fonctionnalités que vous souhaitez utiliser dans votre modèle sont des données attendues de type et éviter les erreurs.
  
    ```R
    rxGetVarInfo(data = inDataSource)
    ```

    **Résultats**
    
    ```
    Var 1: tipped, Type: integer
    Var 2: fare_amount, Type: numeric
    Var 3: passenger_count, Type: integer
    Var 4: trip_time_in_secs, Type: numeric, Storage: int64
    Var 5: trip_distance, Type: numeric
    Var 6: pickup_datetime, Type: character
    Var 7: dropoff_datetime, Type: character
    Var 8: pickup_longitude, Type: numeric
    Var 9: pickup_latitude, Type: numeric
    Var 10: dropoff_longitude, Type: numeric
    ```

2. À présent, appelez la fonction RevoScaleR [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary) pour obtenir des statistiques plus détaillées sur les variables individuelles.

    rxSummary est basée sur la R `summary` de fonctionner, mais présente ses propres avantages et des fonctionnalités supplémentaires. rxSummary fonctionne dans plusieurs contextes de calcul et prend en charge la segmentation.  Vous pouvez également utiliser rxSummary pour transformer les valeurs ou résumer en fonction des niveaux de facteur.
    
    Dans cet exemple, vous Résumez le montant de frais en fonction du nombre de personnes.
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + Le premier argument rxSummary spécifie la formule ou un terme à synthétiser par. Ici, le `F()` fonction est utilisée pour convertir les valeurs dans _passagers\_nombre_ en facteurs avant de synthèse. Vous devez également spécifier la valeur minimale (1) et la valeur maximale (6) pour le _passagers\_nombre_ variable de facteur.
    + Si vous ne spécifiez pas les statistiques de sortie, rxSummary génère par défaut moyenne, StDev, Min, Max et le nombre d’observations valides et manquants.
    + Cet exemple inclut également du code pour effectuer le suivi de l’heure à laquelle la fonction démarre et se termine, afin que vous puissiez comparer les performances.
  
    **Résultats**

    ```
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    Name  Mean    StdDev   Min Max ValidObs MissingObs
    fare_amount:F_passenger_count 12.4875 9.682605 2.5 64  1000     0
    Statistics by category (6 categories):*
    Category                             F_passenger_count Means    StdDev    Min
    fare_amount for F(passenger_count)=1 1                 12.00901  9.219458  2.5
    fare_amount for F(passenger_count)=2 2                 11.61893  8.858739  3.0
    fare_amount for F(passenger_count)=3 3                 14.40196 10.673340  3.5
    fare_amount for F(passenger_count)=4 4                 13.69048  8.647942  4.5
    fare_amount for F(passenger_count)=5 5                 19.30909 14.122969  3.5
    fare_amount for F(passenger_count)=6 6                 12.00000        NA 12.0
    Max ValidObs
    55  666
    52  206
    52   51
    39   21
    64   55
    12    1
    "It takes CPU Time=0.5 seconds, Elapsed Time=4.59 seconds to summarize the inDataSource."
    ```

Si vous avez reçu des résultats différents ? C’est parce que la requête de plus petite en utilisant le mot clé TOP n’est pas garantie pour ramener les mêmes résultats chaque fois.

### <a name="bonus-exercise-on-big-data"></a>Exercice supplémentaire sur les données volumineuses

Essayez de définir une nouvelle chaîne de requête avec toutes les lignes. Nous vous recommandons de que configurer un nouvel objet de source de données pour cette expérience. Vous pouvez également essayer de modifier le *rowsToRead* paramètre pour voir comment il affecte le débit.

```R
bigDataQuery  <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"

bigDataSource <- RxSqlServerData(
      sqlQuery = bigDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )

start.time <- proc.time()
rxSummary(~fare_amount:F(passenger_count,1,6), data = bigDataSource)
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
  Elapsed Time=", round(used.time[3],2),
  " seconds to summarize the inDataSource.", sep=""))
```

> [!TIP]
> Alors que cela est en cours d’exécution, vous pouvez utiliser un outil tel que [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) ou du Générateur de profils SQL pour voir comment la connexion est établie et le code R est exécutée à l’aide des services SQL Server.
> 
> Une autre option consiste à analyser les travaux R en cours d’exécution sur SQL Server à l’aide de ces [des rapports personnalisés](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="next-lesson"></a>Leçon suivante

[Créer des graphiques et des tracés à l’aide de R](walkthrough-create-graphs-and-plots-using-r.md)

## <a name="previous-lesson"></a>Leçon précédente

[Explorer les données à l’aide de SQL](walkthrough-view-and-explore-the-data.md)

