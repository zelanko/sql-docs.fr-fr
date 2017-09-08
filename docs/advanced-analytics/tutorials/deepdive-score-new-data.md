---
title: "Un score de nouvelles données | Documents Microsoft"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 87056467-f67f-4d72-a83c-ac052736d85d
caps.latest.revision: 17
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70c63f62647ce614e83414dbf923ba9bc4cc2c29
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="score-new-data"></a>Affecter un score à de nouvelles données

Maintenant que vous avez un modèle utilisable pour les prédictions, vous allez lui injecter des données à partir de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour générer des prédictions.

Dans cette section, vous allez utiliser le modèle de régression logistique *logitObj*pour créer des scores pour un autre dataset qui utilise les mêmes variables indépendantes en tant qu’entrées.

> [!NOTE]
> Vous aurez besoin de privilèges d’administrateur DDL pour certaines de ces étapes.

## <a name="generate-and-save-scores"></a>Générez et enregistrez des Scores
  
1. Mettez à jour la source de données que vous avez déjà configurée ( *sqlScoreDS*) pour ajouter les informations de colonnes nécessaires.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Pour être sûr de ne pas perdre les résultats, vous allez créer un objet de source de données et l’utiliser pour remplir une nouvelle table dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
     À ce stade, la table n’a pas encore été créée. Cette instruction définit simplement un conteneur pour les données.
     
3. Vérifiez le contexte de calcul actuel et définissez-le sur le serveur si nécessaire.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Avant d’exécuter la fonction de prédiction qui génère les résultats, vous devez vérifier l’existence d’une table de sortie. Dans le cas contraire, vous obtenez une erreur lorsque vous avez tenté d’écrire la nouvelle table.
  
    Pour ce faire, appelez les fonctions **rxSqlServerTableExists** et **rxSqlServerDropTable**, en passant le nom de la table en tant qu’entrée.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    -  La fonction rxSqlServerTableExists interroge le pilote ODBC et retourne la valeur TRUE si la table existe, FALSE dans le cas contraire.
    -  La fonction rxSqlServerDropTable fonction exécute l’instruction DDL et retourne TRUE si la table est correctement supprimée, FALSE dans le cas contraire.
  
5. Vous êtes maintenant prêt à utiliser la fonction **rxPredict** pour créer les scores et les enregistrer dans la nouvelle table définie dans la source de données *sqlScoreDS*.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    La fonction rxPredict est une autre fonction qui prend en charge l’exécution dans des contextes de calcul à distance. Vous pouvez utiliser la fonction rxPredict pour créer des scores à partir de modèles créés à l’aide de rxLinMod, rxLogit ou rxGlm.
  
    - Le paramètre *writeModelVars* a ici la valeur **TRUE** . Cela signifie que les variables qui ont été utilisées pour l’estimation figureront dans la nouvelle table.
  
    - Le paramètre *predVarNames* spécifie la variable où les résultats seront stockés. Ici, vous passez une nouvelle variable nommée *ccFraudLogitScore*.
  
    - Le *type* paramètre rxPredict définit comment vous souhaitez que les prédictions calculées. Spécifiez le mot clé **response** pour générer des scores basés sur l’échelle de la variable de réponse, ou utilisez le mot clé **link** pour générer des scores basés sur la fonction de liaison sous-jacente, auquel cas les prédictions seront sur une échelle logistique.

6. Après un certain temps, vous pouvez actualiser la liste de tables dans Management Studio pour voir la nouvelle table et ses données.

7. Pour ajouter des variables supplémentaires aux prédictions de sortie, vous pouvez utiliser l’argument *extraVarsToWrite* .  Par exemple, dans le code suivant, la variable *custID* de la table de données de scores est ajoutée à la table de sortie de prédictions.
  
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

Après avoir créé la table, vous allez calculer et afficher un histogramme des 10 000 scores prédits. Les calculs seront plus rapides si vous spécifiez les valeurs minimale et maximale. Vous allez donc les obtenir à partir de la base de données et les ajouter à vos données de travail.

1. Créez une source de données nommée *sqlMinMax*qui interroge la base de données pour obtenir les valeurs minimale et maximale.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     Dans cet exemple, vous pouvez voir combien il est facile à utiliser les objets de source de données RxSqlServerData pour définir des jeux de données arbitraires basée sur des procédures stockées, des fonctions ou des requêtes SQL et puis les utiliser dans votre code R. La variable ne stocke pas les valeurs réelles, uniquement la définition de source de données ; la requête est exécutée pour générer les valeurs uniquement lorsque vous l’utilisez dans une fonction comme rxImport.
      
2. Appelez la fonction rxImport pour placer les valeurs dans une trame de données qui peut être partagée entre plusieurs contextes de calcul.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals \<- as.vector(unlist(minMaxVals))
  
    ```
     **Résultats**
     
     *> minMaxVals*
     
     *[1] -23.970256   9.786345*
  
3. Maintenant que les valeurs minimale et maximales sont disponibles, utilisez les valeurs pour créer la source de données de score.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Enfin, utilisez l’objet de source de données de scores pour obtenir les données de scores en vue de calculer et afficher un histogramme. Ajoutez le code pour définir le contexte de calcul, si nécessaire.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Résultats**
  
    ![Histogramme complexe créé par R](media/rsql-sue-complex-histogram.png "Histogramme complexe créé par R")
  
## <a name="next-step"></a>Étape suivante

[Transformer des données à l’aide de R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="previous-step"></a>Étape précédente

[Créer des modèles](../../advanced-analytics/tutorials/deepdive-create-models.md)



