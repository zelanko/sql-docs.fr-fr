---
title: Afficher et synthétiser les données de SQL Server à l’aide de fonctions R
description: Didacticiel illustrant comment visualiser et générer des résumés statistiques à l’aide de fonctions R pour l’analyse dans la base de données sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: e209b707c3d04cef7709945dc2a32b171f90771e
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68468835"
---
# <a name="view-and-summarize-sql-server-data-using-r-walkthrough"></a>Afficher et résumer les données d’SQL Server à l’aide de R (procédure pas à pas)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette leçon vous présente les fonctions du package **RevoScaleR** et vous guide tout au long des tâches suivantes:

> [!div class="checklist"]
> * Se connecter à SQL Server
> * Définir une requête qui contient les données dont vous avez besoin, ou spécifier une table ou une vue
> * Définir un ou plusieurs contextes de calcul à utiliser lors de l’exécution du code R
> * Éventuellement, définissez les transformations qui sont appliquées à la source de données pendant qu’elle est lue à partir de la source.

## <a name="define-a-sql-server-compute-context"></a>Définir un contexte de calcul SQL Server

Exécutez les instructions R suivantes dans un environnement R sur la station de travail cliente. Cette section part du principe qu’il s’agit d’une [station de travail de science des données avec Microsoft R client](../r/set-up-a-data-science-client.md), car elle comprend tous les packages RevoScaleR, ainsi qu’un ensemble basique et léger d’outils R. Par exemple, vous pouvez utiliser RGUI. exe pour exécuter le script R dans cette section.

1. Si le package **RevoScaleR** n’est pas déjà chargé, exécutez la ligne de code R suivante:

    ```R
    library("RevoScaleR")
    ```

     Les guillemets sont facultatifs, dans ce cas, bien que recommandés.
     
     Si vous recevez une erreur, assurez-vous que votre environnement de développement R utilise une bibliothèque qui comprend le package RevoScaleR. Utilisez une commande telle que `.libPaths()` pour afficher le chemin d’accès à la bibliothèque actuelle.

2. Créez la chaîne de connexion pour SQL Server et enregistrez-la dans une variable R, *ConnStr*.

   Vous devez remplacer l’espace réservé «your_server_name» par un nom d’instance valide SQL Server. Pour le nom du serveur, vous pouvez utiliser uniquement le nom de l’instance, ou vous devrez peut-être qualifier complètement le nom, en fonction de votre réseau.
    
   Pour l’authentification SQL Server, la syntaxe de la connexion est la suivante:

    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Uid=your-sql-login;Pwd=your-login-password"
    ```

    Pour l’authentification Windows, la syntaxe est un peu différente:
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Trusted_Connection=True"
    ```

    En règle générale, nous vous recommandons d’utiliser l’authentification Windows dans la mesure du possible, afin d’éviter d’enregistrer les mots de passe dans votre code R.

3. Définissez les variables à utiliser lors de la création d’un nouveau *contexte de calcul*. Après avoir créé l’objet de contexte de calcul, vous pouvez l’utiliser pour exécuter le code R sur l’instance SQL Server.

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - R utilise un répertoire temporaire pour la sérialisation bidirectionnelle des objets R entre votre station de travail et l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez spécifier le répertoire local qui est utilisé en tant que *sqlShareDir*ou accepter la valeur par défaut.
  
    - Utilisez *sqlWait* pour indiquer si vous souhaitez que R attende les résultats du serveur.  Pour plus d’informations sur les travaux en attente et non en attente, consultez la page relative [à l’informatique distribuée et parallèle avec RevoScaleR dans Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).
  
    - Utilisez l’argument *sqlConsoleOutput* pour indiquer que vous ne souhaitez pas afficher la sortie de la console R.

4. Vous appelez le constructeur [RxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) pour créer l’objet de contexte de calcul avec les variables et les chaînes de connexion déjà définies, puis enregistrer le nouvel objet dans la variable R *sqlcc*.
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. Par défaut, le contexte de calcul est local. vous devez donc définir explicitement le contexte de calcul *actif* .

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) renvoie le contexte de calcul précédemment actif, ce qui vous permet de l’utiliser
    + [rxGetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) retourne le contexte de calcul actif
    
    Notez que la définition d’un contexte de calcul affecte uniquement les opérations qui utilisent des fonctions dans le package **RevoScaleR** ; le contexte de calcul n’a aucune incidence sur la façon dont les opérations R Open source sont effectuées.

## <a name="create-a-data-source-using-rxsqlserver"></a>Créer une source de données à l’aide de RxSqlServer

Lorsque vous utilisez les bibliothèques Microsoft R telles que RevoScaleR et MicrosoftML, une *source de données* est un objet que vous créez à l’aide de fonctions RevoScaleR. L’objet source de données spécifie un jeu de données que vous souhaitez utiliser pour une tâche, telle que l’apprentissage du modèle ou l’extraction de fonctionnalités. Vous pouvez obtenir des données à partir de diverses sources, notamment des SQL Server. Pour obtenir la liste des sources actuellement prises en charge, consultez [RxDataSource](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource).

Précédemment, vous avez défini une chaîne de connexion et enregistré ces informations dans une variable R. Vous pouvez réutiliser ces informations de connexion pour spécifier les données que vous souhaitez obtenir.

1. Enregistrez une requête SQL en tant que variable de chaîne. La requête définit les données pour l’apprentissage du modèle.

    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    Nous avons utilisé ici une clause TOP pour accélérer l’exécution des opérations, mais les lignes réelles retournées par la requête peuvent varier en fonction de l’ordre. Par conséquent, les résultats de votre synthèse peuvent également être différents de ceux listés ci-dessous. N’hésitez pas à supprimer la clause TOP.

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
    
    + L’argument  *colClasses* spécifie les types de colonne à utiliser pour le déplacement des données entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et R. Cela est important, car par rapport à R, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des types de données différents et plus nombreux. Pour plus d’informations, consultez [bibliothèques et types de données R](../r/r-libraries-and-data-types.md).
  
    + L’argument *rowsPerRead* est important pour la gestion de l’utilisation de la mémoire et des calculs efficaces.  La plupart des fonctions analytiques améliorées dans[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] traitent les données en segments et accumulent les résultats intermédiaires. Elles retournent les calculs finaux une fois que toutes les données ont été lues.  En ajoutant le paramètre *rowsPerRead* , vous pouvez contrôler le nombre de lignes de données lues dans chaque segment en vue de leur traitement.  Si la valeur de ce paramètre est trop grande, l’accès aux données peut être lent, car vous n’avez pas suffisamment de mémoire pour traiter efficacement un grand nombre de données.  Sur certains systèmes, la définition de *rowsPerRead* sur une valeur trop faible peut également offrir des performances plus lentes.

3. À ce stade, vous avez créé l'  objet indatasource, mais il ne contient aucune donnée. Les données ne sont pas extraites de la requête SQL dans l’environnement local tant que vous n’exécutez pas une fonction telle que [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) ou [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary).

    Toutefois, maintenant que vous avez défini les objets de données, vous pouvez l’utiliser comme argument pour d’autres fonctions.

## <a name="use-the-sql-server-data-in-r-summaries"></a>Utiliser les données de SQL Server dans les résumés R

Dans cette section, vous allez essayer plusieurs des fonctions fournies dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] qui prennent en charge les contextes de calcul à distance. En appliquant des fonctions R à la source de données, vous pouvez explorer, synthétiser et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] représenter graphiquement les données.

1. Appelez la fonction [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) pour obtenir la liste des variables dans la source de données et leurs types de données.

    **rxGetVarInfo** est une fonction pratique. vous pouvez l’appeler sur n’importe quelle trame de données, ou sur un ensemble de données dans un objet de données distant, pour obtenir des informations telles que les valeurs maximale et minimale, le type de données et le nombre de niveaux dans les colonnes de facteurs.
    
    Envisagez d’exécuter cette fonction après tout type d’entrée de données, de transformation de caractéristique ou d’ingénierie de caractéristiques. En procédant ainsi, vous pouvez vous assurer que toutes les fonctionnalités que vous souhaitez utiliser dans votre modèle sont du type de données attendu et éviter des erreurs.
  
    ```R
    rxGetVarInfo(data = inDataSource)
    ```

    **Résultats**
    
    ```R
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

    rxSummary est basé sur la fonction `summary` R, mais offre des fonctionnalités et des avantages supplémentaires. rxSummary fonctionne dans plusieurs contextes de calcul et prend en charge la segmentation.  Vous pouvez également utiliser rxSummary pour transformer des valeurs ou synthétiser en fonction de niveaux de facteur.
    
    Dans cet exemple, vous résumez le montant du prix en fonction du nombre de passagers.
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + Le premier argument de rxSummary spécifie la formule ou le terme à synthétiser. Ici, la `F()` fonction est utilisée pour convertir les valeurs du _nombre\_de passagers_ en facteurs avant la synthèse. Vous devez également spécifier la valeur minimale (1) et la valeur maximale (6) pour la variable facteur de _nombre de passagers\__ .
    + Si vous ne spécifiez pas les statistiques à générer, par défaut, les sorties rxSummary sont Mean, StDev, min, Max et le nombre d’observations valides et manquantes.
    + Cet exemple inclut également du code pour effectuer le suivi de l’heure à laquelle la fonction démarre et se termine, afin que vous puissiez comparer les performances.
  
    **Résultats**

    Si la fonction rxSummary s’exécute correctement, vous devez voir les résultats comme ceux-ci, suivis d’une liste de statistiques par catégorie. 

    ```R
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>Exercice bonus sur Big Data

Essayez de définir une nouvelle chaîne de requête avec toutes les lignes. Nous vous recommandons de configurer un nouvel objet de source de données pour cette expérience. Vous pouvez également essayer de modifier le paramètre *rowsToRead* pour voir comment il affecte le débit.

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
> Pendant son exécution, vous pouvez utiliser un outil tel que [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) ou le générateur de profils SQL pour voir comment la connexion est établie et le code R est exécuté à l’aide des services SQL Server.
> 
> Une autre option consiste à surveiller les travaux R exécutés sur SQL Server à l’aide de ces [rapports personnalisés](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer des graphiques et des tracés à l’aide de R](walkthrough-create-graphs-and-plots-using-r.md)