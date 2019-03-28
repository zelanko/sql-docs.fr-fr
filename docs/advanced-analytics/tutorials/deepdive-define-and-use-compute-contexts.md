---
title: Définir et utiliser des contextes de calcul RevoScaleR - SQL Server Machine Learning
description: Didacticiel pas à pas sur la façon de définir un contexte de calcul à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: f020fffd28223fe37699c38f55bedb2f9e5e65d8
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511017"
---
# <a name="define-and-use-compute-contexts-sql-server-and-revoscaler-tutorial"></a>Définir et utiliser des contextes de calcul (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie de la [RevoScaleR didacticiel](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans la leçon précédente, vous avez utilisé **RevoScaleR** fonctions pour inspecter les objets de données. Cette leçon présente la [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) (fonction), ce qui vous permet de définir un contexte de calcul pour un serveur SQL distant. Avec un contexte de calcul à distance, vous pouvez décaler l’exécution de R à partir d’une session locale à une session à distance sur le serveur. 

> [!div class="checklist"]
> * Découvrez que les éléments d’un serveur SQL distant contexte de calcul
> * Activer le suivi sur un objet de contexte de calcul

**RevoScaleR** prend en charge plusieurs contextes de calcul : Hadoop, Spark sur HDFS et SQL Server dans la base de données. Pour SQL Server, le **RxInSqlServer** fonction est utilisée pour les connexions au serveur et le passage d’objets entre l’ordinateur local et le contexte d’exécution à distance.

## <a name="create-and-set-a-compute-context"></a>Créer et définir un contexte de calcul

Le **RxInSqlServer** fonction qui crée le contexte de calcul SQL Server utilise les informations suivantes :

+ Chaîne de connexion pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance
+ Spécification du mode de traitement de sortie
+ Spécification facultative d’un répertoire de données partagée
+ Arguments facultatifs qui activent le suivi ou de spécifient le niveau de trace

Cette section vous guide tout au long de chaque partie.

1. Spécifiez la chaîne de connexion pour l’instance où les calculs sont effectués. Vous pouvez réutiliser la chaîne de connexion que vous avez créé précédemment.

    **Utilisation d’une connexion SQL**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user nme>;Pwd=<password>"
      ```

    **Avec l’authentification Windows**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=RevoDeepDive;Trusted_Connection=True"
    ```
    
2. Spécifiez la façon dont vous voulez gérer la sortie. Le script suivant indique à la session R locale pour attendre les résultats de la tâche R sur le serveur avant de traiter l’opération suivante. Il supprime également la sortie des calculs distants d’apparaître dans la session locale.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    L’argument *wait* pour **RxInSqlServer** prend en charge ces options :
  
    -   **TRUE**. La tâche est configurée en tant que le blocage et ne retourne pas jusqu'à ce qu’il s’est terminée ou a échoué.  Pour plus d’informations, consultez [distribué et calcul parallèle dans Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Travaux sont configurés en tant que non bloquant et retournent immédiatement, ce qui vous permet de continuer à exécuter tout autre code R. Toutefois, même en mode non bloquant, la connexion client à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être maintenue pendant l’exécution de la tâche.

3. Si vous le souhaitez, spécifiez l’emplacement d’un répertoire local pour une utilisation partagée par la session R locale et distante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur et ses comptes.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
   Si vous souhaitez créer manuellement un répertoire spécifique pour le partage, vous pouvez ajouter une ligne comme suit :

    ```R
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Passer des arguments à la **RxInSqlServer** constructeur pour créer le *objet de contexte de calcul*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    La syntaxe de **RxInSqlServer** est quasiment identique à celle de la **RxSqlServerData** fonction que vous avez utilisé précédemment pour définir la source de données. Toutefois, il existe des différences importantes.
      
    - L’objet source de données (défini à l’aide de la fonction [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)) spécifie où sont stockées les données.
    
    - En revanche, le contexte de calcul défini à l’aide de la fonction [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) indique où les agrégations et autres calculs doivent avoir lieu.
    
    La définition d’un contexte de calcul n’affecte pas les autres calculs R génériques que vous pouvez effectuer sur votre station de travail, et ne modifie pas la source des données. Vous pouvez par exemple, définir un fichier texte local comme source de données, mais modifier le contexte de calcul de SQL Server et effectuer toutes vos lectures et résumés des données sur l’ordinateur SQL Server.

5. Activer le contexte de calcul à distance.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

6. Retourner des informations sur le contexte de calcul, y compris ses propriétés.

    ```R
    rxGetComputeContext()
    ```

7. Réinitialiser le contexte de calcul à l’ordinateur local en spécifiant le mot-clé « local » (la leçon suivante montre l’aide du contexte de calcul à distance).

    ```R
    rxSetComputeContext("local")
    ```

> [!Tip]
> Pour obtenir la liste des autres mots clés pris en charge par cette fonction, tapez `help("rxSetComputeContext")` sur une ligne de commande R.

## <a name="enable-tracing"></a>Activer le suivi

Il arrive parfois que les opérations fonctionnent sur votre contexte local, mais qu’elles rencontrent des problèmes quand elles sont exécutées dans un contexte de calcul distant. Si vous souhaitez analyser les problèmes ou analyser les performances, vous pouvez activer le suivi dans le contexte de calcul pour prendre en charge la résolution des problèmes de l’exécution.

1. Créer un nouveau contexte de calcul qui utilise la même chaîne de connexion, mais ajoutez les arguments *traceEnabled* et *traceLevel* à la **RxInSqlServer** constructeur.

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

2. Utilisez le [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) (fonction) pour spécifier le contexte de calcul le traçage activé par nom.

    ```R
    rxSetComputeContext(sqlComputeTrace)
    ```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment basculer des contextes de calcul pour exécuter du code R sur le serveur ou localement.

> [!div class="nextstepaction"]
> [Contextes de calcul du calcul des statistiques de synthèse dans locale et à distance](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)