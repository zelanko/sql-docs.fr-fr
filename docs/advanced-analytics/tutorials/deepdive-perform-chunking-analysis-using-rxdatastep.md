---
title: Effectuer une analyse de segmentation à l’aide de RevoScaleR rxDataStep
description: Didacticiel procédure pas à pas sur la façon de segmenter des données pour l’analyse distribuée à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3aa0b42c9806e8d8972f31c69b1b33b222c43287
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469709"
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Effectuer une analyse de segmentation à l’aide de rxDataStep (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette leçon, vous utilisez la fonction **rxDataStep** pour traiter les données en segments, plutôt que d’exiger que l’ensemble du jeu de données soit chargé en mémoire et traité en une seule fois, comme dans R traditionnel. Les fonctions **rxDataStep** lisent les données en bloc, appliquent des fonctions R à chaque segment de données, puis enregistre les résultats de synthèse pour chaque segment dans une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données commune. Lorsque toutes les données ont été lues, les résultats sont combinés.

> [!TIP]
> Pour cette leçon, vous calculez une table de contingence à l’aide de la fonction **table** dans R. Cet exemple est destiné à des fins pédagogiques uniquement. 
> 
> Si vous avez besoin de classer les jeux de données réels, nous vous recommandons d’utiliser les fonctions **rxCrossTabs** ou **rxCube** dans **RevoScaleR**, qui sont optimisées pour ce type d’opération.

## <a name="partition-data-by-values"></a>Partitionner les données par valeurs

1. Créez une fonction R personnalisée qui appelle la fonction de **table** r sur chaque segment de données et nommez la nouvelle fonction **ProcessChunk**.
  
    ```R
    ProcessChunk <- function( dataList) {
    # Convert the input list to a data frame and compute contingency table
    chunkTable <- table(as.data.frame(dataList))
  
    # Convert table output to a data frame with a single row
    varNames <- names(chunkTable)
    varValues <- as.vector(chunkTable)
    dim(varValues) <- c(1, length(varNames))
    chunkDF <- as.data.frame(varValues)
    names(chunkDF) <- varNames
  
    # Return the data frame, which has a single row
    return( chunkDF )
    }
    ```

2. Définissez le contexte de calcul sur le serveur.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
3. Définissez une source de données SQL Server pour stocker les données que vous traitez. Commencez par attribuer une requête SQL à une variable. Utilisez ensuite cette variable dans l’argument *SQLQuery* d’une nouvelle source de données SQL Server.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```

4. Si vous le souhaitez, vous pouvez exécuter **rxGetVarInfo** sur cette source de données. À ce stade, elle contient une seule colonne: *Var 1: DayOfWeek, type: facteur, aucun niveau de facteur disponible*
     
5. Avant d’appliquer cette variable de facteur à la source de données, créez une autre table pour stocker les résultats intermédiaires. Là encore, vous utilisez simplement la fonction **RxSqlServerData** pour définir les données, en veillant à supprimer toutes les tables existantes portant le même nom.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Appelez la fonction personnalisée **ProcessChunk** pour transformer les données au fur et à mesure de leur lecture, en l’utilisant comme argument *transformfunc est utilisé* pour la fonction **rxDataStep** .
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Pour afficher les résultats intermédiaires de **ProcessChunk**, assignez les résultats de **rxImport** à une variable, puis affichez les résultats dans la console.
  
    ```R
    iroResults <- rxImport(iroDataSource)
    iroResults
    ```

    **Résultats partiels**

    |      |    1  |   2   |  3   |  4   |  5  |   6\.   |  7 |
    | --- | ---  | --- | ---  |  ---  | ---  | ---  | --- |
    | 1 | 8228 | 8924 | 6916 | 6932 | 6944 | 5602 | 6454 |
    | 2  | 8321  | 5351 | 7329 | 7411 | 7409 | 6487 | 7692 |

9. Pour calculer les résultats finaux de l’ensemble des segments, additionnez les colonnes et affichez les résultats dans la console.

    ```R
    finalResults <- colSums(iroResults)
    finalResults
    ```

    **Résultats**

    1  |   2  |   3  |   4  |   5  |   6\.  |   7
    ---  |   ---  |   ---  |   ---  |   ---  |   ---  |   ---
    97975 | 77725 | 78875 | 81304 | 82987 | 86159 | 94975 

10. Pour supprimer la table de résultats intermédiaires, effectuez un appel à **rxSqlServerDropTable**.
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Didacticiels R pour SQL Server](sql-server-r-tutorials.md)