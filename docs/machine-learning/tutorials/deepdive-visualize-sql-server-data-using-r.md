---
title: Visualiser des données à l’aide de RevoScaleR
description: 'Tutoriel RevoScaleR 6 : Comment visualiser des données à l’aide du langage R sur SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4cc97db70461797e2e37614ae33d23ed51b21147
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116722"
---
#  <a name="visualize-sql-server-data-using-r-sql-server-and-revoscaler-tutorial"></a>Visualiser des données SQL Server à l’aide de R (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Il s’agit du tutoriel 6 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans ce tutoriel, vous allez utiliser les fonctions de R pour afficher la distribution des valeurs dans la colonne *creditLine* par sexe.

> [!div class="checklist"]
> * Créer des variables min-max pour les entrées d’histogramme
> * Représenter des données dans un histogramme à l’aide de **rxHistogram** à partir de **RevoScaleR**
> * Créer une visualisation avec des nuages de points à l’aide de la fonction **levelplot** de **lattice** inclus dans la distribution R de base

Comme ce tutoriel le montre, vous pouvez associer des fonctions Microsoft et open source dans le même script.

## <a name="add-maximum-and-minimum-values"></a>Ajouter des valeurs maximales et minimales

D’après les statistiques de synthèse calculées dans le tutoriel précédent, vous avez trouvé des informations utiles sur les données que vous pouvez placer dans la source de données pour effectuer d’autres calculs. Par exemple, les valeurs minimales et maximales peuvent être utilisées pour créer des histogrammes. Dans cet exercice, ajoutez les valeurs haute et basse de la source de données **RxSqlServerData**.

1. Commencez par configurer des variables temporaires.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Utilisez la variable *ccColInfo* créée dans le tutoriel précédent pour définir les colonnes de la source de données.
  
   Ajoutez de nouvelles colonnes calculées (*numTrans*, *numIntlTrans*et *creditLine*) à la collection de colonnes qui remplacent la définition d’origine. Le script ci-dessous ajoute des facteurs basés sur les valeurs minimales et maximales, obtenus à partir de sumOut, qui stocke la sortie en mémoire de **rxSummary**. 
  
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
  
3. Après avoir mis à jour la collection de colonnes, appliquez l’instruction suivante pour créer une version mise à jour de la source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] déjà définie.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    La source de données sqlFraudDS inclut désormais les nouvelles colonnes ajoutées à l’aide de *ccColInfo*.
  
À ce stade, les modifications affectent uniquement l’objet de source de données dans R. Aucune nouvelle donnée n’a encore été écrite dans la table de base de données. Toutefois, vous pouvez utiliser les données capturées dans la variable sumOut pour créer des visualisations et des synthèses. 

> [!TIP]
> Si vous avez oublié le contexte de calcul que vous utilisez, exécutez **rxGetComputeContext()** . Une valeur renvoyée « RxLocalSeq Compute Context » indique que l’exécution a lieu dans le contexte de calcul local.

## <a name="visualize-data-using-rxhistogram"></a>Visualiser des données à l’aide de rxHistogram

1. Le code R suivant permet d’appeler la fonction [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) et de passer une formule et une source de données. Le code peut être exécuté localement dans un premier temps, afin de voir les résultats attendus et combien de temps peut durer son exécution.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    En interne, **rxHistogram** appelle la fonction [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) , qui est incluse dans le package **RevoScaleR** . **rxCube** génère une liste unique (ou trame de données) qui contient une colonne pour chaque variable spécifiée dans la formule, plus une colonne de nombres.
    
2. À présent, définissez le contexte de calcul sur l’ordinateur SQL Server distant, puis réexécutez **rxHistogram**.
  
    ```R
    rxSetComputeContext(sqlCompute)
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
3. Les résultats sont exactement les mêmes, puisque vous utilisez la même source de données. Cependant, dans la deuxième étape, les calculs sont effectués sur l’ordinateur distant. Les résultats sont ensuite renvoyés à votre station de travail locale à des fins de traçage.
   
  ![résultats de l’histogramme](media/rsql-sue-histogramresults.jpg "résultats de l’histogramme")


## <a name="visualize-with-scatter-plots"></a>Créer une visualisation avec des nuages de points

Les nuages de points sont souvent utilisés lors de l’exploration des données pour comparer la relation entre deux variables. Vous pouvez utiliser des packages R intégrés avec les entrées fournies par les fonctions **RevoScaleR**.

1. Appelez la fonction [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) pour calculer la moyenne de *fraudRisk* pour chaque combinaison de *numTrans* et *numIntlTrans* :
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Pour spécifier les groupes utilisés pour calculer les moyennes de groupe, utilisez la notation `F()` . Dans cet exemple, `F(numTrans):F(numIntlTrans)` indique que les entiers dans les variables `numTrans` et `numIntlTrans` doivent être traités comme des variables catégorielles, avec un niveau pour chaque valeur d’entier.
  
    La valeur renvoyée par défaut de **rxCube** est un *objet rxCube*qui représente un tableau croisé. 
  
2. Appelez la fonction [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) pour convertir les résultats en une trame de données facilement exploitable dans l’une des fonctions de traçage standard de R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    La fonction **rxCube** inclut un argument facultatif, *returnDataFrame* = **TRUE**, que vous pouvez utiliser pour convertir les résultats en une trame de données directement. Par exemple :
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Toutefois, la sortie de **rxResultsDF** est plus propre et préserve le nom des colonnes sources. Vous pouvez exécuter `head(cube1)` suivi par `head(cubePlot)` pour comparer la sortie.
  
3. Créez une carte thermique en utilisant la fonction **levelplot** du package **lattice** inclus dans toutes les distributions de R.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Résultats**
  
    ![résultats de nuage de points](media/rsql-sue-scatterplotresults.jpg "résultats du nuage de points")
  
À partir de cette analyse rapide, vous pouvez voir que le risque de fraude augmente avec le nombre de transactions et le nombre de transactions internationales.

Pour plus d’informations sur la fonction **rxCube** et sur les analyses croisées en général, consultez [How to summarize data using RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries) (Comment synthétiser des données à l’aide de RevoScaleR).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer des modèles R à l’aide de données SQL Server](../../machine-learning/tutorials/deepdive-create-models.md)