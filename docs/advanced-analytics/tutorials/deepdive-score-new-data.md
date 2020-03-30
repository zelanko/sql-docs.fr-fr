---
title: Scorer des données à l’aide de RevoScaleR
description: 'Tutoriel RevoScaleR 8 : Comment évaluer des données à l’aide du langage R sur SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 26f5c7b56298e6a3bd5f1fa9d8bc1d4db79d60af
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "74947188"
---
# <a name="score-new-data-sql-server-and-revoscaler-tutorial"></a>Scorer des nouvelles données (tutoriel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Il s’agit du tutoriel 8 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans ce tutoriel, vous allez utiliser le modèle de régression logistique que vous avez créé lors du tutoriel précédent pour évaluer un autre jeu de données qui utilise les mêmes variables indépendantes sous forme d’entrées.

> [!div class="checklist"]
> * Affecter un score à de nouvelles données
> * Créer un histogramme des scores

> [!NOTE]
> Vous avez besoin de privilèges d’administrateur DDL pour certaines de ces étapes.

## <a name="generate-and-save-scores"></a>Générer et enregistrer des scores
  
1. Mettez à jour la source de données sqlScoreDS (créée dans le [tutoriel deux](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)) pour utiliser les informations de colonne créées à la leçon précédente.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Pour éviter de perdre les résultats, créez un objet de source de données. Utilisez ensuite le nouvel objet de source de données pour remplir une nouvelle table dans la base de données RevoDeepDive.
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    À ce stade, la table n’a pas encore été créée. Cette instruction définit simplement un conteneur pour les données.
     
3. Vérifiez le contexte de calcul actuel à l’aide de **rxGetComputeContext()** , puis définissez-le sur le serveur si nécessaire.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Par précaution, vérifiez que la table de sortie existe. S’il en existe déjà une de même nom, vous obtiendrez une erreur pendant la tentative d’écriture de la nouvelle table.
  
    Pour ce faire, appelez les fonctions [rxSqlServerTableExists](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) et [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable), en passant le nom de la table en tant qu’entrée.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    + **rxSqlServerTableExists** interroge le pilote ODBC et retourne TRUE si la table existe, FALSE dans le cas contraire.
    + **rxSqlServerDropTable** exécute l’instruction DDL et retourne TRUE si la table a été correctement supprimée, FALSE dans le cas contraire.

5. Exécutez [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) pour créer les scores, puis enregistrez-les dans la nouvelle table définie dans la source de données sqlScoreDS.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    La fonction **rxPredict** est une autre fonction qui peut être exécutée dans les contextes de calcul distants. Vous pouvez utiliser la fonction **rxPredict** pour créer des scores à partir de modèles basés sur [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) ou [rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm).
  
    - Le paramètre *writeModelVars* a ici la valeur **TRUE** . Cela signifie que les variables qui ont été utilisées pour l’estimation figureront dans la nouvelle table.
  
    - Le paramètre *predVarNames* spécifie la variable où les résultats seront stockés. Ici, vous transmettez une nouvelle variable, `ccFraudLogitScore`.
  
    - Le paramètre *type* de **rxPredict** définit la manière dont les prédictions sont calculées. Spécifiez le mot clé **response** pour générer des scores en fonction de l’échelle de la variable de réponse. Sinon, utilisez le mot clé **link** pour générer des scores basés sur la fonction de liaison sous-jacente. Dans ce cas, les prédictions sont créées en utilisant une échelle logistique.

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

Après avoir créé la table, calculez et affichez un histogramme des 10 000 scores prédits. Le calcul étant plus rapide si vous spécifiez les valeurs minimale et maximale, procurez-vous-les dans la base de données et ajoutez-les à vos données de travail.

1. Créez une source de données, sqlMinMax, qui interroge la base de données pour se procurer les valeurs minimale et maximale.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     Dans cet exemple, vous allez voir combien il est facile d’utiliser les objets de source de données **RxSqlServerData** pour définir des datasets arbitraires basés sur des fonctions ou des requêtes SQL, ou des procédures stockées, puis de les utiliser dans votre code R. La variable ne stocke pas les valeurs réelles, mais seulement la définition de la source de données. La requête est exécutée pour générer les valeurs uniquement lorsque vous l’utilisez dans une fonction comme **rxImport**.
      
2. Appelez la fonction [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) pour placer les valeurs dans une trame de données qui peut être partagée entre plusieurs contextes de calcul.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals <- as.vector(unlist(minMaxVals))
    ```

    **Résultats**
     
    ```R
    > minMaxVals
     
    [1] -23.970256   9.786345
    ```

3. Maintenant que les valeurs minimale et maximale sont disponibles, utilisez-les pour créer une autre source de données pour les scores générés.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Utilisez l’objet de source de données sqlOutScoreDS pour obtenir les scores, puis calculez et affichez un histogramme. Ajoutez le code pour définir le contexte de calcul, si nécessaire.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Résultats**
  
    ![histogramme complexe créé par R](media/rsql-sue-complex-histogram.png "histogramme complexe créé par R")
  
## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Transformer des données à l’aide de R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)