---
title: Afficher et résumer les données à l’aide de R (procédure pas à pas) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/02/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1d6c225b3ec6b2a7a80dea155b564b94ecab60fb
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51032886"
---
# <a name="view-and-summarize-data-using-r"></a>Afficher et résumer les données à l’aide de R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Maintenant nous allons travailler avec les mêmes données à l’aide de code R. Dans cette leçon, vous allez apprendre à utiliser les fonctions dans le **RevoScaleR** package.

Un script R est fourni avec cette procédure pas à pas, dans lequel se trouve tout le code nécessaire pour créer l’objet de données, générer des résumés et créer des modèles. Le fichier de script R, **RSQL_RWalkthrough.R**, se trouve à l’emplacement auquel vous avez installé les fichiers de script.

+ Si vous êtes familiarisé avec R, vous pouvez exécuter le script en entier.
+ Pour les personnes apprennent à utiliser RevoScaleR, ce didacticiel passe en revue le script ligne par ligne.
+ Pour exécuter des lignes individuelles du script, vous pouvez mettre en surbrillance une ou plusieurs lignes dans le fichier et appuyer sur Ctrl + Entrée.

> [!TIP]
> Enregistrez votre espace de travail R au cas où vous souhaiteriez effectuer le reste de la procédure pas à pas ultérieurement.  Les objets de données et d’autres variables de cette façon sont prêts pour une réutilisation.

## <a name="define-a-sql-server-compute-context"></a>Définir un contexte de calcul de SQL Server

Microsoft R rend facile à obtenir des données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser dans votre code R. Le processus est le suivant :
  
- Créer une connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
- Définir une requête qui contient les données dont vous avez besoin, ou spécifier une table ou une vue
- Définir un ou plusieurs contextes de calcul à utiliser lors de l’exécution du code R
- Si vous le souhaitez, définir les transformations qui sont appliquées à la source de données pendant la lecture à partir de la source

Les étapes suivantes font tous partie du code R et doivent être exécutées dans un environnement R. Nous avons utilisé Microsoft R Client, car il inclut tous les packages RevoScaleR, ainsi qu’un ensemble de base, légère des outils R.

1. Si le **RevoScaleR** package n'est pas déjà chargé, exécutez cette ligne de code R :

    ```R
    library("RevoScaleR")
    ```

     Les guillemets sont facultatifs, dans ce cas, bien que recommandée.
     
     Si vous obtenez une erreur, assurez-vous que votre environnement de développement R utilise une bibliothèque qui inclut le package RevoScaleR. Utilisez une commande telle que `.libPaths()` pour afficher le chemin de bibliothèque en cours.

2. Créer la chaîne de connexion pour SQL Server et l’enregistrer dans une variable R, _connStr_.
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Uid=your-sql-login;Pwd=your-login-password"
    ```

    Le nom de serveur, vous serez peut-être en mesure d’utiliser uniquement le nom d’instance, ou vous devrez peut-être qualifier entièrement le nom, en fonction de votre réseau.

    Pour l’authentification Windows, la syntaxe est un peu différente :
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Trusted_Connection=True"
    ```

    Le script R disponible en téléchargement utilise uniquement des connexions SQL. En règle générale, nous vous recommandons d’utiliser l’authentification Windows lorsque cela est possible, afin d’éviter l’enregistrement des mots de passe dans votre code R. Toutefois, pour vous assurer que le code dans ce didacticiel correspond au code téléchargé à partir de Github, nous allons utiliser une connexion SQL pour le reste de la procédure pas à pas.

3. Définir des variables à utiliser pour créer un nouveau *contexte de calcul*. Après avoir créé l’objet de contexte de calcul, vous pouvez l’utiliser pour exécuter le code R sur l’instance de SQL Server.

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - R utilise un répertoire temporaire pour la sérialisation bidirectionnelle des objets R entre votre station de travail et l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez spécifier le répertoire local qui est utilisé en tant que *sqlShareDir*ou accepter la valeur par défaut.
  
    - Utilisez *sqlWait* pour indiquer si vous souhaitez que R attende les résultats à partir du serveur.  Pour une discussion sur avec ou sans attente travaux, consultez [distribuées et les calculs parallèles avec ScaleR dans Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).
  
    - Utilisez l’argument *sqlConsoleOutput* pour indiquer que vous ne souhaitez pas afficher la sortie de la console R.


4. Vous appelez le [RxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) constructeur pour créer l’objet de contexte de calcul avec les variables et les chaînes de connexion déjà définies et enregistrer le nouvel objet dans la variable R *sqlcc*.
  
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

Microsoft r, un *source de données* est un objet que vous créez à l’aide de fonctions RevoScaleR. L’objet de source de données spécifie un jeu de données que vous souhaitez utiliser pour une tâche, telle que de l’extraction de formation ou une fonctionnalité de modèle. Vous pouvez obtenir des données à partir de diverses sources ; pour la liste des sources actuellement prises en charge, consultez [RxDataSource](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource).

Plus tôt vous définie par une chaîne de connexion et enregistré ces informations dans une variable R. Vous pouvez réutiliser ces informations de connexion pour spécifier les données que vous souhaitez obtenir.

1. Enregistrer une requête SQL comme une variable de chaîne. La requête définit les données d’apprentissage du modèle.

    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    Nous avons utilisé ici une clause TOP pour rendre les choses s’exécutent plus rapidement, mais les lignes réelles retournées par la requête peuvent varier en fonction de l’ordre. Par conséquent, votre synthèse des résultats peuvent également être différents de ceux répertoriés ci-dessous. N’hésitez pas à supprimer la clause TOP.

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
  
    + L’argument *rowsPerRead* est important pour la gestion de l’utilisation de mémoire et l’efficacité des calculs.  La plupart des fonctions analytiques améliorées dans[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] traitent les données en segments et accumulent les résultats intermédiaires. Elles retournent les calculs finaux une fois que toutes les données ont été lues.  En ajoutant le *rowsPerRead* paramètre, vous pouvez contrôler le nombre de lignes de données est lues dans chaque segment pour le traitement.  Si la valeur de ce paramètre est trop grande, l’accès aux données peut être lent, car vous n’avez pas suffisamment de mémoire pour traiter efficacement un si grand segment de données.  Sur certains systèmes, en définissant *rowsPerRead* à une valeur trop petite peut également fournir la baisse des performances.

3. À ce stade, vous avez créé le *inDataSource* objet, mais il ne contient pas toutes les données. Les données ne sont pas extraites à partir de la requête SQL dans l’environnement local jusqu'à ce que vous exécutez une fonction telle que [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) ou [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary).

    Toutefois, maintenant que vous avez défini les objets de données, vous pouvez l’utiliser comme argument à d’autres fonctions.

## <a name="use-the-sql-server-data-in-r-summaries"></a>Utiliser les données de SQL Server dans des résumés de R

Dans cette section, vous allez tester plusieurs des fonctions fournies dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] distantes prise en charge des contextes de calcul. En appliquant des fonctions R à la source de données, vous pouvez Explorer, résumer et du graphique le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données.

1. Appelez la fonction [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) pour obtenir la liste des variables dans la source de données et leurs types de données.

    **rxGetVarInfo** est une fonction pratique ; vous pouvez l’appeler sur toute trame de données, ou sur un jeu de données dans un objet de données distant, pour obtenir des informations telles que les valeurs maximale et minimale des valeurs, le type de données et le nombre de niveaux dans les colonnes de facteurs.
    
    Envisagez d’exécuter cette fonction après tout type d’entrée de données, de transformation de caractéristique ou d’ingénierie de caractéristiques. En procédant ainsi, vous pouvez vous assurer que toutes les fonctionnalités que vous souhaitez utiliser dans votre modèle sont les données attendues tapez et éviter les erreurs.
  
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

2. À présent, appelez la fonction RevoScaleR [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary) pour obtenir des statistiques plus détaillées sur des variables individuelles.

    rxSummary repose sur R `summary` de fonctionner, mais a des fonctionnalités supplémentaires et des avantages. rxSummary fonctionne dans plusieurs contextes de calcul et prend en charge la segmentation.  Vous pouvez également utiliser rxSummary pour transformer des valeurs ou résumer en fonction des niveaux de facteur.
    
    Dans cet exemple, vous résumer le prix selon le nombre de passagers.
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + Le premier argument de rxSummary spécifie la formule ou un terme à synthétiser par. Ici, le `F()` fonction est utilisée pour convertir les valeurs dans _passagers\_nombre_ en facteurs avant de synthèse. Vous devez également spécifier la valeur minimale (1) et la valeur maximale (6) pour le _passagers\_nombre_ variable facteur.
    + Si vous ne spécifiez pas les statistiques à générer, rxSummary génère par défaut Mean, StDev, Min, Max et le nombre d’observations valides et manquantes.
    + Cet exemple inclut également du code pour effectuer le suivi de l’heure à laquelle la fonction démarre et se termine, afin que vous puissiez comparer les performances.
  
    **Résultats**

    Si la fonction rxSummary s’exécute correctement, vous devriez voir les résultats comme ceux-ci, suivie d’une liste des statistiques par catégorie. 

    ```
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>Exercice supplémentaire sur les big data

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
> Bien que cela est en cours d’exécution, vous pouvez utiliser un outil tel que [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) ou Profiler SQL pour voir comment la connexion est établie et le code R est exécuté à l’aide des services SQL Server.
> 
> Une autre option consiste à surveiller les travaux R s’exécutant sur SQL Server à l’aide de ces [des rapports personnalisés](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="next-lesson"></a>Leçon suivante

[Créer des graphiques et des tracés à l’aide de R](walkthrough-create-graphs-and-plots-using-r.md)

## <a name="previous-lesson"></a>Leçon précédente

[Explorer les données à l’aide de SQL](walkthrough-view-and-explore-the-data.md)
