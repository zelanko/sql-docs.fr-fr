---
title: Effectuer une analyse de segmentation à l’aide de rxDataStep RevoScaleR - SQL Server Machine Learning
description: Didacticiel pas à pas sur la façon de segmenter des données pour l’analyse distribuée à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c5d3b50af1f7db3a39dec0e475aa00582bc77e0a
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596030"
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Effectuer une analyse de segmentation à l’aide de rxDataStep (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie de la [RevoScaleR didacticiel](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette leçon, vous utilisez le **rxDataStep** fonction pour traiter les données en segments, plutôt que de nécessiter que l’ensemble du dataset être chargé en mémoire et traité en même temps, comme dans R. traditionnel Le **rxDataStep** fonctions lit les données dans le bloc, applique des fonctions R pour chaque segment de données à son tour et puis enregistre les synthèse des résultats pour chaque segment dans un commun [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données. Lorsque toutes les données ont été lues, les résultats sont combinés.

> [!TIP]
> Pour cette leçon, vous calculer un tableau de contingence en utilisant le **table** fonction dans R. Cet exemple est destiné uniquement à des fins pédagogiques. 
> 
> Si vous avez besoin tabuler les jeux de données réels, nous vous recommandons d’utiliser le **rxCrossTabs** ou **rxCube** dans les fonctions **RevoScaleR**, qui sont optimisés pour cela de quelque sorte opération.

## <a name="partition-data-by-values"></a>Partitionner les données par valeurs

1. Créer une fonction R personnalisée qui appelle R **table** fonction sur chaque segment de données, puis nommez la nouvelle fonction **ProcessChunk**.
  
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
  
3. Définir une source de données SQL Server pour stocker les données que vous traitez. Commencez par attribuer une requête SQL à une variable. Ensuite, utilisez cette variable dans le *sqlQuery* argument d’une nouvelle source de données SQL Server.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```

4. Si vous le souhaitez, vous pouvez exécuter **rxGetVarInfo** sur cette source de données. À ce stade, il contient une seule colonne : *Var 1 : DayOfWeek, Type : facteur, aucun niveau de facteur disponible*
     
5. Avant d’appliquer cette variable de facteur à la source de données, créez une autre table pour stocker les résultats intermédiaires. Là encore, vous utilisez simplement la **RxSqlServerData** (fonction) pour définir les données, en veillant à supprimer des tables existantes du même nom.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Appeler la fonction personnalisée **ProcessChunk** pour transformer les données qu’il est lu, en l’utilisant comme le *transformFunc* l’argument de la **rxDataStep** (fonction).
  
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

10. Pour supprimer la table de résultats intermédiaires, effectuez un appel à **rxSqlServerDropTable**.
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Didacticiels R pour SQL Server](sql-server-r-tutorials.md)