---
title: Analyse de segmentation dans RevoScaleR
description: 'Tutoriel RevoScaleR 12 : Comment segmenter des données pour effectuer une analyse distribuée à l’aide du langage R sur SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0ad082c3a21292b782d5888b48b698c986c0b5b2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "74947210"
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Effectuer une analyse de segmentation à l’aide de rxDataStep (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Il s’agit du tutoriel 12 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans ce tutoriel, vous allez utiliser la fonction **rxDataStep** pour traiter les données en segments, plutôt que d’exiger que l’ensemble du jeu de données soit chargé en mémoire et traité en une seule fois, comme avec le langage R traditionnel. La fonction **rxDataStep** lit les segments de données, applique les fonctions R à chaque segment de données l’une après l’autre, puis enregistre la synthèse des résultats de chaque segment dans une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commune. Lorsque toutes les données ont été lues, les résultats sont combinés.

> [!TIP]
> Pour ce tutoriel, vous calculez une table d’urgence à l’aide de la fonction **table** dans R. Cet exemple est destiné à des fins pédagogiques uniquement. 
> 
> Si vous avez besoin de générer des jeux de données réels, nous vous recommandons d’utiliser les fonctions **rxCrossTabs** ou **rxCube** dans **RevoScaleR**, qui sont optimisées pour ce genre d’opération.

## <a name="partition-data-by-values"></a>Partitionner les données par valeurs

1. Créez une fonction R personnalisée qui appelle la fonction **table** pour chaque segment de données et nommez la nouvelle fonction **ProcessChunk**.
  
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
  
3. Définissez une source de données SQL Server pour stocker les données que vous traitez. Commencez par attribuer une requête SQL à une variable. Utilisez ensuite cette variable dans l’argument *sqlQuery* d’une nouvelle source de données SQL Server.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```

4. Si vous le souhaitez, vous pouvez exécuter **rxGetVarInfo** sur cette source de données. À ce stade, elle contient une seule colonne : *Var 1 : DayOfWeek, Type : facteur, aucun niveau de facteur disponible*
     
5. Avant d’appliquer cette variable de facteur à la source de données, créez une autre table pour stocker les résultats intermédiaires. Là encore, vous utilisez simplement la fonction **RxSqlServerData** pour définir les données et supprimer des tables existantes du même nom.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Appelez la fonction personnalisée **ProcessChunk** permettant de transformer les données à mesure qu’elles sont lues, en l’utilisant comme l’argument *transformFunc* de la fonction **rxDataStep**.
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Pour afficher les résultats intermédiaires de **ProcessChunk**, affectez les résultats de **rxImport** à une variable, puis affichez les résultats dans la console.
  
    ```R
    iroResults <- rxImport(iroDataSource)
    iroResults
    ```

    **Résultats partiels**

    |      |    1  |   2   |  3   |  4   |  5  |   6   |  7 |
    | --- | ---  | --- | ---  |  ---  | ---  | ---  | --- |
    | 1 | 8228 | 8924 | 6916 | 6932 | 6944 | 5602 | 6454 |
    | 2  | 8321  | 5351 | 7329 | 7411 | 7409 | 6487 | 7692 |

9. Pour calculer les résultats finaux de l’ensemble des segments, additionnez les colonnes et affichez les résultats dans la console.

    ```R
    finalResults <- colSums(iroResults)
    finalResults
    ```

    **Résultats**

    1  |   2  |   3  |   4  |   5  |   6  |   7
    ---  |   ---  |   ---  |   ---  |   ---  |   ---  |   ---
    97975 | 77725 | 78875 | 81304 | 82987 | 86159 | 94975 

10. Pour supprimer la table de résultats intermédiaires, appelez **rxSqlServerDropTable**.
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Didacticiels R pour SQL Server](sql-server-r-tutorials.md)