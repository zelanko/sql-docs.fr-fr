---
title: Générer un modèle R et l’enregistrer dans SQL Server (procédure pas à pas) - SQL Server Machine Learning
description: Didacticiel montrant comment créer un modèle de langage R utilisé pour l’analytique en base de données de SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 039e5a8970b2161bfe54b1836f3bd12b48477e1a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513056"
---
# <a name="build-an-r-model-and-save-to-sql-server-walkthrough"></a>Créer un modèle R et l’enregistrer dans SQL Server (procédure pas à pas)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans cette étape, découvrez comment créer un modèle machine learning et d’enregistrer le modèle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En enregistrant un modèle, vous pouvez l’appeler directement à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] code, à l’aide de la procédure stockée système, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ou [fonction PREDICT (T-SQL)](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql).

## <a name="prerequisites"></a>Prérequis

Cette étape suppose une session R en cours en fonction des étapes précédentes dans cette procédure pas à pas. Il utilise les connexion chaînes et les objets créés dans ces étapes. Les outils et les packages suivants sont utilisés pour exécuter le script.

+ RGUI.exe pour exécuter des commandes R
+ Management Studio pour exécuter T-SQL
+ Package ROCR
+ Package RODBC

### <a name="create-a-stored-procedure-to-save-models"></a>Créer une procédure stockée d’enregistrer les modèles

Cette étape utilise une procédure stockée pour enregistrer un modèle formé dans SQL Server. Création d’une procédure stockée pour effectuer cette opération facilite la tâche.

Exécutez le code T-SQL suivant dans une fenêtre de requête dans Management Studio pour créer la procédure stockée.

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
> Si vous obtenez une erreur, assurez-vous que votre connexion est autorisé à créer des objets. Vous pouvez accorder des autorisations explicites pour créer des objets en exécutant une instruction T-SQL comme celle-ci : `exec sp_addrolemember 'db_owner', '<user_name>'`.

## <a name="create-a-classification-model-using-rxlogit"></a>Créer un modèle de classification à l’aide de rxLogit

Le modèle est un classifieur binaire qui prédit si le conducteur est susceptible d’obtenir un pourboire lors d’un trajet donné ou non. Vous allez utiliser la source de données que vous avez créé dans la leçon précédente pour former le classifieur de pourboires, à l’aide de la régression logistique.

1. Appelez la fonction [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) , comprise dans le package **RevoScaleR** , pour créer un modèle de régression logistique. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource));
    ```

    L’appel qui génère le modèle est placé dans la fonction system.time. Cela vous donne le temps de générer le modèle.

2. Une fois que vous générez le modèle, vous pouvez le vérifier à l’aide de la `summary` de fonction et afficher les coefficients.

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

1. Tout d’abord, utilisez le [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) (fonction) pour définir un objet de source de données pour stocker le résultat de notation.

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Pour simplifier cet exemple, l’entrée pour le modèle de régression logistique est la même source de données de fonctionnalité (`sql_feature_ds`) que vous avez utilisé pour former le modèle.  Plus généralement, vous aurez sans doute de nouvelles données avec lesquelles calculer les scores, ou vous aurez peut-être mis de côté certaines données de test et de formation.
  
    + Les résultats de prédiction seront enregistrés dans la table, _taxiscoreOutput_. Notez que le schéma pour cette table n’est pas défini lorsque vous créez à l’aide de rxSqlServerData. Le schéma est obtenu à partir de la sortie de rxPredict.
  
    + Pour créer la table qui stocke les valeurs prédites, la connexion SQL en cours d’exécution la fonction de données rxSqlServer doit disposer de privilèges DDL dans la base de données. Si la connexion ne peut pas créer des tables, l’instruction échoue.

2. Appelez la fonction [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) pour générer les résultats.

    ```R
    rxPredict(modelObject = logitObj,
        data = featureDataSource,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Si l’instruction réussit, il doit prendre un certain temps à s’exécuter. Lorsque vous avez terminé, vous pouvez ouvrir SQL Server Management Studio et vérifiez que la table a été créée et qu’il contient la colonne de Score et l’autre sortie attendue.

## <a name="plot-model-accuracy"></a>Tracer la précision du modèle

Pour obtenir une idée de la précision du modèle, vous pouvez utiliser la [rxRoc](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc) fonction pour tracer la courbe Receiver Operating Curve. Étant donné que rxRoc est une des nouvelles fonctions fournies par le package RevoScaleR qui prend en charge les contextes de calcul distants, vous avez deux options :

+ Vous pouvez utiliser la fonction rxRoc pour exécuter le tracé dans le contexte de calcul à distance et de retourner le tracé à votre client local.

+ Vous pouvez également importer les données sur votre ordinateur client R et utiliser d’autres fonctions de traçage R pour créer le graphique de performances.

Dans cette section, vous expérimenterez les deux techniques.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Exécuter un tracé dans le contexte de calcul distant (SQL Server)

1. Appelez la fonction rxRoc et fournir les données définies précédemment en tant qu’entrée.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    Cet appel renvoie les valeurs utilisées dans le graphique ROC de l’informatique. La colonne d’étiquette est _tipped_, qui présente les résultats réels que vous essayez de prédire, tandis que le _Score_ colonne a la prédiction.

2. Pour réellement tracer le graphique, vous pouvez enregistrer l’objet ROC et puis dessinez-le avec la fonction de traçage. Le graphique est créé sur le contexte de calcul à distance et retourné à votre environnement R.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Afficher le graphique en ouvrant le périphérique graphique R ou en cliquant sur le **tracer** fenêtre dans RStudio.

    ![Tracé ROC pour le modèle](media/rsql-e2e-rocplot.png "Tracé ROC pour le modèle")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Créer les tracés dans le contexte de calcul local à l’aide de données de SQL Server

Vous pouvez vérifier le contexte de calcul est local en exécutant `rxGetComputeContext()` à l’invite de commandes. La valeur de retour doit être « Contexte de calcul RxLocalSeq ».

1. Pour le contexte de calcul local, le processus est très similaire. Vous utilisez le [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) (fonction) pour afficher les données spécifiées dans votre environnement R local.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. En utilisant les données dans la mémoire locale, vous chargez le **ROCR** empaqueter et utiliser la fonction de prédiction à partir de ce package pour créer des prédictions de nouveau.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. Générer un tracé local, en fonction des valeurs stockées dans la variable de sortie `pred`.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![Traçage des performances d’un modèle à l’aide de R](media/rsql-e2e-performanceplot.png "Traçage des performances d’un modèle à l’aide de R")

> [!NOTE]
> Vos graphiques peuvent différer de ceux-ci, selon le nombre de points de données que vous avez utilisé.

## <a name="deploy-the-model"></a>Déployer le modèle

Une fois que vous avez créé un modèle et vous être assuré qu’elle s’exécute correctement, vous souhaiterez probablement déployer sur un site où les utilisateurs ou les personnes de votre organisation peuvent rendre utilisent le modèle, ou peut-être reformer et revoir le modèle sur une base régulière. Ce processus est parfois appelé *Opérationnalisation* un modèle. Dans SQL Server, Opérationnalisation est obtenue en incorporant le code R dans une procédure stockée. Étant donné que le code se trouve dans la procédure, elle peut être appelée à partir de n’importe quelle application pouvant se connecter à SQL Server.

Avant de pouvoir appeler le modèle à partir d’une application externe, vous devez enregistrer le modèle dans la base de données utilisée pour la production. Modèles formés sont stockés sous forme binaire, dans une seule colonne de type **varbinary (max)**.

Un flux de travail de déploiement classique se compose des étapes suivantes :

1. Sérialisation du modèle dans une chaîne hexadécimale
2. Transmettre l’objet sérialisé à la base de données
3. Enregistrer le modèle dans une colonne varbinary (max)

Dans cette section, découvrez comment utiliser une procédure stockée pour conserver le modèle et le rendre disponible pour les prédictions. La procédure stockée utilisée dans cette section est PersistModel. La définition de PersistModel est [conditions préalables](#prerequisites).

1. Revenez à votre environnement R local si vous ne l’utilisez pas déjà, sérialiser le modèle et enregistrez-le dans une variable.

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. Ouvrez une connexion ODBC à l’aide **RODBC**. Vous pouvez omettre l’appel à RODBC si vous avez déjà le package chargé.

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

3. Appelez la procédure PersistModel stockée sur SQL Server pour transmite l’objet sérialisé à la base de données et stocker la représentation binaire du modèle dans une colonne. 

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

4. Utilisez Management Studio pour vérifier le modèle existe. Dans l’Explorateur d’objets, cliquez sur le **nyc_taxi_models** de table et cliquez sur **sélectionner les 1000 premières lignes**. Dans les résultats, vous devez voir une représentation binaire dans le **modèles** colonne.

L’enregistrement d’un modèle dans une table nécessite uniquement une instruction INSERT. Toutefois, il est souvent plus facile lorsque encapsulée dans une procédure stockée, tel que *PersistModel*.

## <a name="next-steps"></a>Étapes suivantes

Dans la prochaine et dernière leçon, apprenez à effectuer le calcul de scores sur le modèle enregistré à l’aide [!INCLUDE[tsql](../../includes/tsql-md.md)].

> [!div class="nextstepaction"]
> [Déployer le modèle R et l’utiliser dans SQL](walkthrough-deploy-and-use-the-model.md)
