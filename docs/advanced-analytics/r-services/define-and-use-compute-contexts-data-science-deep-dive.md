---
title: "D&#233;finir et utiliser des contextes de calcul (Immersion dans la science des donn&#233;es) | Microsoft Docs"
ms.custom: ""
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
ms.assetid: b13058d0-9c6a-44e1-849b-72189d9050ba
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# D&#233;finir et utiliser des contextes de calcul (Immersion dans la science des donn&#233;es)
Vous avez décidé d’effectuer les calculs les plus complexes sur le serveur, plutôt que sur votre ordinateur local. Pour ce faire, vous devez créer un contexte de calcul qui vous permette d’exécuter le code R sur le serveur.  
  
La fonction [RxInSqlServer](https://msdn.microsoft.com/microsoft-r/scaler/rxinsqlserver) est l’une des fonctions R améliorées fournies dans le package [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler). La fonction gère les tâches de création de la connexion de base de données et de transmission des objets entre l’ordinateur local et le contexte d’exécution distant.  
  
Dans cette étape, vous allez apprendre à utiliser la fonction *RxInSqlServer* pour définir un contexte de calcul.  


  
## Créer et définir un contexte de calcul  
Pour créer un contexte de calcul, vous avez besoin des informations de base suivantes sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   La chaîne de connexion pour l’instance  
-   Une spécification pour le traitement de la sortie  
-   Des arguments facultatifs pour l’activation du suivi, ou pour spécifier un répertoire partagé


 Nous pouvons commencer.

1.  Spécifiez la chaîne de connexion pour l’instance dans laquelle ont lieu les calculs.  Il s’agit de l’une des nombreuses variables que vous passez à la fonction *RxInSqlServer* pour créer le contexte de calcul. 

    **Utilisation d’une connexion SQL**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user name>;Pwd=<password>" 
      ```

    **Utilisation de l’authentification intégrée de Windows**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"" 
      ```
2.  Spécifiez la façon dont vous voulez gérer la sortie. Dans le code suivant, vous indiquez que la session R sur la station de travail doit toujours attendre les résultats de la tâche R, mais pas retourner la sortie de console des calculs distants.  
  
    ```R  
    sqlWait <- TRUE   
    sqlConsoleOutput <- FALSE   
    ```  
  
    L’argument *wait* pour *RxInSqlServer* prend en charge ces options :  
  
    -   **TRUE**. La tâche a une action bloquante et ne retourne aucun résultat tant qu’elle n’est pas terminée ou qu’elle n’a pas échoué.  Pour plus d’informations sur les tâches bloquantes et non bloquantes, consultez 
  
    -   **FALSE**. Les tâches n’ont pas d’action bloquante et retournent immédiatement les résultats, ce qui vous permet de continuer à exécuter un autre code R. Toutefois, même en mode non bloquant, la connexion client à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être maintenue pendant l’exécution de la tâche.  

3. Si vous le souhaitez, vous pouvez spécifier l’emplacement d’un répertoire local pour une utilisation partagée par la session R locale et par l’ordinateur distant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ses comptes.
    
    ```R  
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")   
    
    ## Add this line to create directory if it does not exist
    dir.create(sqlShareDir, recursive = TRUE) 
    ```  
    Pour cet argument, nous vous recommandons d’utiliser la valeur par défaut, au lieu de spécifier manuellement un dossier. Pour plus d’informations, consultez la [documentation de référence ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/rxinsqlserver).
    
    Si vous souhaitez simplement connaître le dossier qui est utilisé, vous pouvez exécuter `rxGetComputeContext` pour afficher plus d’informations sur l’actuel contexte de calcul. 
  

4.  Après avoir préparé toutes les variables, fournissez-les comme arguments au constructeur `RxInSqlServer` pour définir l’objet de contexte de calcul.  
  
    ```R  
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,        
         #shareDir = sqlShareDir,       
         wait = sqlWait,   
         consoleOutput = sqlConsoleOutput)  
    ```  
  
    Vous pouvez observer que la syntaxe de *RxInSqlServer* est presque identique à celle de la fonction *RxSqlServerData* que vous avez utilisée précédemment pour définir la source de données. Toutefois, il existe des différences importantes.  
  
    -   L’objet source de données (défini à l’aide de la fonction *RxSqlServerData*) spécifie où sont stockées les données.  
  
    -   En revanche, le contexte de calcul (défini à l’aide de la fonction *RxInSqlServer*) indique où doivent avoir lieu les agrégations et autres calculs.  
  
    La définition d’un contexte de calcul n’affecte pas les autres calculs R génériques que vous pouvez effectuer sur votre station de travail, et ne modifie pas la source des données. Vous pouvez par exemple, définir un fichier texte local comme source de données, mais modifier le contexte de calcul de SQL Server et effectuer toutes vos lectures et résumés des données sur l’ordinateur SQL Server. 
  
## Activer le traçage sur le contexte de calcul  
Parfois, les opérations qui fonctionnent pour votre contexte local rencontrent des problèmes lorsqu’elles sont exécutées dans un contexte de calcul distant. Si vous souhaitez analyser les problèmes ou suivre les performances, vous pouvez activer le suivi dans le contexte de calcul, pour que la résolution des problèmes d’exécution soit prise en charge.  
  
1. Créez un nouveau contexte de calcul qui utilise la même chaîne de connexion, mais ajoutez les arguments *traceEnabled* et *traceLevel* au constructeur *RxInSqlServer*.  
  
    ```R  
    sqlComputeTrace <- RxInSqlServer(   
        connectionString = sqlConnString,        
        #shareDir = sqlShareDir,  
        wait = sqlWait,   
        consoleOutput = sqlConsoleOutput,       
        traceEnabled = TRUE,
        traceLevel = 7)  
    ```  
  
    Dans cet exemple, la propriété *traceLevel* a la valeur 7, ce qui signifie « afficher toutes les informations de traçage ».  

2. Pour basculer vers ce contexte de calcul à tout moment, utilisez la fonction *rxSetComputeContext* et spécifiez le contexte par son nom.

    ```R  
    rxSetComputeContext( sqlComputeTrace)
    ```

    Pour ce didacticiel, nous allons utiliser le contexte de calcul pour lequel le traçage n’est pas activé. Les performances de l’option de suivi n’ont pas été testées pour toutes les opérations et votre expérience peut varier en fonction de la connectivité réseau.  
  
Maintenant que vous avez créé un contexte de calcul à distance, vous allez apprendre à modifier le calcul des contextes, pour exécuter le code R sur le serveur ou localement.  
  
## Étape suivante  
[Leçon 2 : Créer et exécuter des scripts R &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
## Étape précédente  
[Interroger et modifier les données du serveur SQL &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/query-and-modify-the-sql-server-data-data-science-deep-dive.md)  
  
## Voir aussi  
[Immersion dans la science des données : utilisation des packages RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
