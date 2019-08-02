---
title: Définir et utiliser des contextes de calcul RevoScaleR
description: Didacticiel procédure pas à pas sur la définition d’un contexte de calcul à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c5fb28af293c549a9f5494ab08c6c01ebf5d2a20
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715543"
---
# <a name="define-and-use-compute-contexts-sql-server-and-revoscaler-tutorial"></a>Définir et utiliser des contextes de calcul (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans la leçon précédente, vous avez utilisé les fonctions **RevoScaleR** pour inspecter les objets de données. Cette leçon présente la fonction [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) , qui vous permet de définir un contexte de calcul pour une SQL Server distante. Avec un contexte de calcul distant, vous pouvez déplacer l’exécution de R d’une session locale vers une session à distance sur le serveur. 

> [!div class="checklist"]
> * En savoir plus sur les éléments d’un contexte de calcul SQL Server distant
> * Activer le suivi sur un objet de contexte de calcul

**RevoScaleR** prend en charge plusieurs contextes de calcul: Hadoop, Spark sur HDFS et SQL Server dans la base de données. Par SQL Server, la fonction **RxInSqlServer** est utilisée pour les connexions serveur et le passage d’objets entre l’ordinateur local et le contexte d’exécution distant.

## <a name="create-and-set-a-compute-context"></a>Créer et définir un contexte de calcul

La fonction **RxInSqlServer** qui crée le contexte de calcul SQL Server utilise les informations suivantes:

+ Chaîne de connexion pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’instance
+ Spécification de la façon dont la sortie doit être gérée
+ Spécification facultative d’un répertoire de données partagées
+ Arguments facultatifs qui activent le suivi ou spécifient le niveau de suivi

Cette section vous guide tout au long de chaque partie.

1. Spécifiez la chaîne de connexion pour l’instance dans laquelle les calculs sont effectués. Vous pouvez réutiliser la chaîne de connexion que vous avez créée précédemment.

    **Utilisation d’une connexion SQL**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user nme>;Pwd=<password>"
      ```

    **Avec l’authentification Windows**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=RevoDeepDive;Trusted_Connection=True"
    ```
    
2. Spécifiez la façon dont vous voulez gérer la sortie. Le script suivant indique à la session R locale d’attendre les résultats du travail R sur le serveur avant de traiter l’opération suivante. Elle supprime également de l’affichage de la sortie des calculs distants dans la session locale.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    L’argument *wait* pour **RxInSqlServer** prend en charge ces options :
  
    -   **TRUE**. La tâche est configurée en tant que blocage et n’est pas retournée tant qu’elle n’est pas terminée ou a échoué.  Pour plus d’informations, consultez la page relative [à l’informatique distribuée et parallèle dans machine learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Les tâches sont configurées comme non bloquantes et sont retournées immédiatement, ce qui vous permet de continuer à exécuter d’autres codes R. Toutefois, même en mode non bloquant, la connexion client à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être maintenue pendant l’exécution de la tâche.

3. Si vous le souhaitez, spécifiez l’emplacement d’un répertoire local pour une utilisation partagée par la session R locale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et par l’ordinateur distant et ses comptes.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
   Si vous souhaitez créer manuellement un répertoire spécifique pour le partage, vous pouvez ajouter une ligne semblable à la suivante:

    ```R
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Transmettez les arguments au constructeur **RxInSqlServer** pour créer l' *objet de contexte de calcul*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    La syntaxe de **RxInSqlServer** semble presque identique à celle de la fonction **RxSqlServerData** que vous avez utilisée précédemment pour définir la source de données. Toutefois, il existe des différences importantes.
      
    - L’objet source de données (défini à l’aide de la fonction [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)) spécifie où sont stockées les données.
    
    - En revanche, le contexte de calcul, défini à l’aide de la fonction [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) , indique où les agrégations et autres calculs doivent avoir lieu.
    
    La définition d’un contexte de calcul n’affecte pas les autres calculs R génériques que vous pouvez effectuer sur votre station de travail, et ne modifie pas la source des données. Vous pouvez par exemple, définir un fichier texte local comme source de données, mais modifier le contexte de calcul de SQL Server et effectuer toutes vos lectures et résumés des données sur l’ordinateur SQL Server.

5. Activez le contexte de calcul distant.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

6. Retourne des informations sur le contexte de calcul, y compris ses propriétés.

    ```R
    rxGetComputeContext()
    ```

7. Réinitialisez le contexte de calcul sur l’ordinateur local en spécifiant le mot clé «local» (la leçon suivante montre l’utilisation du contexte de calcul distant).

    ```R
    rxSetComputeContext("local")
    ```

> [!Tip]
> Pour obtenir la liste des autres mots clés pris en charge par cette fonction, tapez `help("rxSetComputeContext")` sur une ligne de commande R.

## <a name="enable-tracing"></a>Activer le suivi

Il arrive parfois que les opérations fonctionnent sur votre contexte local, mais qu’elles rencontrent des problèmes quand elles sont exécutées dans un contexte de calcul distant. Si vous souhaitez analyser les problèmes ou surveiller les performances, vous pouvez activer le suivi dans le contexte de calcul afin de prendre en charge le dépannage au moment de l’exécution.

1. Créez un contexte de calcul qui utilise la même chaîne de connexion, mais ajoutez les arguments *traceEnabled* et *TraceLevel* au constructeur **RxInSqlServer** .

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

2. Utilisez la fonction [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) pour spécifier le contexte de calcul activé pour le suivi par nom.

    ```R
    rxSetComputeContext(sqlComputeTrace)
    ```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment basculer les contextes de calcul pour exécuter du code R sur le serveur ou localement.

> [!div class="nextstepaction"]
> [Calculer les statistiques de résumé dans les contextes de calcul locaux et distants](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)