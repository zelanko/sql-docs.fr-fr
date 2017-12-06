---
title: "Effectuer une analyse de segmentation à l’aide de rxDataStep | Documents Microsoft"
ms.custom: 
ms.date: 05/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 4290ee5f-be90-446a-91e8-3095d694bd82
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 245bf9cf48b833a87b96666f1c050ca8fc1b4dbc
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="perform-chunking-analysis-using-rxdatastep"></a>Effectuer une analyse de segmentation à l’aide de rxDataStep

La fonction **rxDataStep** peut être utilisée pour traiter les données en segments, plutôt que d’exiger que l’ensemble du dataset soit chargé en mémoire et traité en une seule fois, comme avec le R traditionnel. Vous lisez donc les segments de données et utilisez les fonctions R pour traiter chaque segment de données l’une après l’autre, puis vous écrivez la synthèse des résultats de chaque segment dans une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commune.

Dans cette leçon, vous allez essayer cette technique à l’aide de la `table` fonction dans R, calculer une table d’urgence.

> [!TIP]
> Cet exemple est fourni à des fins pédagogiques uniquement. Si vous avez besoin générer des jeux de données réelles, nous vous recommandons d’utiliser le **rxCrossTabs** ou **rxCube** dans les fonctions **RevoScaleR**, qui sont optimisés pour ce type d’opération.

## <a name="partition-data-by-values"></a>Partitionner les données par valeurs

1. Tout d’abord, créez une fonction R personnalisée qui appelle la *table* la fonction sur chaque segment de données et nommez-le `ProcessChunk`.
  
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
    rxSetComputeContext( sqlCompute )
    ```
  
3. Vous allez définir une source de données SQL Server pour stocker les données que vous traitez. Commencez par attribuer une requête SQL à une variable.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    ```

4. Branchez cette variable dans l’argument *sqlQuery* d’une nouvelle source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```
     Si vous avez exécuté *rxGetVarInfo* dans cette source de données, vous verrez qu’elle contient une seule colonne : *Var 1: DayOfWeek, Type: factor, no factor levels available*
     
5. Avant d’appliquer cette variable de facteur à la source de données, créez une autre table pour stocker les résultats intermédiaires. Là encore, vous utilisez simplement la fonction RxSqlServerData pour définir les données et supprimez des tables existantes du même nom.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Maintenant vous devez appeler la fonction personnalisée `ProcessChunk` pour transformer les données qu’il est lu à l’aide en tant que le *transformfunc est utilisé* l’argument de la fonction rxDataStep.
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Pour afficher les résultats intermédiaires du `ProcessChunk`, affecter les résultats de rxImport à une variable, puis génère les résultats dans la console.
  
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

10. Pour supprimer la table de résultats intermédiaires, appeler une autre rxSqlServerDropTable.
  
    ```R
    rxSqlServerDropTable( table = "iroResults",     connectionString = sqlConnString)
    ```

## <a name="next-step"></a>Étape suivante

[Analyser les données dans le contexte de calcul Local ;](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)

## <a name="previous-step"></a>Étape précédente

[Créer la nouvelle Table SQL Server à l’aide de rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)


