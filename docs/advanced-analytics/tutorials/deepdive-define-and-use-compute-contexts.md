---
title: "Définir et utiliser des contextes de calcul (Immersion dans la science des données) | Microsoft Docs"
ms.custom: 
ms.date: 05/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: b13058d0-9c6a-44e1-849b-72189d9050ba
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a682a40a9a62af3e1ff18ec0cc777ac9c1da7a9e
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="define-and-use-compute-contexts"></a>Définir et utiliser des contextes de calcul


Supposons que vous souhaitiez effectuer des calculs parmi les plus complexes sur le serveur, plutôt que sur votre ordinateur local. Pour ce faire, vous pouvez créer un contexte de calcul qui permet au code R de s’exécuter sur le serveur.

La fonction **RxInSqlServer** est l’une des fonctions R améliorées fournies dans le package [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) . La fonction gère les tâches de création de la connexion de base de données et de transmission des objets entre l’ordinateur local et le contexte d’exécution distant.

Dans cette étape, vous allez apprendre à utiliser la fonction **RxInSqlServer** pour définir un contexte de calcul.

Pour créer un contexte de calcul, vous avez besoin des informations de base suivantes sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :

- La chaîne de connexion pour l’instance
- Une spécification pour le traitement de la sortie
- Des arguments facultatifs pour l’activation du suivi, ou pour spécifier un répertoire partagé

## <a name="create-and-set-a-compute-context"></a>Créer et définir un contexte de calcul

1. Spécifiez la chaîne de connexion pour l’instance dans laquelle ont lieu les calculs.  Il s’agit de l’une des nombreuses variables que vous passez à la fonction *RxInSqlServer* pour créer le contexte de calcul. Vous pouvez soit réutiliser la chaîne de connexion créée précédemment, soit en créer une autre si vous souhaitez déplacer les calculs sur un autre serveur ou utiliser une identité différente.

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
  
    L’argument *wait* pour *RxInSqlServer* prend en charge ces options :
  
    -   **TRUE**. La tâche a une action bloquante et ne retourne aucun résultat tant qu’elle n’est pas terminée ou qu’elle n’a pas échoué.  Pour plus d’informations, consultez [distribué et le calcul parallèle dans Microsoft R](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing).
  
    -   **FALSE**. Les tâches n’ont pas d’action bloquante et retournent immédiatement les résultats, ce qui vous permet de continuer à exécuter un autre code R. Toutefois, même en mode non bloquant, la connexion client à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être maintenue pendant l’exécution de la tâche.

3. Si vous le souhaitez, vous pouvez spécifier l’emplacement d’un répertoire local pour une utilisation partagée par la session R locale et par l’ordinateur distant  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ses comptes.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
4. Si vous souhaitez créer manuellement un répertoire spécifique pour le partage, vous pouvez ajouter une ligne semblable à celle-ci. Pour déterminer le dossier utilisé pour le partage, exécutez `rxGetComputeContext`, qui retourne le contexte de calcul plus d’informations sur en cours. Pour plus d’informations, consultez la [documentation de référence ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinsqlserver).

    ```
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Avoir préparé toutes les variables, de les fournir en tant qu’arguments au constructeur RxInSqlServer pour créer le *objet de contexte de calcul*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    Vous pouvez observer que la syntaxe pour RxInSqlServer * est quasiment identique à celui de la fonction RxSqlServerData que vous avez utilisé précédemment pour définir la source de données. Toutefois, il existe des différences importantes.
      
    - L’objet de source de données, défini à l’aide de la fonction RxSqlServerData, spécifie où les données sont stockées.
    
    - En revanche, le contexte de calcul (défini à l’aide de la fonction RxInSqlServer) indique où les agrégations et autres calculs doivent avoir lieu.
    
    La définition d’un contexte de calcul n’affecte pas les autres calculs R génériques que vous pouvez effectuer sur votre station de travail, et ne modifie pas la source des données. Vous pouvez par exemple, définir un fichier texte local comme source de données, mais modifier le contexte de calcul de SQL Server et effectuer toutes vos lectures et résumés des données sur l’ordinateur SQL Server.

## <a name="enable-tracing-on-the-compute-context"></a>Activer le traçage sur le contexte de calcul

Il arrive parfois que les opérations fonctionnent sur votre contexte local, mais qu’elles rencontrent des problèmes quand elles sont exécutées dans un contexte de calcul distant. Si vous souhaitez analyser les problèmes ou suivre les performances, vous pouvez activer le suivi dans le contexte de calcul, pour que la résolution des problèmes d’exécution soit prise en charge.

1. Créer un nouveau contexte de calcul qui utilise la même chaîne de connexion, mais ajouter les arguments *traceEnabled* et *traceLevel* à la *RxInSqlServer* constructeur.

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

2. Pour modifier le contexte de calcul, utilisez la fonction rxSetComputeContext et spécifier le contexte par nom.

    ```R
    rxSetComputeContext( sqlComputeTrace)
    ```

    > [!NOTE]
    > 
    > Pour ce didacticiel, nous allons utiliser le contexte de calcul pour lequel le traçage n’est pas activé. C’est parce que les performances de l’option de suivi n’a pas été testé pour toutes les opérations.
    > 
    > Toutefois, si vous décidez d’utiliser le suivi, sachez que votre expérience peut-être être affectée par une connectivité réseau.

Maintenant que vous avez créé un contexte de calcul à distance, vous allez apprendre à modifier le calcul des contextes, pour exécuter le code R sur le serveur ou localement.

## <a name="next-step"></a>Étape suivante

[Créer et exécuter des Scripts R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)


## <a name="previous-step"></a>Étape précédente

[Interroger et modifier les données du serveur SQL](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)


