---
title: Visualiser les données de SQL Server à l’aide de RevoScaleR rxHistogram
description: Didacticiel procédure pas à pas sur la visualisation des données à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8c7e837f9ed4392a8ecfc9e7c237b95f3fdde3d3
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714852"
---
#  <a name="visualize-sql-server-data-using-r-sql-server-and-revoscaler-tutorial"></a>Visualiser les données de SQL Server à l’aide de R (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette leçon, utilisez les fonctions R pour afficher la distribution des valeurs dans la colonne *creditLine* par sexe.

> [!div class="checklist"]
> * Créer des variables min-max pour les entrées d’histogramme
> * Visualiser des données dans un histogramme à l’aide de **rxHistogram** à partir de **RevoScaleR**
> * Visualisez les nuages de points à l’aide de **levelplot** à partir d’un **treillis** inclus dans la distribution R de base

Comme le montre cette leçon, vous pouvez combiner des fonctions Open source et spécifiques à Microsoft dans le même script.

## <a name="add-maximum-and-minimum-values"></a>Ajouter des valeurs maximales et minimales

En fonction des statistiques de résumé calculées de la leçon précédente, vous avez découvert des informations utiles sur les données que vous pouvez insérer dans la source de données pour d’autres calculs. Par exemple, les valeurs minimales et maximales peuvent être utilisées pour calculer des histogrammes. Dans cet exercice, ajoutez les valeurs haute et basse à la source de données **RxSqlServerData** .

1. Commencez par configurer des variables temporaires.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Utilisez la variable *ccColInfo* que vous avez créée dans la leçon précédente pour définir les colonnes dans la source de données.
  
   Ajoutez de nouvelles colonnes calculées (*numTrans*, *numIntlTrans*et *creditLine*) à la collection de colonnes qui remplace la définition d’origine. Le script ci-dessous ajoute des facteurs basés sur des valeurs minimales et maximales, obtenus à partir de sumOut, qui stocke la sortie en mémoire à partir de **rxSummary**. 
  
    ```R 
    ccColInfo <- list(
        gender = list(type = "factor",
          levels = c("1", "2"), 
          newLevels = c("Male", "Female")),
        cardholder = list(type = "factor",
          levels = c("1", "2"), 
          newLevels = c("Principal", "Secondary")), 
        state = list(type = "factor", 
          levels = as.character(1:51), 
          newLevels = stateAbb), 
        balance  = list(type = "numeric"),
        numTrans = list(type = "factor", 
          levels = as.character(sumDF[var == "numTrans", "Min"]:sumDF[var == "numTrans", "Max"])),
        numIntlTrans = list(type = "factor",  
            levels = as.character(sumDF[var == "numIntlTrans", "Min"]:sumDF[var =="numIntlTrans", "Max"])),
        creditLine = list(type = "numeric")
            )
    ```
  
3. Après avoir mis à jour la collection de colonnes, appliquez l’instruction suivante pour créer une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version mise à jour de la source de données que vous avez définie précédemment.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    La source de données sqlFraudDS comprend désormais les nouvelles colonnes ajoutées à l’aide de *ccColInfo*.
  
À ce stade, les modifications affectent uniquement l’objet de source de données dans R; aucune nouvelle donnée n’a encore été écrite dans la table de base de données. Toutefois, vous pouvez utiliser les données capturées dans la variable sumOut pour créer des visualisations et des synthèses. 

> [!TIP]
> Si vous oubliez le contexte de calcul que vous utilisez, exécutez **rxGetComputeContext ()** . Une valeur de retour «RxLocalSeq Compute Context» indique que vous exécutez dans le contexte de calcul local.

## <a name="visualize-data-using-rxhistogram"></a>Visualiser les données à l’aide de rxHistogram

1. Le code R suivant permet d’appeler la fonction [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) et de passer une formule et une source de données. Le code peut être exécuté localement dans un premier temps, afin de voir les résultats attendus et combien de temps peut durer son exécution.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    En interne, **rxHistogram** appelle la fonction [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) , qui est incluse dans le package **RevoScaleR** . **rxCube** génère une liste unique (ou trame de données) contenant une colonne pour chaque variable spécifiée dans la formule, plus une colonne de nombres.
    
2. Maintenant, définissez le contexte de calcul sur l’ordinateur distant SQL Server, puis réexécutez **rxHistogram** .
  
    ```R
    rxSetComputeContext(sqlCompute)
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
3. Les résultats sont exactement les mêmes car vous utilisez la même source de données, mais à la deuxième étape, les calculs sont effectués sur le serveur distant. Les résultats sont ensuite renvoyés à votre station de travail locale à des fins de traçage.
   
  ![Résultats de l’histogramme](media/rsql-sue-histogramresults.jpg "Résultats de l’histogramme")


## <a name="visualize-with-scatter-plots"></a>Visualiser avec les nuages de points

Les nuages de points sont souvent utilisés lors de l’exploration des données pour comparer la relation entre deux variables. Vous pouvez utiliser des packages R intégrés à cet effet, avec les entrées fournies par les fonctions **RevoScaleR** .

1. Appelez la fonction [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) pour calculer la moyenne de *fraudRisk* pour chaque combinaison de *numTrans* et *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Pour spécifier les groupes utilisés pour calculer les moyennes de groupe, utilisez la notation `F()` . Dans cet exemple, `F(numTrans):F(numIntlTrans)` indique que les entiers dans les variables `numTrans` et `numIntlTrans` doivent être traités comme des variables catégoriques, avec un niveau pour chaque valeur entière.
  
    La valeur de retour par défaut de **rxCube** est un *objet rxCube*, qui représente un tableau croisé. 
  
2. Appelez la fonction [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) pour convertir les résultats en une trame de données qui peut facilement être utilisée dans l’une des fonctions de traçage standard de R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    La fonction **rxCube** comprend un argument facultatif, *returnDataFrame* = **true**, que vous pouvez utiliser pour convertir les résultats en une trame de données directement. Exemple :
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Toutefois, la sortie de **rxResultsDF** est plus propre et préserve les noms des colonnes sources. Vous pouvez exécuter `head(cube1)` `head(cubePlot)` suivi de pour comparer la sortie.
  
3. Créez une carte thermique à l’aide de la fonction **levelplot** du package de **treillis** , incluse dans toutes les distributions de R.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Résultats**
  
    ![Résultats du nuage de points](media/rsql-sue-scatterplotresults.jpg "Résultats de nuage de points")
  
À partir de cette analyse rapide, vous pouvez constater que le risque de fraude augmente avec le nombre de transactions et le nombre de transactions internationales.

Pour plus d’informations sur la fonction **rxCube** et analyses croisées en général, consultez synthèses de [données à l’aide de RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer des modèles R à l’aide de données SQL Server](../../advanced-analytics/tutorials/deepdive-create-models.md)