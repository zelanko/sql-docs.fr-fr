---
title: "Affichage et r&#233;sumer les donn&#233;es &#224; l’aide de R (Proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 358e1431-8f47-4d32-a02f-f90e519eef49
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Affichage et r&#233;sumer les donn&#233;es &#224; l’aide de R (Proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es)
Maintenant, vous allez travailler avec les mêmes données à l’aide de code R. Vous allez également apprendre à utiliser les fonctions du package **RevoScaleR** inclus dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] pour générer des résumés de données dans le contexte du serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et à renvoyer les résultats à votre environnement R.  

Un script R est fourni avec cette procédure pas à pas, dans lequel se trouve tout le code nécessaire pour créer l’objet de données, générer des résumés et créer des modèles. Le fichier de script R, **RSQL_RWalkthrough.R**, se trouve à l’emplacement auquel vous avez installé les fichiers de script.  
+ Si vous êtes familiarisé avec R, vous pouvez exécuter le script en entier.
+ Pour ceux qui apprennent à utiliser RevoScaleR, ce didacticiel passe en revue le script ligne par ligne.
+ Pour exécuter des lignes individuelles du script, vous pouvez mettre en surbrillance une ou plusieurs lignes dans le fichier et appuyer sur Ctrl + Entrée.    
  
> [!TIP]  Enregistrez votre espace de travail R au cas où vous souhaiteriez effectuer le reste de la procédure pas à pas ultérieurement.  De cette façon, vous pourrez réutiliser les objets de données et autres variables.   

## <a name="defining-sql-server-data-sources-and-compute-contexts"></a>Définition des sources de données et des contextes de calcul SQL Server
Pour récupérer des données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de les intégrer dans votre code R, vous devez :  
  
- Créer une connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
- Définir une requête qui contient les données dont vous avez besoin, ou spécifier une table ou une vue    
- Définir un ou plusieurs contextes de calcul à utiliser lors de l’exécution du code R    
-   Définir éventuellement des fonctions qui peuvent être appliquées à la source de données  
 

### <a name="load-the-revoscaler-library"></a>Charger la bibliothèque RevoScaleR

+  Si le package **RevoScaleR** n’est pas encore chargé, exécutez :
    ```R
    library("RevoScaleR")`.  
    ```  
    Si vous obtenez une erreur, vérifiez que votre environnement de développement R utilise la bibliothèque qui inclut le package RevoScaleR. Utilisez une commande telle que `.libPaths())` pour afficher le chemin d’accès actuel :  

    Si c’est la première fois que vous utilisez le package **RevoScaleR** , accédez à l’aide en ligne dans l’environnement R en tapant `help("RevoScaleR")` ou `help("RxSqlServerData")`.  

### <a name="create-connection-strings"></a>Créer les chaînes de connexion


1. Définissez les chaînes de connexion. Dans le cadre de cette procédure pas à pas, nous vous avons fourni des exemples pour les connexions SQL et l’authentification intégrée de Windows. Dans la mesure du possible, nous vous recommandons d’utiliser l’authentification de Windows afin de ne pas enregistrer de mots de passe dans votre code R.

    Le compte utilisé doit disposer des autorisations nécessaires pour lire les données et créer des tables dans la base de données spécifiée. Pour plus d’informations sur la façon d’ajouter des utilisateurs à la base de données SQL et de leur accorder les autorisations correctes, consultez [Post-Installation Server Configuration &#40;SQL Server R Services&#41;](../Topic/Post-Installation%20Server%20Configuration%20(SQL%20Server%20R%20Services).md) (Configuration du serveur post-installation SQL Server R Services). 

    ```R  
    # SQL authentication  
    connStrSql <- "Driver=SQL Server;Server=<SQL_instance_name>;Database=<database_name>;    Uid=<user_name>;Pwd=<user password>"  

    # Windows authentication  
    connStrWin <- "Driver=SQL Server;Server=<SQL_instance_name>;Database=<database_name>;Trusted_Connection=Yes" 
    
    # Use one of the connection strings
    connStr <- connStrWin 
    ```
    > [!NOTE] Le cas échéant, modifiez le nom du serveur, le nom de la base de données, le nom d’utilisateur et le mot de passe. 
      
  
### <a name="define-and-set-a-compute-context"></a>Définir et spécifier un contexte de calcul  

Vous allez maintenant définir un *contexte de calcul* pour permettre au code R de s’exécuter sur l’ordinateur SQL Server. En règle générale, quand vous utilisez R, toutes les opérations s’exécutent en mémoire sur votre ordinateur. Cependant, en indiquant que les opérations R doivent être exécutées sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez exécuter des tâches en parallèle et tirer parti des ressources du serveur.  

Le contexte de calcul est local par défaut. Vous devez donc spécifier explicitement le contexte de calcul en fonction de l’opération.  


1.  Commencez par définir quelques variables utilisées pour créer le contexte de calcul.  
  
    ```R    
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")  
    sqlWait <- TRUE  
    sqlConsoleOutput <- FALSE    
    ```    
    -   R utilise un répertoire temporaire pour la sérialisation bidirectionnelle des objets R entre votre station de travail et l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez spécifier le répertoire local qui est utilisé en tant que *sqlShareDir* ou accepter la valeur par défaut.  
  
    -   Utilisez *sqlWait* pour indiquer si vous souhaitez ou non que R attende les résultats.  Pour obtenir des informations complémentaires sur la question des travaux avec ou sans attente, consultez [ScaleR Distributed Computing](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing) (Calcul distribué ScaleR).
  
    -   Utilisez l’argument *sqlConsoleOutput* pour indiquer que vous ne souhaitez pas voir la sortie de la console R.  
  
2.  Créez l’objet de contexte de calcul avec les variables et les chaînes de connexion déjà définies et enregistrez-le dans la variable R *sqlcc*.  
  
    ```  
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir,   
                        wait = sqlWait, consoleOutput = sqlConsoleOutput)  
    ```  

4. Spécifiez le contexte de calcul.
    ```R
    rxSetComputeContext(sqlcc)  
    ```  
   + `rxSetComputeContext` retourne sans le montrer le contexte de calcul précédemment actif afin que vous puissiez l’utiliser.
   + `rxGetComputeContext` retourne le contexte de calcul actif.  
  
    Notez que le contexte de calcul spécifié affecte uniquement les opérations qui utilisent les fonctions disponibles dans le package **RevoScaleR** ; il n’affecte pas la façon dont les opérations R open source sont effectuées.  
  
### <a name="create-an-rxsqlserver-data-object"></a>Créer un objet de données RxSqlServer  

Une fois la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser définie, vous pouvez vous appuyer sur cet objet de connexion de données pour définir différentes sources de données. Une *source de données* spécifie un jeu de données à utiliser pour une tâche, telle que l’apprentissage, l’exploration, le calcul de score et la génération de caractéristiques.  
    
Pour définir des jeux de données SQL Server, vous devez utiliser la fonction *RxSqlServer*, et transmettre une chaîne de connexion et la définition des données à obtenir.  
  
1. Enregistrez l’instruction SQL en tant que variable de chaîne. Cette requête définit les données que vous allez utiliser pour effectuer l’apprentissage du modèle.    
    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, 
           passenger_count,trip_time_in_secs,trip_distance,   
           pickup_datetime, dropoff_datetime, pickup_longitude, 
           pickup_latitude, dropoff_longitude,    
           dropoff_latitude 
           FROM nyctaxi_sample"  
    ```

2. Transmettez la définition de la requête en tant qu’argument à la source de données SQL Server. L’argument *colClasses* spécifie le schéma des données à retourner en mappant la requête SQL. 

    ```R  
    inDataSource <- RxSqlServerData(sqlQuery = sampleDataQuery, 
         connectionString = connStr,
         colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
         dropoff_longitude = "numeric", dropoff_latitude = "numeric"),  
         rowsPerRead=500)  
    ```
    
    + L’argument *colClasses* spécifie les types de colonne à utiliser pour le déplacement des données entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et R. Cela est important, car par rapport à R, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des types de données différents et plus nombreux. Pour plus d’informations, consultez [Utilisation des types de données R](../../advanced-analytics/r-services/working-with-r-data-types.md).  
  
    + L’argument *rowsPerRead* est important pour gérer l’utilisation de la mémoire et optimiser l’efficacité des calculs.  La plupart des fonctions analytiques améliorées dans[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] traitent les données en segments et accumulent les résultats intermédiaires. Elles retournent les calculs finaux une fois que toutes les données ont été lues.  En ajoutant le paramètre `rowsPerRead` , vous pouvez contrôler le nombre de lignes de données lues dans chaque segment pour le traitement.  Si la valeur de ce paramètre est trop grande, l’accès aux données peut être lent, car vous n’avez pas suffisamment de mémoire pour traiter efficacement un si grand segment de données.  Sur certains systèmes, si vous définissez `rowsPerRead` sur une valeur trop petite, les performances peuvent également être ralenties.  

> [!TIP] Une fois l’objet de données *inDataSource* créé, vous pouvez le réutiliser autant de fois que nécessaire pour obtenir des informations de base sur les données et les variables utilisées, pour manipuler et transformer les données ou pour effectuer l’apprentissage d’un modèle.  Toutefois, l’objet *inDataSource* lui-même ne contient pour l’instant aucune donnée issue de la requête SQL. Les données ne sont extraites dans l’environnement local qu’au moment où vous exécutez une fonction telle que *rxImport* ou *rxSummary*.          
  
## <a name="using-the-sql-server-data-in-r"></a>Utilisation des données SQL Server dans R  
Vous pouvez à présent appliquer des fonctions R à la source de données, pour explorer et résumer les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ainsi que pour les représenter sous forme graphique. Dans cette section, vous allez tester plusieurs fonctions fournies dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] qui prennent en charge les contextes de calcul à distance.  
  
-   `rxGetVarInfo` : utilisez cette fonction pour les trames ou les jeux de données d’un objet de données distant (également avec certaines listes et matrices) afin d’obtenir des informations telles que les valeurs minimale et maximale, le type de données et le nombre de niveaux dans les colonnes de facteurs.  
  
    Envisagez d’exécuter cette fonction après tout type d’entrée de données, de transformation de caractéristique ou d’ingénierie de caractéristiques. Ainsi, toutes les caractéristiques que vous souhaitez utiliser dans votre modèle correspondent au type de données attendu et vous évitez les erreurs.  
 
  
-   `rxSummary` : utilisez cette fonction pour obtenir des statistiques plus détaillées sur des variables spécifiques. Vous pouvez également transformer des valeurs, calculer des résumés à l’aide de niveaux de facteur et enregistrer les résumés en vue de les réutiliser.  
  
  
### <a name="inspect-variables-in-the-data-source"></a>Inspecter les variables de la source de données  
    
+ Appelez la fonction `rxGetVarInfo`, en utilisant la source de données  `inDataSource` comme argument, pour obtenir la liste des variables dans la source de données et leurs types de données.  
  
    ```R  
    rxGetVarInfo(data = inDataSource)  
    ```  
  
    *Résultats :*  
    *Var 1: tipped, Type: integer*  
    *Var 2: fare_amount, Type: numeric*  
    *Var 3: passenger_count, Type: integer*  
    *Var 4: trip_time_in_secs, Type: numeric, Storage: int64*  
    *Var 5: trip_distance, Type: numeric*  
    *Var 6: pickup_datetime, Type: character*  
    *Var 7: dropoff_datetime, Type: character*  
    *Var 8: pickup_longitude, Type: numeric*  
    *Var 9: pickup_latitude, Type: numeric*  
    *Var 10: dropoff_longitude, Type: numeric*  
  
### <a name="create-a-summary-using-r"></a>Créer un résumé à l’aide de R

+ Appelez la fonction RevoScaleR `rxSummary` pour résumer le prix selon le nombre de passagers. 
    ```R  
    start.time <- proc.time()  
    rxSummary(~fare_amount:F(passenger_count), data = inDataSource)  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2), 
      " seconds to summarize the inDataSource.", sep=""))
    ```  
 
    + Le premier argument de `rxSummary` spécifie la formule ou le terme à utiliser pour effectuer le résumé. Ici, la fonction `F()` est utilisée pour convertir les valeurs de passenger_count en facteurs avant de procéder au résumé.  
    + Si vous ne spécifiez pas les statistiques à générer, par défaut, `rxSummary` génère Mean, StDev, Min, Max et le nombre d’observations valides et manquantes.  
    + Cet exemple inclut également du code pour effectuer le suivi de l’heure à laquelle la fonction démarre et se termine, afin que vous puissiez comparer les performances.  
  
    *Résultats*  
    *rxSummary(formula = ~fare_amount:F(passenger_count), data = inDataSource)*  
    *Summary Statistics Results for: ~fare_amount:F(passenger_count)*  
    *Data: inDataSource (RxSqlServerData Data Source)*  
    *Number of valid observations: 1000*   
    *Name                          Mean    StdDev   Min Max ValidObs MissingObs*  
    *fare_amount:F_passenger_count 12.4875 9.682605 2.5 64  1000     0*   
    *Statistics by category (6 categories):   *Category                             F_passenger_count Means    StdDev    Min*   
    *fare_amount for F(passenger_count)=1 1                 12.00901  9.219458  2.5*  
    *fare_amount for F(passenger_count)=2 2                 11.61893  8.858739  3.0*  
    *fare_amount for F(passenger_count)=3 3                 14.40196 10.673340  3.5*  
    *fare_amount for F(passenger_count)=4 4                 13.69048  8.647942  4.5*  
    *fare_amount for F(passenger_count)=5 5                 19.30909 14.122969  3.5*  
    *fare_amount for F(passenger_count)=6 6                 12.00000        NA 12.0*  
    *Max ValidObs*  
    *55  666*   
    *52  206*   
    *52   51*   
    *39   21*   
    *64   55*   
    *12    1*   
    *"It takes CPU Time=0.5 seconds, Elapsed Time=4.59 seconds to summarize the inDataSource."*  
  

  
## <a name="next-step"></a>Étape suivante  
[Créer des graphiques et des tracés à l’aide de R &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/create-graphs-and-plots-using-r-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Leçon précédente  
[Leçon 1 : Préparer les données &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
