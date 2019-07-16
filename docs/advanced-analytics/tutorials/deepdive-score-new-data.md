---
title: Noter les nouvelles données à l’aide de RevoScaleR et rxPredict - SQL Server Machine Learning
description: Didacticiel pas à pas sur la façon d’évaluer les données à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 386daeb62262182d40ea0b15cca3eb9714c23d64
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962197"
---
# <a name="score-new-data-sql-server-and-revoscaler-tutorial"></a>Noter les nouvelles données (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie de la [RevoScaleR didacticiel](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette étape, vous utilisez le modèle de régression logistique que vous avez créé dans la leçon précédente pour la notation d’un autre jeu de données qui utilise les mêmes variables indépendantes en tant qu’entrées.

> [!div class="checklist"]
> * Affecter un score à de nouvelles données
> * Créer un histogramme des scores

> [!NOTE]
> Vous avez besoin de privilèges d’administrateur DDL pour certaines de ces étapes.

## <a name="generate-and-save-scores"></a>Générer et enregistrer des scores
  
1. Mettre à jour la source de données sqlScoreDS (créé dans [leçon deux](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)) à utiliser les informations sur les colonnes créées dans la leçon précédente.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Pour vous assurer de que ne pas perdre les résultats, créez un nouvel objet de source de données. Ensuite, utilisez le nouvel objet de source de données pour remplir une nouvelle table dans la base de données RevoDeepDive.
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    À ce stade, la table n’a pas encore été créée. Cette instruction définit simplement un conteneur pour les données.
     
3. Vérifiez le contexte de calcul actuel à l’aide **rxGetComputeContext()** et définissez le contexte de calcul sur le serveur si nécessaire.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Par précaution, vérifier l’existence de la table de sortie. S’il en existe déjà avec le même nom, vous obtiendrez une erreur lorsque vous tentez d’écrire la nouvelle table.
  
    Pour ce faire, appelez les fonctions [rxSqlServerTableExists](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) et [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable), en passant le nom de la table en tant qu’entrée.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    + **rxSqlServerTableExists** interroge le pilote ODBC et retourne TRUE si la table existe, FALSE sinon.
    + **rxSqlServerDropTable** exécute l’instruction DDL et retourne la valeur TRUE si la table a été correctement supprimée, FALSE dans le cas contraire.

5. Exécutez [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) pour créer les scores et les enregistrer dans la nouvelle table définie dans sqlScoreDS de source de données.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    La fonction **rxPredict** est une autre fonction qui peut être exécutée dans les contextes de calcul distants. Vous pouvez utiliser la **rxPredict** (fonction) pour créer des scores à partir de modèles selon [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit), ou [rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm).
  
    - Le paramètre *writeModelVars* a ici la valeur **TRUE** . Cela signifie que les variables qui ont été utilisées pour l’estimation figureront dans la nouvelle table.
  
    - Le paramètre *predVarNames* spécifie la variable où les résultats seront stockés. Ici, vous passez une nouvelle variable, `ccFraudLogitScore`.
  
    - Le paramètre *type* de **rxPredict** définit la manière dont les prédictions sont calculées. Spécifiez le mot clé **réponse** pour générer des scores basés sur l’échelle de la variable de réponse. Ou, utilisez le mot clé **lien** pour générer des scores basés sur la fonction de liaison sous-jacente, auquel cas les prédictions sont créées à l’aide d’une échelle logistique.

6. Après un certain temps, vous pouvez actualiser la liste de tables dans Management Studio pour voir la nouvelle table et ses données.

7. Pour ajouter des variables supplémentaires aux prédictions de sortie, utilisez l’argument *extraVarsToWrite*.  Par exemple, dans le code suivant, la variable *custID* de la table de données de scores est ajoutée à la table de sortie de prédictions.
  
    ```R
    rxPredict(modelObject = logitObj,
            data = sqlScoreDS,
            outData = sqlServerOutDS,
            predVarNames = "ccFraudLogitScore",
              type = "link",
            writeModelVars = TRUE,
            extraVarsToWrite = "custID",
            overwrite = TRUE)
    ```

## <a name="display-scores-in-a-histogram"></a>Affichage des scores dans un histogramme

Une fois que la nouvelle table a été créée, calculer et afficher un histogramme des 10 000 scores prédits. Calcul est plus rapide si vous spécifiez les valeurs minimale et maximale, donc les obtenez à partir de la base de données et les ajoutez à vos données de travail.

1. Créer une nouvelle source de données, sqlMinMax, qui interroge la base de données pour obtenir les valeurs supérieure et inférieure.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     Dans cet exemple, vous allez voir combien il est facile d’utiliser les objets de source de données **RxSqlServerData** pour définir des datasets arbitraires basés sur des fonctions ou des requêtes SQL, ou des procédures stockées, puis de les utiliser dans votre code R. La variable ne stocke pas les valeurs réelles, mais seulement la définition de la source de données. La requête est exécutée pour générer les valeurs uniquement lorsque vous l’utilisez dans une fonction comme **rxImport**.
      
2. Appelez le [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) (fonction) pour placer les valeurs dans une trame de données qui peut être partagée entre plusieurs contextes de calcul.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals <- as.vector(unlist(minMaxVals))
    ```

    **Résultats**
     
    ```R
    > minMaxVals
     
    [1] -23.970256   9.786345
    ```

3. Maintenant que les valeurs minimales et maximales sont disponibles, utilisez les valeurs pour créer une autre source de données pour les scores générés.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Utilisez le sqlOutScoreDS d’objet de source de données pour obtenir les scores, calculer et afficher un histogramme. Ajoutez le code pour définir le contexte de calcul, si nécessaire.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Résultats**
  
    ![Histogramme complexe créé par R](media/rsql-sue-complex-histogram.png "Histogramme complexe créé par R")
  
## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Transformer des données à l’aide de R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)