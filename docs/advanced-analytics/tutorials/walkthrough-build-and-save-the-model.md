---
title: Créer un modèle R et l’enregistrer dans SQL Server (procédure pas à pas)
description: Didacticiel expliquant comment créer un modèle de langage R utilisé pour SQL Server analytique dans la base de données.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: eec6d165b8e3aa4130246aae6d4aaf5b4102fc0f
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345824"
---
# <a name="build-an-r-model-and-save-to-sql-server-walkthrough"></a>Créer un modèle R et l’enregistrer dans SQL Server (procédure pas à pas)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans cette étape, vous allez apprendre à créer un modèle de Machine Learning et à enregistrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]le modèle dans. En enregistrant un modèle, vous pouvez l’appeler directement [!INCLUDE[tsql](../../includes/tsql-md.md)] à partir du code, à l’aide de la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ou de la [fonction Predict (T-SQL)](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql).

## <a name="prerequisites"></a>Prérequis

Cette étape suppose une session R en cours basée sur les étapes précédentes de cette procédure pas à pas. Elle utilise les chaînes de connexion et les objets de source de données créés dans ces étapes. Les outils et les packages suivants sont utilisés pour exécuter le script.

+ RGUI. exe pour exécuter des commandes R
+ Management Studio pour exécuter T-SQL
+ Package ROCR
+ Package RODBC

### <a name="create-a-stored-procedure-to-save-models"></a>Créer une procédure stockée pour enregistrer des modèles

Cette étape utilise une procédure stockée pour enregistrer un modèle formé dans SQL Server. La création d’une procédure stockée pour effectuer cette opération facilite la tâche.

Exécutez le code T-SQL suivant dans une fenêtre de requête de Management Studio pour créer la procédure stockée.

```sql
USE [NYCTaxi_Sample]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PersistModel')
  DROP PROCEDURE PersistModel
GO

CREATE PROCEDURE [dbo].[PersistModel] @m nvarchar(max)
AS
BEGIN
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements.
    SET NOCOUNT ON;
    insert into nyc_taxi_models (model) values (convert(varbinary(max),@m,2))
END
GO
```

> [!NOTE]
> Si vous recevez une erreur, assurez-vous que votre connexion a l’autorisation de créer des objets. Vous pouvez accorder des autorisations explicites pour créer des objets en exécutant une instruction T-SQL `exec sp_addrolemember 'db_owner', '<user_name>'`comme suit:.

## <a name="create-a-classification-model-using-rxlogit"></a>Créer un modèle de classification à l’aide de rxLogit

Le modèle est un classifieur binaire qui prédit si le pilote de taxi est susceptible d’obtenir un pourboire sur une touche particulière. Vous allez utiliser la source de données que vous avez créée dans la leçon précédente pour former le classifieur de pourboires à l’aide de la régression logistique.

1. Appelez la fonction [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) , comprise dans le package **RevoScaleR** , pour créer un modèle de régression logistique. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource));
    ```

    L’appel qui génère le modèle est placé dans la fonction system.time. Cela vous donne le temps de générer le modèle.

2. Après avoir généré le modèle, vous pouvez l’inspecter à `summary` l’aide de la fonction et afficher les coefficients.

    ```R
    summary(logitObj);
    ```

    **Résultats**
    
    ```R
     *Logistic Regression Results for: tipped ~ passenger_count + trip_distance + trip_time_in_secs +*
     direct_distance* 
     *Data: featureDataSource (RxSqlServerData Data Source)*
     *Dependent variable(s): tipped*
     *Total independent variables: 5*
     *Number of valid observations: 17068*
     *Number of missing observations: 0*
     *-2\*LogLikelihood: 23540.0602 (Residual deviance on 17063 degrees of freedom)*
     *Coefficients:*
     *Estimate Std. Error z value Pr(>|z|)*
     *(Intercept)       -2.509e-03  3.223e-02  -0.078  0.93793*
     *passenger_count   -5.753e-02  1.088e-02  -5.289 1.23e-07 \*\*\**
     *trip_distance     -3.896e-02  1.466e-02  -2.658  0.00786 \*\**
     *trip_time_in_secs  2.115e-04  4.336e-05   4.878 1.07e-06 \*\*\**
     *direct_distance    6.156e-02  2.076e-02   2.966  0.00302 \*\**
     *---*
     *Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1*
     *Condition number of final variance-covariance matrix: 48.3933*
     *Number of iterations: 4*
   ```

## <a name="use-the-logistic-regression-model-for-scoring"></a>Utiliser le modèle de régression logistique pour calculer les scores

Maintenant que le modèle est créé, vous pouvez l’utiliser pour évaluer la probabilité que le conducteur obtienne un pourboire lors d’un trajet donné.

1. Tout d’abord, utilisez la fonction [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) pour définir un objet de source de données pour le stockage du résultat de notation.

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Pour simplifier cet exemple, l’entrée du modèle de régression logistique est la même source de données de fonctionnalité (`sql_feature_ds`) que celle utilisée pour l’apprentissage du modèle.  Plus généralement, vous aurez sans doute de nouvelles données avec lesquelles calculer les scores, ou vous aurez peut-être mis de côté certaines données de test et de formation.
  
    + Les résultats de prédiction sont enregistrés dans la table _taxiscoreOutput_. Notez que le schéma de cette table n’est pas défini lorsque vous le créez à l’aide de rxSqlServerData. Le schéma est obtenu à partir de la sortie rxPredict.
  
    + Pour créer la table qui stocke les valeurs prédites, la connexion SQL qui exécute la fonction de données rxSqlServer doit avoir des privilèges DDL dans la base de données. Si la connexion ne peut pas créer de tables, l’instruction échoue.

2. Appelez la fonction [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) pour générer les résultats.

    ```R
    rxPredict(modelObject = logitObj,
        data = featureDataSource,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Si l’instruction est réussie, son exécution doit prendre un certain temps. Lorsque vous avez terminé, vous pouvez ouvrir SQL Server Management Studio et vérifier que la table a été créée et qu’elle contient la colonne score et une autre sortie attendue.

## <a name="plot-model-accuracy"></a>Précision du modèle de tracé

Pour avoir une idée de la précision du modèle, vous pouvez utiliser la fonction [rxRoc](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc) pour tracer la courbe de fonctionnement du récepteur. Étant donné que rxRoc est l’une des nouvelles fonctions fournies par le package RevoScaleR qui prend en charge les contextes de calcul distants, vous avez deux options:

+ Vous pouvez utiliser la fonction rxRoc pour exécuter le tracé dans le contexte de calcul distant, puis retourner le tracé à votre client local.

+ Vous pouvez également importer les données sur votre ordinateur client R et utiliser d’autres fonctions de traçage R pour créer le graphique de performances.

Dans cette section, vous allez expérimenter les deux techniques.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Exécuter un tracé dans le contexte de calcul distant (SQL Server)

1. Appelez la fonction rxRoc et fournissez les données définies précédemment en tant qu’entrée.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    Cet appel retourne les valeurs utilisées pour calculer le graphique ROC. La colonne d’étiquette _est_dépassée, ce qui a les résultats que vous essayez de prédire, tandis que la colonne _score_ contient la prédiction.

2. Pour tracer le graphique, vous pouvez enregistrer l’objet ROC, puis le dessiner avec la fonction plot. Le graphique est créé dans le contexte de calcul distant, puis retourné à votre environnement R.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Affichez le graphique en ouvrant le périphérique graphique R ou en cliquant sur  la fenêtre de tracés dans RStudio.

    ![Tracé ROC pour le modèle](media/rsql-e2e-rocplot.png "Tracé ROC pour le modèle")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Créer les tracés dans le contexte de calcul local à l’aide de données de SQL Server

Vous pouvez vérifier que le contexte de calcul est local en `rxGetComputeContext()` exécutant à l’invite de commandes. La valeur de retour doit être «RxLocalSeq Compute Context».

1. Pour le contexte de calcul local, le processus est très similaire. Vous utilisez la fonction [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) pour importer les données spécifiées dans votre environnement R local.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. À l’aide des données de la mémoire locale, vous chargez le package **ROCR** et utilisez la fonction de prédiction de ce package pour créer des prédictions.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. Générez un tracé local en fonction des valeurs stockées dans la variable `pred`de sortie.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![Traçage des performances d’un modèle à l’aide de R](media/rsql-e2e-performanceplot.png "Traçage des performances d’un modèle à l’aide de R")

> [!NOTE]
> Selon le nombre de points de données utilisés, les graphiques peuvent être différents.

## <a name="deploy-the-model"></a>Déployer le modèle

Une fois que vous avez créé un modèle et déterminé qu’il fonctionne correctement, vous souhaiterez probablement le déployer sur un site où les utilisateurs ou les personnes de votre organisation peuvent utiliser le modèle, ou peut-être reformer et reétalonner le modèle régulièrement. Ce processus est parfois appelé « *fonctionnement* d’un modèle». Dans SQL Server, la désintégration est obtenue en incorporant du code R dans une procédure stockée. Étant donné que le code réside dans la procédure, il peut être appelé à partir de n’importe quelle application capable de se connecter à SQL Server.

Avant de pouvoir appeler le modèle à partir d’une application externe, vous devez enregistrer le modèle dans la base de données utilisée pour la production. Les modèles formés sont stockés sous forme binaire, dans une seule colonne de type **varbinary (max)** .

Un flux de travail de déploiement classique comprend les étapes suivantes:

1. Sérialiser le modèle dans une chaîne hexadécimale
2. Transmettre l’objet sérialisé à la base de données
3. Enregistrer le modèle dans une colonne varbinary (max)

Dans cette section, vous allez apprendre à utiliser une procédure stockée pour rendre le modèle persistant et le rendre disponible pour les prédictions. La procédure stockée utilisée dans cette section est PersistModel. La définition de PersistModel est dans les [conditions préalables](#prerequisites).

1. Revenez à votre environnement R local si vous ne l’utilisez pas déjà, Sérialisez le modèle et enregistrez-le dans une variable.

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. Ouvrez une connexion ODBC à l’aide de **RODBC**. Vous pouvez omettre l’appel à RODBC si vous avez déjà chargé le package.

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

3. Appelez la procédure stockée PersistModel sur SQL Server pour transmettre l’objet sérialisé à la base de données et stocker la représentation binaire du modèle dans une colonne. 

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

4. Utilisez Management Studio pour vérifier que le modèle existe. Dans l’Explorateur d’objets, cliquez avec le bouton droit sur la table **nyc_taxi_models** , puis cliquez sur **Sélectionner les 1000 premières lignes**. Dans résultats, vous devez voir une représentation binaire dans la colonne **modèles** .

L’enregistrement d’un modèle dans une table nécessite uniquement une instruction INSERT. Toutefois, il est souvent plus facile de les inclure dans un wrapper dans une procédure stockée, par exemple *PersistModel*.

## <a name="next-steps"></a>Étapes suivantes

Dans la leçon suivante et finale, Découvrez comment effectuer des notations sur le modèle enregistré [!INCLUDE[tsql](../../includes/tsql-md.md)]à l’aide de.

> [!div class="nextstepaction"]
> [Déployer le modèle R et l’utiliser dans SQL](walkthrough-deploy-and-use-the-model.md)
