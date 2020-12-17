---
title: 'Didacticiel R : Créer et enregistrer le modèle'
description: Découvrez plus d’informations sur la création d’un modèle de Machine Learning en langage R utilisé pour l’analytique de base de données SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 1974c58ad2adbad3b7e136ffa36ffa88b5783fc6
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470050"
---
# <a name="build-an-r-model-and-save-to-sql-server-walkthrough"></a>Créer un modèle R et l’enregistrer dans SQL Server (procédure pas à pas)
[!INCLUDE [SQL Server 2016](../../includes/applies-to-version/sqlserver2016.md)]

Dans cette leçon, vous allez découvrir comment créer un modèle Machine Learning et enregistrer le modèle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En enregistrant un modèle, vous pouvez l’appeler directement à partir du code [!INCLUDE[tsql](../../includes/tsql-md.md)], à l’aide de la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ou de la [fonction PREDICT (T-SQL)](../../t-sql/queries/predict-transact-sql.md).

## <a name="prerequisites"></a>Prérequis

Cette étape suppose que vous utilisez une session R ouverte basée sur les étapes précédentes de cette procédure pas à pas. Elle utilise les chaînes de connexion et les objets de source de données créés dans ces étapes. Les outils et les packages suivants sont utilisés pour exécuter le script.

+ RGUI.exe pour exécuter des commandes R
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
> Si vous recevez une erreur, assurez-vous que votre compte de connexion a l’autorisation de créer des objets. Vous pouvez accorder des autorisations explicites pour créer des objets en exécutant une instruction T-SQL comme suit : `exec sp_addrolemember 'db_owner', '<user_name>'`.

## <a name="create-a-classification-model-using-rxlogit"></a>Créer un modèle de classification à l’aide de rxLogit

Le modèle est un classifieur binaire qui évalue la probabilité que le chauffeur de taxi obtienne un pourboire lors d’un trajet donné. Vous allez utiliser la source de données que vous avez créée dans la leçon précédente pour former le classifieur de pourboires, à l’aide de la régression logistique.

1. Appelez la fonction [rxLogit](/r-server/r-reference/revoscaler/rxlogit) , comprise dans le package **RevoScaleR** , pour créer un modèle de régression logistique. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource));
    ```

    L’appel qui génère le modèle est placé dans la fonction system.time. Cela vous donne le temps de générer le modèle.

2. Après avoir créé le modèle, vous pouvez l’examiner à l’aide de la fonction `summary` et afficher les coefficients.

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

1. Tout d’abord, utilisez la fonction [RxSqlServerData](/r-server/r-reference/revoscaler/rxsqlserverdata) pour définir un objet de source de données pour le stockage du résultat de scoring.

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Pour simplifier cet exemple, l’entrée du modèle de régression logistique est la même source de données de caractéristique (`sql_feature_ds`) que celle utilisée pour former le modèle.  Plus généralement, vous aurez sans doute de nouvelles données avec lesquelles calculer les scores, ou vous aurez peut-être mis de côté certaines données de test et de formation.
  
    + Les résultats de la prédiction sont enregistrés dans la table _taxiscoreOutput_. Notez que le schéma de cette table n’est pas défini lorsque vous le créez à l’aide de rxSqlServerData. Le schéma est obtenu à partir de la sortie rxPredict.
  
    + Pour créer la table qui stocke les valeurs prédites, le compte de connexion SQL qui exécute la fonction de données rxSqlServer doit disposer de privilèges DDL dans la base de données. Si le compte de connexion ne peut pas créer de table, l’instruction échoue.

2. Appelez la fonction [rxPredict](/r-server/r-reference/revoscaler/rxpredict) pour générer les résultats.

    ```R
    rxPredict(modelObject = logitObj,
        data = featureDataSource,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Si l’instruction réussit, son exécution doit prendre un certain temps. Lorsque vous avez terminé, vous pouvez ouvrir SQL Server Management Studio et vérifier que la table a été créée et qu’elle contient la colonne Score et l’autre sortie attendue.

## <a name="plot-model-accuracy"></a>Précision du modèle de tracé

Pour avoir une idée de la précision du modèle, vous pouvez utiliser la fonction [rxRoc](/r-server/r-reference/revoscaler/rxroc) pour tracer la courbe Receiver Operating Curve. Comme rxRoc est l’une des nouvelles fonctions fournies par le package RevoScaleR qui prend en charge les contextes de calcul distants, vous avez deux options :

+ Vous pouvez utiliser la fonction rxRoc pour exécuter le tracé dans le contexte de calcul distant, puis renvoyer le tracé à votre client local.

+ Vous pouvez également importer les données sur votre ordinateur client R et utiliser d’autres fonctions de traçage R pour créer le graphique de performances.

Dans cette section, vous allez tester les deux techniques.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Exécuter un tracé dans le contexte de calcul distant (SQL Server)

1. Appelez la fonction rxRocCurve et fournissez les données définies précédemment en tant qu’entrée.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    Cet appel renvoie les valeurs utilisées pour calculer le graphique ROC. La colonne d’étiquette est _tipped_ et contient les résultats que vous essayez de prédire, tandis que la colonne _Score_ contient la prédiction.

2. Pour tracer le graphique, vous pouvez enregistrer l’objet ROC, puis le dessiner avec la fonction de tracé. Le graphique est créé dans le contexte de calcul distant, puis renvoyé à votre environnement R.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Affichez le graphique en ouvrant le périphérique graphique R ou en cliquant sur la fenêtre de **tracés** dans RStudio.

    ![Tracé ROC pour le modèle](media/rsql-e2e-rocplot.png "Tracé ROC pour le modèle")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Créer les tracés dans le contexte de calcul local à l’aide de données de SQL Server

Vous pouvez vérifier que le contexte de calcul est local en exécutant `rxGetComputeContext()` à l’invite de commandes. La valeur renvoyée doit être « RxLocalSeq Compute Context ».

1. Pour le contexte de calcul local, le processus est très similaire. Vous utilisez la fonction [rxImport](/r-server/r-reference/revoscaler/rximport) pour ajouter les données spécifiées à votre environnement R local.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. En utilisant les données de la mémoire locale, vous chargez le package **ROCR** et utilisez la fonction de prédiction de ce package pour créer des prédictions.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. Générez un tracé local en fonction des valeurs stockées dans la variable de sortie `pred`.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![traçage des performances du modèle à l’aide de R](media/rsql-e2e-performanceplot.png "traçage des performances du modèle à l’aide de R")

> [!NOTE]
> Selon le nombre de points de données utilisés, vos graphiques peuvent être différents.

## <a name="deploy-the-model"></a>Déployer le modèle

Une fois que vous avez créé un modèle et déterminé qu’il fonctionne correctement, vous souhaiterez probablement le déployer sur un site où les utilisateurs ou les personnes de votre organisation peuvent utiliser le modèle, ou peut-être reformer et réétalonner le modèle régulièrement. Ce processus est parfois appelé *opérationnalisation* d’un modèle. Dans SQL Server, l’opérationnalisation est obtenue en incorporant du code R dans une procédure stockée. Étant donné que le code réside dans la procédure, il peut être appelé à partir de n’importe quelle application capable de se connecter à SQL Server.

Avant de pouvoir appeler le modèle à partir d’une application externe, vous devez l’enregistrer dans la base de données utilisée pour la production. Les modèles formés sont stockés sous forme binaire, dans une seule colonne de type **varbinary(max)** .

Un flux de travail de déploiement classique comprend les étapes suivantes :

1. Sérialiser le modèle dans une chaîne hexadécimale
2. Transmettre l’objet sérialisé à la base de données
3. Enregistrer le modèle dans une colonne varbinary(max)

Dans cette section, vous allez découvrir comment utiliser une procédure stockée pour rendre le modèle persistant et le rendre disponible pour les prédictions. La procédure stockée utilisée dans cette section est PersistModel. La définition de PersistModel se trouve dans [Conditions préalables requises](#prerequisites).

1. Basculez dans votre environnement R local si vous n’êtes pas déjà en train de l’utiliser, sérialisez le modèle et enregistrez-le dans une variable.

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

4. Utilisez Management Studio pour vérifier que le modèle existe. Dans l’Explorateur d’objets, cliquez avec le bouton droit sur la table **nyc_taxi_models**, puis cliquez sur **Sélectionner les 1000 lignes du haut**. Dans Résultats, vous devez voir une représentation binaire dans la colonne **models**.

L’enregistrement d’un modèle dans une table nécessite uniquement une instruction INSERT. Toutefois, il est souvent plus facile d’inclure dans un wrapper une procédure stockée, telle que *PersistModel*.

## <a name="next-steps"></a>Étapes suivantes

Dans la leçon suivante, qui est aussi la dernière, découvrez comment effectuer le scoring sur le modèle enregistré à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].

> [!div class="nextstepaction"]
> [Déployer le modèle R et l’utiliser dans SQL](walkthrough-deploy-and-use-the-model.md)