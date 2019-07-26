---
title: Noter les nouvelles données à l’aide de RevoScaleR et rxPredict
description: Didacticiel procédure pas à pas sur la façon de noter les données à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 8d38f2183078ee87fdb53e6333ecd13e85f3c65e
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469668"
---
# <a name="score-new-data-sql-server-and-revoscaler-tutorial"></a>Noter les nouvelles données (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Au cours de cette étape, vous allez utiliser le modèle de régression logistique que vous avez créé dans la leçon précédente pour noter un autre jeu de données qui utilise les mêmes variables indépendantes que les entrées.

> [!div class="checklist"]
> * Affecter un score à de nouvelles données
> * Créer un histogramme des scores

> [!NOTE]
> Vous avez besoin de privilèges d’administrateur DDL pour certaines de ces étapes.

## <a name="generate-and-save-scores"></a>Générer et enregistrer des scores
  
1. Mettez à jour la source de données sqlScoreDS (créée dans la [leçon 2](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)) pour utiliser les informations de colonne créées dans la leçon précédente.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Pour être sûr de ne pas perdre les résultats, créez un objet de source de données. Utilisez ensuite le nouvel objet source de données pour remplir une nouvelle table dans la base de données RevoDeepDive.
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    À ce stade, la table n’a pas encore été créée. Cette instruction définit simplement un conteneur pour les données.
     
3. Vérifiez le contexte de calcul actuel à l’aide de **rxGetComputeContext ()** et définissez le contexte de calcul sur le serveur si nécessaire.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Par précaution, vérifiez l’existence de la table de sortie. S’il en existe déjà un portant le même nom, vous obtiendrez une erreur lors de la tentative d’écriture de la nouvelle table.
  
    Pour ce faire, appelez les fonctions [rxSqlServerTableExists](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) et [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable), en passant le nom de la table en tant qu’entrée.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    + **rxSqlServerTableExists** interroge le pilote ODBC et retourne true si la table existe; sinon, false.
    + **rxSqlServerDropTable** exécute le DDL et retourne true si la table a été supprimée avec succès; sinon, false.

5. Exécutez [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) pour créer les scores et enregistrez-les dans la nouvelle table définie dans la source de données sqlScoreDS.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    La fonction **rxPredict** est une autre fonction qui peut être exécutée dans les contextes de calcul distants. Vous pouvez utiliser la fonction **rxPredict** pour créer des scores à partir de modèles basés sur [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)ou [rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm).
  
    - Le paramètre *writeModelVars* a ici la valeur **TRUE** . Cela signifie que les variables qui ont été utilisées pour l’estimation figureront dans la nouvelle table.
  
    - Le paramètre *predVarNames* spécifie la variable où les résultats seront stockés. Ici, vous passez une nouvelle variable, `ccFraudLogitScore`.
  
    - Le paramètre *type* de **rxPredict** définit la manière dont les prédictions sont calculées. Spécifiez la **réponse** du mot clé pour générer des scores en fonction de l’échelle de la variable de réponse. Vous pouvez utiliser le **lien** de mot clé pour générer des scores basés sur la fonction de liaison sous-jacente, auquel cas des prédictions sont créées à l’aide d’une échelle logistique.

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

## <a name="display-scores-in-a-histogram"></a>Afficher les scores dans un histogramme

Une fois la nouvelle table créée, calculez et affichez un histogramme des scores prévisibles de 10 000. Le calcul est plus rapide si vous spécifiez des valeurs basses et élevées, récupérez-les à partir de la base de données et ajoutez-les à vos données de travail.

1. Créez une nouvelle source de données, sqlMinMax, qui interroge la base de données pour obtenir les valeurs basses et élevées.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     Dans cet exemple, vous allez voir combien il est facile d’utiliser les objets de source de données **RxSqlServerData** pour définir des datasets arbitraires basés sur des fonctions ou des requêtes SQL, ou des procédures stockées, puis de les utiliser dans votre code R. La variable ne stocke pas les valeurs réelles, mais seulement la définition de la source de données. La requête est exécutée pour générer les valeurs uniquement lorsque vous l’utilisez dans une fonction comme **rxImport**.
      
2. Appelez la fonction [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) pour placer les valeurs dans une trame de données qui peut être partagée entre des contextes de calcul.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals <- as.vector(unlist(minMaxVals))
    ```

    **Résultats**
     
    ```R
    > minMaxVals
     
    [1] -23.970256   9.786345
    ```

3. Maintenant que les valeurs maximale et minimale sont disponibles, utilisez les valeurs pour créer une autre source de données pour les scores générés.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Utilisez l’objet de source de données sqlOutScoreDS pour obtenir les scores et calculer et afficher un histogramme. Ajoutez le code pour définir le contexte de calcul, si nécessaire.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Résultats**
  
    ![Histogramme complexe créé par R](media/rsql-sue-complex-histogram.png "Histogramme complexe créé par R")
  
## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Transformer des données à l’aide de R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)