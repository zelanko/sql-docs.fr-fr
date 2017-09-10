---
title: "Étape 6 : Rendez le modèle opérationnel | Documents Microsoft"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- python-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b33f3876f054d7e7150a18967d5cfa37dd2d82bf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="step-6-operationalize-the-model"></a>Étape 6 : Rendre le modèle opérationnel

Dans cette étape, vous allez apprendre à *opérationnaliser* les modèles que vous avez formé et enregistré à l’étape précédente. Tiens dans ce cas signifie « déploiement du modèle en production pour calculer les scores ». Il est facile à suivre si votre code Python est contenue dans une procédure stockée. Vous pouvez ensuite appeler la procédure stockée à partir d’applications, pour effectuer des prévisions sur nouvelles observations.

Vous apprendrez à deux méthodes d’appel d’un modèle de Python à partir d’une procédure stockée :

- **Mode de calcul de score du lot**: utiliser une requête SELECT pour fournir plusieurs lignes de données. La procédure stockée retourne une table d’observations correspondant aux cas d’entrée.
- **Mode de calcul de score individuel**: passer un ensemble de valeurs de paramètres en tant qu’entrée.  La procédure stockée retourne une seule ligne ou valeur.

## <a name="scoring-using-the-scikit-learn-model"></a>Calcul de score à l’aide de la scikit-en savoir plus de modèle

La procédure stockée _PredictTipSciKitPy_ utilise le scikit-en savoir plus le modèle. Cette procédure stockée illustre la syntaxe de base pour encapsuler un appel de prédiction Python dans une procédure stockée.

- Le nom du modèle à utiliser est fourni en tant que paramètre d’entrée à la procédure stockée. 
- La procédure stockée puis charge le modèle sérialisé à partir de la table de base de données `nyc_taxi_models`.table, à l’aide de l’instruction SELECT dans la procédure stockée.
- Le modèle sérialisé est stocké dans la variable de Python `mod` pour un traitement supplémentaire à l’aide de Python.
- Les nouveaux cas qui doivent être évaluées sont obtenues à partir de la [!INCLUDE[tsql](../../includes/tsql-md.md)] requête spécifiée dans `@input_data_1`. Lors de la lecture des données de requête, les lignes sont enregistrées dans la trame de données par défaut, `InputDataSet`.
- Cette trame de données est transmise à la `predict_proba` fonction du modèle de régression logistique, `mod`, lequel a été créée à l’aide de scikit-Découvrez le modèle. 
- Le `predict_proba` (fonction) (`probArray = mod.predict_proba(X)`) retourne un **float** qui représente la probabilité que recevra un Conseil (de n’importe quel volume).
- La procédure stockée calcule également une mesure de précision, AUC (zone sous la courbe). Les mesures de précision telles que AUC ne peuvent être générés si vous fournissez également l’étiquette cible (par exemple, la colonne pourboires). Prédictions n’avez pas besoin de l’étiquette cible (variable `y`), mais le calcul de mesures de précision.

  Par conséquent, si vous n’avez pas les étiquettes de cible pour les données à noter, vous pouvez modifier la procédure stockée pour supprimer les calculs AUC et se contentent de retourner les probabilités de Conseil dans les fonctionnalités (variable `X` dans la procédure stockée).

```SQL
CREATE PROCEDURE [dbo].[PredictTipSciKitPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
  EXEC sp_execute_external_script
    @language = N'Python',
    @script = N'
        import pickle;
        import numpy;
        import pandas;
        from sklearn import metrics
        
        mod = pickle.loads(lmodel2)
        
        X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
        y = numpy.ravel(InputDataSet[["tipped"]])
        
        probArray = mod.predict_proba(X)
        probList = []
        for i in range(len(probArray)):
          probList.append((probArray[i])[1])
        
        probArray = numpy.asarray(probList)
        fpr, tpr, thresholds = metrics.roc_curve(y, probArray)
        aucResult = metrics.auc(fpr, tpr)
        print ("AUC on testing data is: " + str(aucResult))
        
        OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
        ',  
    @input_data_1 = @inquery,
    @input_data_1_name = N'InputDataSet',
    @params = N'@lmodel2 varbinary(max)',
    @lmodel2 = @lmodel2
  WITH RESULT SETS ((Score float));
END
GO
```

## <a name="scoring-using-the-revoscalepy-model"></a>Calcul de score à l’aide du modèle revoscalepy

La procédure stockée _PredictTipRxPy_ utilise un modèle qui a été créé à l’aide de la **revoscalepy** bibliothèque. Il fonctionne de la même façon que les _PredictTipSciKitPy_ procédure, mais certaines modifications pour la **revoscalepy** fonctions.

```SQL
CREATE PROCEDURE [dbo].[PredictTipRxPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from sklearn import metrics
      from revoscalepy.functions.RxPredict import rx_predict_ex;
      
      mod = pickle.loads(lmodel2)
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      y = numpy.ravel(InputDataSet[["tipped"]])
      
      probArray = rx_predict_ex(mod, X)
      probList = []
      for i in range(len(probArray._results["tipped_Pred"])):
        probList.append((probArray._results["tipped_Pred"][i]))
      
      probArray = numpy.asarray(probList)
      fpr, tpr, thresholds = metrics.roc_curve(y, probArray)
      aucResult = metrics.auc(fpr, tpr)
      print ("AUC on testing data is: " + str(aucResult))
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
      ',    
    @input_data_1 = @inquery,
    @input_data_1_name = N'InputDataSet',
    @params = N'@lmodel2 varbinary(max)',
    @lmodel2 = @lmodel2
  WITH RESULT SETS ((Score float));
END
GO
```

## <a name="batch-scoring-using-a-select-query"></a>Calcul de score du lot à l’aide d’une requête SELECT

Les procédures stockées **PredictTipSciKitPy** et **PredictTipRxPy** requièrent deux paramètres d’entrée : 

- La requête qui Récupère les données pour calculer les scores
- Le nom d’un modèle formé

Dans cette section, vous allez apprendre à passer les arguments à la procédure stockée facilement modifier le modèle et les données utilisées pour calculer les scores.

1. Définir les données d’entrée et appeler les procédures stockées pour calculer les scores comme suit. Cet exemple utilise la procédure stockée PredictTipSciKitPy pour calculer les scores et passe le nom du modèle et de la chaîne de requête

    ```SQL
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    La procédure stockée retourne les probabilités prévues pour chaque voyage qui a été passée dans le cadre de la requête d’entrée. Si vous utilisez SSMS (SQL Server Management Studio) pour l’exécution de requêtes, les probabilités seront affiche sous forme de table dans le **résultats** volet. Le **Messages** volet génère les mesures de précision (AUC ou zone sous la courbe) avec une valeur de 0,56 environ.

2. Pour utiliser le **revoscalepy** de modèle pour le calcul de score, appelez la procédure stockée **PredictTipRxPy**, en passant la chaîne de requête et de nom de modèle.

    ```SQL
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="score-individual-rows-using-scikit-learn-model"></a>Un score de lignes individuelles à l’aide de scikit-en savoir plus de modèle

Dans certains cas, au lieu de calcul du score du lot, vous souhaitez transmettre dans un cas unique, l’obtention des valeurs à partir d’une application et obtenir un résultat unique en fonction de ces valeurs. Par exemple, vous pouvez configurer une feuille de calcul Excel, une application web ou un rapport Reporting Services pour appeler la procédure stockée et fournir des entrées tapées ou sélectionnées par les utilisateurs.

Dans cette section, vous allez apprendre à créer des prévisions uniques en appelant une procédure stockée.

1. Prenez une minute pour examiner le code des procédures stockées [PredictTipSingleModeSciKitPy](#PredictTipSingleModeSciKitPy) et [PredictTipSingleModeRxPy](#PredictTipSingleModeRxPy), qui sont inclus dans le cadre du téléchargement. Ces procédures stockées utilisent la scikit-en savoir plus et les modèles de revoscalepy et effectuer le calcul de score comme suit :

  - Le nom du modèle et plusieurs valeurs uniques sont fournis en tant qu’entrée. Ces entrées incluent le nombre de passagers, distance du voyage et ainsi de suite.
  - Une fonction table, `fnEngineerFeatures`, prend des valeurs d’entrée et convertit la latitude et longitudes pour indiquer à distance. [Leçon 4](sqldev-py4-create-data-features-using-t-sql.md) contient une description de cette fonction table.
  - Si vous appelez la procédure stockée à partir d’une application externe, assurez-vous que les données d’entrée correspond à des fonctionnalités d’entrée requises du modèle Python. Il peut s’agir de casting ou conversion des données d’entrée en un type de données Python, ou la validation de type de données et la longueur des données.
  - La procédure stockée crée un score basé sur le modèle de Python stocké.

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

Voici la définition de la procédure stockée qui effectue le calcul de score à l’aide de la **scikit-en savoir plus** modèle.

```SQL
CREATE PROCEDURE [dbo].[PredictTipSingleModeSciKitPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
  SELECT * FROM [dbo].[fnEngineerFeatures]( 
    @passenger_count,
    @trip_distance,
    @trip_time_in_secs,
    @pickup_latitude,
    @pickup_longitude,
    @dropoff_latitude,
    @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      probList = []
      probList.append((mod.predict_proba(X)[0])[1])
      
      # Create output data frame
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
    ',
    @input_data_1 = @inquery,
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      @model = @lmodel2,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance,
      @trip_time_in_secs=@trip_time_in_secs,
      @pickup_latitude=@pickup_latitude,
      @pickup_longitude=@pickup_longitude,
      @dropoff_latitude=@dropoff_latitude,
      @dropoff_longitude=@dropoff_longitude
  WITH RESULT SETS ((Score float));
END
GO
```

### <a name="predicttipsinglemoderxpy"></a>PredictTipSingleModeRxPy

Voici la définition de la procédure stockée qui effectue le calcul de score à l’aide de la **revoscalepy** modèle.

```SQL
CREATE PROCEDURE [dbo].[PredictTipSingleModeRxPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
    SELECT * FROM [dbo].[fnEngineerFeatures]( 
      @passenger_count,
      @trip_distance,
      @trip_time_in_secs,
      @pickup_latitude,
      @pickup_longitude,
      @dropoff_latitude,
      @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from revoscalepy.functions.RxPredict import rx_predict_ex;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      
      probArray = rx_predict_ex(mod, X)
      
      probList = []
      probList.append(probArray._results["tipped_Pred"])
      
      # Create output data frame
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
      ',
    @input_data_1 = @inquery,
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      @model = @lmodel2,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance,
      @trip_time_in_secs=@trip_time_in_secs,
      @pickup_latitude=@pickup_latitude,
      @pickup_longitude=@pickup_longitude,
      @dropoff_latitude=@dropoff_latitude,
      @dropoff_longitude=@dropoff_longitude
  WITH RESULT SETS ((Score float));
END
GO
```

2.  Pour l’essayer, ouvrez une nouvelle **requête** fenêtre et appelez la procédure stockée, en tapant les paramètres pour chacune des colonnes de fonctionnalité.

    ```SQL
    -- Call stored procedure PredictTipSingleModeSciKitPy to score using SciKit-Learn model
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'linear_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    -- Call stored procedure PredictTipSingleModeRxPy to score using revoscalepy model
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```
    
    Les sept valeurs existe pour ces colonnes de fonctionnalités, dans l’ordre :
    
    -   *passenger_count*
    -   *trip_distance*
    -   *trip_time_in_secs*
    -   *pickup_latitude*
    -   *pickup_longitude*
    -   *dropoff_latitude*
    -   *dropoff_longitude*

3. La sortie à partir de deux procédures est la probabilité d’une info-bulle est payée pour le voyage taxi avec les paramètres ou les fonctionnalités ci-dessus.

## <a name="conclusions"></a>Conclusions

Dans ce didacticiel, vous avez appris à utiliser avec le code Python incorporé dans des procédures stockées. L’intégration avec [!INCLUDE[tsql](../../includes/tsql-md.md)] rend plus facile à déployer des modèles de Python pour la prédiction et d’incorporer le recyclage de modèle dans le cadre d’un workflow de données d’entreprise.

## <a name="previous-step"></a>Étape précédente
[Étape 6 : Rendre le modèle opérationnel](sqldev-py6-operationalize-the-model.md)

## <a name="see-also"></a>Voir aussi

[Machine Learning Services avec Python](../python/sql-server-python-services.md)

