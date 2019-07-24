---
title: Déplacer des données entre SQL Server et un fichier XDF à l’aide de RevoScaleR
description: Didacticiel pas à pas sur la façon de déplacer des données à l’aide de XDF et du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0e4c0fbdd9f625886a7d38fc80895e9f4407ce88
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344752"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-server-and-revoscaler-tutorial"></a>Déplacer des données entre SQL Server et un fichier XDF (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette étape, vous allez apprendre à utiliser un fichier baXDF pour transférer des données entre des contextes de calcul locaux et distants. Le stockage des données dans un fichier XDF vous permet d’effectuer des transformations sur les données.

Lorsque vous avez terminé, vous utilisez les données du fichier pour créer une nouvelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table. La fonction [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) peut appliquer des transformations aux données et effectue la conversion entre les trames de données et les fichiers. XDF.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Créer une table SQL Server à partir d’un fichier baXDF

Pour cet exercice, vous utilisez à nouveau les données de fraude de carte de crédit. Dans ce scénario, vous avez été invité à effectuer des analyses supplémentaires sur les utilisateurs dans les États de la Californie, de l’Oregon et de Washington. Pour être plus efficace, vous avez décidé de stocker les données pour ces seuls États sur votre ordinateur local et vous travaillez uniquement avec les variables sexe, détenteur, État et équilibre.

1. Réutilisez la `stateAbb` variable que vous avez créée précédemment pour identifier les niveaux à inclure, puis écrivez-les dans une nouvelle `statesToKeep`variable.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Résultats**
    
    CA|Ou|WA
    ----|----|----
    5\.|38|48
    
2. Définissez les données que vous souhaitez mettre en avant SQL Server à l’aide [!INCLUDE[tsql](../../includes/tsql-md.md)] d’une requête.  Plus tard, vous utilisez cette variable  en tant qu’argument inData pour **rxImport**.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Vérifiez que la requête ne contient aucun caractère masqué, tel qu’un saut de ligne ou une tabulation.
  
3. Ensuite, définissez les colonnes à utiliser lors de l’utilisation des données dans R. Par exemple, dans le jeu de données plus petit, vous n’avez besoin que de trois niveaux de facteur, car la requête retourne des données pour seulement trois États.  Appliquez la `statesToKeep` variable pour identifier les niveaux corrects à inclure.
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. Définissez le contexte de calcul sur **local**, car vous souhaitez que toutes les données soient disponibles sur votre ordinateur local.
  
    ```R
    rxSetComputeContext("local")
    ```
    
    La fonction [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) peut importer des données à partir de n’importe quelle source de données prise en charge dans un fichier XDF local. L’utilisation d’une copie locale des données est pratique lorsque vous souhaitez effectuer de nombreuses analyses différentes sur les données, mais que vous souhaitez éviter d’exécuter la même requête.

5. Créez l’objet de source de données en passant les variables précédemment définies comme arguments à **RxSqlServerData**.
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. Appelez **rxImport** pour écrire les données dans un fichier nommé `ccFraudSub.xdf`, dans le répertoire de travail actuel.
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    L' `localDs` objet retourné par la fonction **rxImport** est un objet de source de données **RxXdfData** léger qui représente le `ccFraud.xdf` fichier de données stocké localement sur le disque.
  
7. Appelez [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) dans le fichier XDF pour vérifier que le schéma de données est le même.
  
    ```R
    rxGetVarInfo(data = localDS)
    ```

    **Résultats**
    
    ```R
    rxGetVarInfo(data = localDS)
    Var 1: gender, Type: factor, no factor levels available
    Var 2: cardholder, Type: factor, no factor levels available
    Var 3: balance, Type: integer, Low/High: (0, 22463)
    Var 4: state, Type: factor, no factor levels available
    ```

8. Vous pouvez maintenant appeler différentes fonctions R pour analyser l’objet **localDs** , comme vous le feriez avec les données sources sur SQL Server. Par exemple, vous pouvez résumer par sexe:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

## <a name="next-steps"></a>Étapes suivantes

Cette leçon conclut la série de didacticiels en plusieurs parties sur **RevoScaleR** et SQL Server. Il vous a présenté de nombreux concepts liés aux données et à la calcul, ce qui vous donne une base pour vous faire progresser avec vos propres exigences en matière de données et de projet.

Pour approfondir votre connaissance de **RevoScaleR**, vous pouvez revenir à la liste des didacticiels R pour parcourir les exercices que vous avez pu manquer. Vous pouvez également consulter les Articles de procédure dans la table des matières pour plus d’informations sur les tâches générales.

> [!div class="nextstepaction"]
> [Didacticiels R pour SQL Server](sql-server-r-tutorials.md)