---
title: "Effectuer une analyse de segmentation &#224; l’aide de rxDataStep (Immersion dans la science des donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 4290ee5f-be90-446a-91e8-3095d694bd82
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Effectuer une analyse de segmentation &#224; l’aide de rxDataStep (Immersion dans la science des donn&#233;es)
La fonction *rxDataStep* peut être utilisée pour traiter les données en segments, plutôt que d’exiger que l’ensemble du dataset soit chargé en mémoire et traité en une seule fois, comme avec le R traditionnel. Vous lisez donc les segments de données et utilisez les fonctions R pour traiter chaque segment de données l’une après l’autre, puis vous écrivez la synthèse des résultats de chaque segment dans une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commune.  
  
Dans cette leçon, vous vous exercerez à cette technique en utilisant la fonction *table* de R pour calculer un tableau de contingence.  
  
> [!TIP]  
> Cet exemple est fourni à des fins pédagogiques uniquement. Si vous avez besoin de générer des datasets réels, nous vous recommandons d’utiliser les fonctions *rxCrossTabs* ou *rxCube* intégrées à **RevoScaleR**, qui sont optimisées pour ce genre d’opération.  
  
## Partitionner les données par valeurs  
  
1.  Tout d’abord, créez une fonction R personnalisée nommée *ProcessChunk* qui appelle la fonction *table* pour chaque segment de données.  
  
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
 
  
2.  Définissez le contexte de calcul sur le serveur.  
  
    ```R  
    rxSetComputeContext( sqlCompute )   
    ```  
  
3.  Vous allez définir une source de données SQL Server pour stocker les données que vous traitez. Commencez par attribuer une requête SQL à une variable.   
  
    ```R  
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"   
    ```  

4.  Branchez cette variable dans l’argument *sqlQuery* d’une nouvelle source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```R  
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,  
        connectionString = sqlConnString,    
        rowsPerRead = 50000,      
        colInfo = list(DayOfWeek = list(type = "factor",   
            levels = as.character(1:7))))    
    ```  
     Si vous avez exécuté *rxGetVarInfo* dans cette source de données, vous verrez qu’elle contient une seule colonne : *Var 1: DayOfWeek, Type: factor, no factor levels available*
     
5.  Avant d’appliquer cette variable de facteur à la source de données, créez une autre table pour stocker les résultats intermédiaires. Là encore, vous utilisez simplement la fonction *RxSqlServerData* pour définir les données et supprimer des tables existantes du même nom.   
  
    ```R  
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)   
    # Check whether the table already exists.  
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }   
    ```  
  
7.  À présent, vous devez appeler la fonction personnalisée *ProcessChunk* permettant de transformer les données à mesure qu’elles sont lues, en l’utilisant comme l’argument *transformFunc* de la fonction *rxDataStep*.  
  
    ```R  
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)   
    ```  
  
8.  Pour afficher les résultats intermédiaires de *ProcessChunk*, affectez les résultats de *rxImport* à une variable, puis affichez les résultats dans la console.  
  
    ```R  
    iroResults <- rxImport(iroDataSource)   
  
    iroResults   
    ```  

**Résultats partiels**

|      |     1  |   2   |  3   |  4   |  5  |   6   |  7 |
| --- | ---  | --- | ---  |  ---  | ---  | ---  | --- |
|  1 | 8228 | 8924 | 6916 | 6932 | 6944 | 5602 | 6454 |
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
  
10. Pour supprimer la table de résultats intermédiaires, rappelez la fonction *rxSqlServerDropTable*.  
  
    ```R  
    rxSqlServerDropTable( table = "iroResults",     connectionString = sqlConnString)    
    ```  
  
## Étape suivante  
[Leçon 4 : Analyser les données dans le contexte de calcul local &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
## Étape précédente  
[Créer une table SQL Server à l’aide de rxDataStep &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/create-new-sql-server-table-using-rxdatastep-data-science-deep-dive.md)  
  
## Voir aussi  
[Immersion dans la science des données : utilisation des packages RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
