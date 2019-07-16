---
title: Déplacer des données entre SQL Server et un fichier XDF à l’aide de RevoScaleR - SQL Server Machine Learning
description: Didacticiel pas à pas sur la façon de déplacer des données à l’aide de XDF et le langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: f5800f315ee09328908b612c18faf6c77a7ac13c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962211"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-server-and-revoscaler-tutorial"></a>Déplacer des données entre SQL Server et un fichier XDF (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie de la [RevoScaleR didacticiel](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette étape, apprenez à utiliser un fichier XDF pour transférer des données entre les contextes de calcul locaux et distants. Stockage des données dans un fichier XDF permet de vous permettent d’effectuer des transformations sur les données.

Lorsque vous avez terminé, vous utilisez les données dans le fichier pour créer un nouveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table. La fonction [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) peut appliquer des transformations aux données et effectue la conversion entre des trames de données et fichiers .xdf.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Créer une table SQL Server à partir d’un fichier XDF

Dans cet exercice, vous utilisez à nouveau les données de fraude de carte de crédit. Dans ce scénario, vous avez été invité à effectuer des analyses supplémentaires sur les utilisateurs dans les États de la Californie, de l’Oregon et de Washington. Pour être plus efficace, que vous avez décidé stocker des données pour uniquement ces États sur votre ordinateur local et utiliser uniquement le sexe de variables, titulaires de carte, l’état et solde.

1. Réutiliser la `stateAbb` variable que vous avez créé précédemment pour identifier les niveaux à inclure et les écrire dans une nouvelle variable, `statesToKeep`.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Résultats**
    
    CA|Ou|WA
    ----|----|----
    5\.|38|48
    
2. Définir les données que vous souhaitez déplacer à partir de SQL Server, à l’aide un [!INCLUDE[tsql](../../includes/tsql-md.md)] requête.  Plus tard vous utilisez cette variable en tant que le *inData* argument pour **rxImport**.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Vérifiez que la requête ne contient aucun caractère masqué, tel qu’un saut de ligne ou une tabulation.
  
3. Ensuite, définissez les colonnes à utiliser lorsque vous travaillez avec les données dans R. Par exemple, dans le jeu de données plus petits, vous devez uniquement trois niveaux de facteur, étant donné que la requête retourne des données de seulement trois états.  Appliquer le `statesToKeep` variable pour identifier les niveaux corrects à inclure.
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. La valeur est le contexte de calcul **local**, étant donné que vous souhaitez que toutes les données disponibles sur votre ordinateur local.
  
    ```R
    rxSetComputeContext("local")
    ```
    
    Le [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) fonction peut importer des données à partir de n’importe quelle source de données pris en charge dans un fichier XDF local. À l’aide d’une copie locale des données est pratique lorsque vous souhaitez effectuer de nombreuses analyses différentes sur les données, mais que vous souhaitez éviter d’exécuter la même requête maintes et maintes fois.

5. Créer l’objet de source de données en passant les variables précédemment définies en tant qu’arguments à **RxSqlServerData**.
  
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
  
    Le `localDs` objet retourné par la **rxImport** fonction est un léger **RxXdfData** objet de source de données qui représente le `ccFraud.xdf` le fichier de données stocké localement sur le disque.
  
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

8. Vous pouvez maintenant appeler différentes fonctions R pour analyser le **localDs** de l’objet, comme vous le feriez avec la source de données sur SQL Server. Par exemple, vous pouvez résumer par sexe :
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

## <a name="next-steps"></a>Étapes suivantes

Cette leçon conclut la série de didacticiels plusieurs partie sur **RevoScaleR** et SQL Server. Il vous a présenté plusieurs concepts liées aux données et de calculs, ce qui vous donne une base pour poursuivre sa lancée avec vos propres exigences de données et de projet.

Pour approfondir vos connaissances de **RevoScaleR**, vous pouvez revenir à la liste de didacticiels R pour parcourir les exercices que vous avez omis. Vous pouvez également consulter les articles de savoir-faire dans la table des matières pour plus d’informations sur les tâches générales.

> [!div class="nextstepaction"]
> [Didacticiels R pour SQL Server](sql-server-r-tutorials.md)