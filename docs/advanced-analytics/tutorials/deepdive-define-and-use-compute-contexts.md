---
title: Utiliser des contextes de calcul RevoScaleR
description: 'Tutoriel RevoScaleR 4 : Comment définir un contexte de calcul à l’aide du langage R sur SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c90c935f85584f8886ae112d5cfc03759c0a129a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "74947214"
---
# <a name="define-and-use-compute-contexts-sql-server-and-revoscaler-tutorial"></a>Définir et utiliser des contextes de calcul (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Il s’agit du tutoriel 4 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans le tutoriel précédent, vous avez utilisé les fonctions **RevoScaleR** pour inspecter les objets de données. Ce tutoriel présente la fonction [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver), qui vous permet de définir un contexte de calcul pour un SQL Server distant. Avec un contexte de calcul distant, vous pouvez déplacer l’exécution de R d’une session locale vers une session distante sur le serveur. 

> [!div class="checklist"]
> * Découvrir les éléments d’un contexte de calcul SQL Server distant
> * Activer le traçage sur l’objet de contexte de calcul

**RevoScaleR** prend en charge plusieurs contextes de calcul : Hadoop, Spark sur HDFS et SQL Server dans la base de données. Pour SQL Server, la fonction **RxInSqlServer** est utilisée pour les connexions au serveur et la transmission d’objets entre l’ordinateur local et le contexte d’exécution distant.

## <a name="create-and-set-a-compute-context"></a>Créer et définir un contexte de calcul

La fonction **RxInSqlServer** qui crée le contexte de calcul SQL Server utilise les informations suivantes :

+ Chaîne de connexion pour l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
+ Spécification pour le traitement de la sortie
+ Spécification facultative d’un répertoire de données partagées
+ Arguments facultatifs qui activent le traçage ou spécifient le niveau de trace

Cette section vous guide tout au long de chaque partie.

1. Spécifiez la chaîne de connexion pour l’instance dans laquelle ont lieu les calculs. Vous pouvez réutiliser la chaîne de connexion que vous avez créée précédemment.

    **Utilisation d’une connexion SQL**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL Server instance name>; Database=<database name>;Uid=<SQL user nme>;Pwd=<password>"
      ```

    **Avec l’authentification Windows**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=RevoDeepDive;Trusted_Connection=True"
    ```
    
2. Spécifiez la façon dont vous voulez gérer la sortie. Le script suivant indique à la session R locale d’attendre les résultats du travail R sur le serveur avant de traiter l’opération suivante. Il empêche également l’affichage dans la session locale du résultat des calculs distants.
  
    ```R
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```
  
    L’argument *wait* pour **RxInSqlServer** prend en charge ces options :
  
    -   **TRUE**. Le travail est configuré en tant qu’action bloquante et ne retourne aucun résultat tant qu’il n’est pas terminé ou qu’il n’a pas échoué.  Pour plus d’informations, consultez [Distributed and parallel computing in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) (Calculs distribués et parallèle dans Machine Learning Server).
  
    -   **FALSE**. Les travaux sont configurés en tant qu’actions non bloquantes et retournent immédiatement les résultats, ce qui vous permet de continuer à exécuter un autre code R. Toutefois, même en mode non bloquant, la connexion client à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être maintenue pendant l’exécution de la tâche.

3. Si vous le souhaitez, spécifiez l’emplacement d’un répertoire local pour une utilisation partagée par la session R locale et par l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] distant et ses comptes.

    ```R
    sqlShareDir <- paste("c:\\AllShare\\", Sys.getenv("USERNAME"), sep="")
    ```
    
   Si vous souhaitez créer manuellement un répertoire spécifique pour le partage, vous pouvez ajouter une ligne semblable à ce qui suit :

    ```R
    dir.create(sqlShareDir, recursive = TRUE)
    ```

4. Transmettez des arguments au constructeur **RxInSqlServer** pour créer *l’objet de contexte de calcul*.

    ```R
    sqlCompute <- RxInSqlServer(  
         connectionString = sqlConnString,
         wait = sqlWait,
         consoleOutput = sqlConsoleOutput)
    ```
    
    La syntaxe de **RxInSqlServer** est presque identique à celle de la fonction **RxSqlServerData** que vous avez utilisée précédemment pour définir la source de données. Toutefois, il existe des différences importantes.
      
    - L’objet source de données (défini à l’aide de la fonction [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)) spécifie où sont stockées les données.
    
    - En revanche, le contexte de calcul, défini à l’aide de la fonction [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver), indique où doivent avoir lieu les agrégations et autres calculs.
    
    La définition d’un contexte de calcul n’affecte pas les autres calculs R génériques que vous pouvez effectuer sur votre station de travail, et ne modifie pas la source des données. Vous pouvez par exemple, définir un fichier texte local comme source de données, mais modifier le contexte de calcul de SQL Server et effectuer toutes vos lectures et résumés des données sur l’ordinateur SQL Server.

5. Activez le contexte de calcul distant.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

6. Renvoyez des informations sur le contexte de calcul, y compris ses propriétés.

    ```R
    rxGetComputeContext()
    ```

7. Réinitialisez le contexte de calcul sur l’ordinateur local en spécifiant le mot clé « local » (le tutoriel suivant montre l’utilisation du contexte de calcul distant).

    ```R
    rxSetComputeContext("local")
    ```

> [!Tip]
> Pour obtenir la liste des autres mots clés pris en charge par cette fonction, tapez `help("rxSetComputeContext")` sur une ligne de commande R.

## <a name="enable-tracing"></a>Activer le traçage

Il arrive parfois que les opérations fonctionnent sur votre contexte local, mais qu’elles rencontrent des problèmes quand elles sont exécutées dans un contexte de calcul distant. Si vous souhaitez analyser les problèmes ou suivre les performances, vous pouvez activer le traçage dans le contexte de calcul, pour que la résolution des problèmes d’exécution soit prise en charge.

1. Créez un contexte de calcul qui utilise la même chaîne de connexion, mais ajoutez les arguments *traceEnabled* et *traceLevel* au constructeur **RxInSqlServer**.

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

2. Utilisez la fonction [rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) pour spécifier le contexte de calcul avec le traçage activé par son nom.

    ```R
    rxSetComputeContext(sqlComputeTrace)
    ```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment basculer entre les contextes de calcul pour exécuter du code R sur le serveur ou localement.

> [!div class="nextstepaction"]
> [Calculer des statistiques de synthèse dans des contextes de calcul locaux et distants](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)