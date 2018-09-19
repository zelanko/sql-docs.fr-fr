---
title: Définir et utiliser des contextes de calcul (SQL et R immersion) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6a76e07cb2ecd03a59112f6c39e3fa2f7895e0a2
ms.sourcegitcommit: aa9d2826e3c451f4699c0e69c9fcc8a2781c6213
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45975638"
---
# <a name="define-and-use-compute-contexts-sql-and-r-deep-dive"></a>Définir et utiliser des contextes de calcul (SQL et R immersion)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fait partie du didacticiel de présentation approfondie de science des données, comment utiliser [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Cette leçon présente la [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) (fonction), qui vous permet de définir un contexte de calcul pour SQL Server, puis exécutez des calculs complexes sur le serveur, plutôt que sur votre ordinateur local. 

RevoScaleR prend en charge plusieurs contextes de calcul, afin que vous puissiez exécuter le code R dans Hadoop, Spark ou dans la base de données. Pour SQL Server, vous définissez le serveur, et la fonction gère les tâches de création des objets de connexion et en passant entre l’ordinateur local et le contexte d’exécution à distance de la base de données.

La fonction qui crée le serveur SQL Server de calcul contexte utilise les informations suivantes :

- Chaîne de connexion pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance
- Spécification du mode de traitement de sortie
- Arguments facultatifs qui activent le suivi ou de spécifient le niveau de trace
- Spécification facultative d’un répertoire de données partagée

## <a name="create-and-set-a-compute-context"></a>Créer et définir un contexte de calcul

1. Spécifiez la chaîne de connexion pour l’instance où les calculs sont effectués.  Vous pouvez réutiliser la chaîne de connexion que vous avez créé précédemment. Vous pouvez créer une chaîne de connexion différente si vous souhaitez déplacer les calculs sur un autre serveur, ou utiliser une connexion différente pour effectuer certaines tâches.

    **Utilisation d’une connexion SQL**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user name>;Pwd=<password>"
      ```

    **Avec l’authentification Windows**

      ```R
      sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"
      ```
2. Spécifiez la façon dont vous voulez gérer la sortie. Dans le code suivant, vous indiquez que la session R sur la station de travail doit toujours attendre les résultats de la tâche R, mais pas retourner la sortie de console des calculs distants.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    L’argument *wait* pour **RxInSqlServer** prend en charge ces options :
  
    -   **TRUE**. La tâche est configurée en tant que le blocage et ne retourne pas jusqu'à ce qu’il s’est terminée ou a échoué.  Pour plus d’informations, consultez [distribué et calcul parallèle dans Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).
  
    -   **FALSE**. Travaux sont configurés en tant que non bloquant et retournent immédiatement, ce qui vous permet de continuer à exécuter tout autre code R. Toutefois, même en mode non bloquant, la connexion client à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être maintenue pendant l’exécution de la tâche.

3. Si vous le souhaitez, vous pouvez spécifier l’emplacement d’un répertoire local pour une utilisation partagée par la session R locale et distante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur et ses comptes.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. Si vous souhaitez créer manuellement un répertoire spécifique pour le partage, vous pouvez ajouter une ligne comme suit :

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

    Pour déterminer le dossier utilisé pour le partage, exécutez `rxGetComputeContext()`, qui retourne plus d’informations sur l’actuel contexte de calcul. Pour plus d’informations, consultez la [documentation de référence ScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/).

4. Après avoir préparé toutes les variables, fournissez-les comme arguments pour le **RxInSqlServer** constructeur, pour créer le *objet de contexte de calcul*.

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

## <a name="enable-tracing-on-the-compute-context"></a>Activer le suivi sur le contexte de calcul

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

2. Pour changer de contexte de calcul, utilisez la fonction [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) et spécifiez le contexte par son nom.

    ```R
    rxSetComputeContext( sqlComputeTrace)
    ```

    > [!NOTE]
    > 
    > Pour ce didacticiel, utilisez le contexte de calcul qui n’a pas le suivi est activé. 
    > 
    > Toutefois, si vous décidez d’utiliser le suivi, sachez que votre expérience peut être affectée par une connectivité réseau. Sachez également que, car les performances pour l’option de suivi n’a pas été testée pour toutes les opérations.

Dans l’étape suivante, que vous allez apprendre à utiliser des contextes, localement ou à exécuter le code R sur le serveur de calcul.

## <a name="next-step"></a>Étape suivante

[Créer et exécuter des scripts R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)

## <a name="previous-step"></a>Étape précédente

[Interroger et modifier les données SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
