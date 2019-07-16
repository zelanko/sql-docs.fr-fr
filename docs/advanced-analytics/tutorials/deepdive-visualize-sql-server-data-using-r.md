---
title: Visualiser les données de SQL Server à l’aide de rxHistogram RevoScaleR - SQL Server Machine Learning
description: Didacticiel pas à pas sur la façon de visualiser des données à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 4092de07d19d4d33bd56025076e606269c2b04e8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962156"
---
#  <a name="visualize-sql-server-data-using-r-sql-server-and-revoscaler-tutorial"></a>Visualiser les données de SQL Server à l’aide de R (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie de la [RevoScaleR didacticiel](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette leçon, utiliser des fonctions R pour afficher la distribution des valeurs dans le *creditLine* colonne par sexe.

> [!div class="checklist"]
> * Créer des variables de min-max pour les entrées de l’histogramme
> * Visualiser les données dans un histogramme à l’aide **rxHistogram** de **RevoScaleR**
> * Visualiser des données avec des graphiques à nuages de points à l’aide de **levelplot** de **lattice** inclus dans la distribution R de base

Comme illustré dans cette leçon, vous pouvez combiner des fonctions spécifiques à Microsoft et open source dans le même script.

## <a name="add-maximum-and-minimum-values"></a>Ajouter des valeurs minimale et maximale

Selon les statistiques de synthèse calculées à partir de la leçon précédente, vous avez trouvé des informations utiles sur les données que vous pouvez insérer dans la source de données pour effectuer des calculs plus. Par exemple, les valeurs minimales et maximales peuvent être utilisés pour calculer des histogrammes. Dans cet exercice, ajoutez les valeurs haute et bas pour le **RxSqlServerData** source de données.

1. Commencez par configurer des variables temporaires.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Utilisez la variable *ccColInfo* que vous avez créé dans la leçon précédente pour définir les colonnes dans la source de données.
  
   Ajouter de nouvelles colonnes calculées (*numTrans*, *numIntlTrans*, et *creditLine*) à la collection de colonnes qui remplacent la définition d’origine. Le script ci-dessous ajoute des facteurs en fonction des valeurs minimales et maximales, obtenus à partir de sumOut, qui stocke la sortie en mémoire à partir de **rxSummary**. 
  
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
  
3. Ayant de mises à jour la collection de colonnes, s’appliquent à l’instruction suivante pour créer une version mise à jour de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données que vous avez défini précédemment.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    La source de données sqlFraudDS inclut désormais les nouvelles colonnes ajoutées à l’aide de *ccColInfo*.
  
À ce stade, les modifications affectent uniquement l’objet de source de données dans R ; Aucune nouvelle donnée n’a encore été écrit à la table de base de données. Toutefois, vous pouvez utiliser les données capturées dans la variable sumOut pour créer des visualisations et des synthèses. 

> [!TIP]
> Si vous oubliez quel contexte de calcul que vous utilisez, exécutez **rxGetComputeContext()** . Une valeur de retour de « Contexte de calcul RxLocalSeq » indique que vous sont en cours d’exécution dans le contexte de calcul local.

## <a name="visualize-data-using-rxhistogram"></a>Visualiser les données à l’aide de rxHistogram

1. Le code R suivant permet d’appeler la fonction [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) et de passer une formule et une source de données. Le code peut être exécuté localement dans un premier temps, afin de voir les résultats attendus et combien de temps peut durer son exécution.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    En interne, **rxHistogram** appelle la fonction [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) , qui est incluse dans le package **RevoScaleR** . **rxCube** génère une liste unique (ou trame de données) qui contient une colonne pour chaque variable spécifiée dans la formule, plus une colonne de nombres.
    
2. À présent, définissez le contexte de calcul sur l’ordinateur SQL Server distant et exécuter **rxHistogram** à nouveau.
  
    ```R
    rxSetComputeContext(sqlCompute)
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
3. Les résultats sont exactement les mêmes, car vous utilisez la même source de données, mais dans la deuxième étape, les calculs sont effectués sur le serveur distant. Les résultats sont ensuite renvoyés à votre station de travail locale à des fins de traçage.
   
  ![Résultats de l’histogramme](media/rsql-sue-histogramresults.jpg "Résultats de l’histogramme")


## <a name="visualize-with-scatter-plots"></a>Visualiser des données avec les nuages de points

Nuages de points sont souvent utilisés pendant l’exploration de données pour comparer la relation entre deux variables. Vous pouvez utiliser des packages R intégrés à cet effet, avec les entrées fournies par **RevoScaleR** fonctions.

1. Appelez le [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) fonction pour calculer la moyenne de *fraudRisk* pour chaque combinaison de *numTrans* et *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Pour spécifier les groupes utilisés pour calculer les moyennes de groupe, utilisez la notation `F()` . Dans cet exemple, `F(numTrans):F(numIntlTrans)` indique que les entiers dans les variables `numTrans` et `numIntlTrans` doivent être traités comme des variables catégorielles, avec un niveau pour chaque valeur d’entier.
  
    La valeur par défaut retourne la valeur de **rxCube** est un *objet rxCube*, qui représente un tableau croisé. 
  
2. Appelez [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) fonction pour convertir les résultats dans une trame de données qui peut facilement être utilisée dans une des fonctions de traçage standard de R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    Le **rxCube** fonction inclut un argument facultatif, *returnDataFrame* = **TRUE**, que vous pouvez utiliser pour convertir les résultats en une trame de données directement. Exemple :
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Toutefois, la sortie de **rxResultsDF** est plus propre et préserve les noms des colonnes sources. Vous pouvez exécuter `head(cube1)` suivie `head(cubePlot)` pour comparer la sortie.
  
3. Créer une carte thermique en utilisant le **levelplot** fonction à partir de la **lattice** package, inclus avec toutes les distributions de R.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Résultats**
  
    ![Résultats du nuage de points](media/rsql-sue-scatterplotresults.jpg "Résultats de nuage de points")
  
À partir de cette analyse rapide, vous pouvez voir que le risque de fraude augmente avec le nombre de transactions et le nombre de transactions internationales.

Pour plus d’informations sur la **rxCube** (fonction) et des analyses croisées en général, consultez [des résumés de données à l’aide de RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer des modèles R à l’aide de données SQL Server](../../advanced-analytics/tutorials/deepdive-create-models.md)