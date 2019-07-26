---
title: Prédire les résultats potentiels à l’aide de modèles python
description: Didacticiel illustrant comment mettre en œuvre le script PYthon incorporé dans SQL Server procédures stockées avec des fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/02/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: b04e57c45c6113d4a0404a3a338e6beba4cda813
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68468596"
---
# <a name="run-predictions-using-python-embedded-in-a-stored-procedure"></a>Exécuter des prédictions à l’aide de Python Embedded dans une procédure stockée
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article fait partie d’un didacticiel, [l’analytique Python en base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md). 

Au cours de cette étape, vous allez apprendre à faire *fonctionner* les modèles que vous avez formés et enregistrés à l’étape précédente.

Dans ce scénario, l’exploitation implique le déploiement du modèle en production pour la notation. L’intégration avec SQL Server facilite ce processus, car vous pouvez incorporer du code python dans une procédure stockée. Pour faire des prédictions à partir du modèle en fonction de nouvelles entrées, il vous suffit d’appeler la procédure stockée à partir d’une application et de transmettre les nouvelles données.

Cette leçon présente deux méthodes de création de prédictions basées sur un modèle Python: notation par lots et notation ligne par ligne.

- **Notation par lot:** Pour fournir plusieurs lignes de données d’entrée, transmettez une requête SELECT en tant qu’argument à la procédure stockée. Le résultat est une table d’observations correspondant aux cas d’entrée.
- **Notation individuelle:** Transmettez un ensemble de valeurs de paramètres individuelles comme entrée.  La procédure stockée retourne une seule ligne ou valeur.

Tout le code python nécessaire pour le calcul des scores est fourni dans le cadre des procédures stockées.

## <a name="batch-scoring"></a>Notation par lot

Les deux premières procédures stockées illustrent la syntaxe de base pour l’encapsulation d’un appel de prédiction python dans une procédure stockée. Les deux procédures stockées requièrent une table de données en tant qu’entrées.

- Le nom du modèle exact à utiliser est fourni en tant que paramètre d’entrée à la procédure stockée. La procédure stockée charge le modèle sérialisé à partir de la `nyc_taxi_models`table de base de données. table, à l’aide de l’instruction SELECT de la procédure stockée.
- Le modèle sérialisé est stocké dans la variable `mod` Python pour un traitement ultérieur à l’aide de Python.
- Les nouveaux cas qui doivent être notés sont obtenus à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] la requête spécifiée `@input_data_1`dans. Lors de la lecture des données de requête, les lignes sont enregistrées dans la trame de données par défaut, `InputDataSet`.
- Les deux procédures stockées utilisent des `sklearn` fonctions de pour calculer une mesure de précision, AUC (zone sous la courbe). Les mesures de précision telles que AUC peuvent être générées uniquement si vous fournissez également l’étiquette cible (colonne de _pourboire_ ). Les prédictions n’ont pas besoin de l' `y`étiquette cible (variable), contrairement au calcul de la métrique de précision.

    Par conséquent, si vous n’avez pas d’étiquette cible pour les données à noter, vous pouvez modifier la procédure stockée pour supprimer les calculs AUC et retourner uniquement les probabilités de l’info-bulle `X` à partir des fonctionnalités (variable dans la procédure stockée).

### <a name="predicttipscikitpy"></a>PredictTipSciKitPy

Rrun les instructions T-SQL suivantes pour créer les procédures stockées. Cette procédure stockée requiert un modèle basé sur le package scikit-Learn, car elle utilise des fonctions spécifiques à ce package:

+ La trame de données contenant des entrées est `predict_proba` transmise à la fonction du modèle de `mod`régression logistique,. La `predict_proba` fonction (`probArray = mod.predict_proba(X)`) retourne une valeur **float** qui représente la probabilité qu’une info-bulle soit donnée.

```sql
DROP PROCEDURE IF EXISTS PredictTipSciKitPy;
GO

CREATE PROCEDURE [dbo].[PredictTipSciKitPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
EXEC sp_execute_external_script
  @language = N'Python',
  @script = N'
import pickle;
import numpy;
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

### <a name="predicttiprxpy"></a>PredictTipRxPy

Cette procédure stockée utilise les mêmes entrées et crée le même type de score que la procédure stockée précédente, mais utilise des fonctions du package **revoscalepy** fourni avec SQL Server machine learning.

```sql
DROP PROCEDURE IF EXISTS PredictTipRxPy;
GO

CREATE PROCEDURE [dbo].[PredictTipRxPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
EXEC sp_execute_external_script 
  @language = N'Python',
  @script = N'
import pickle;
import numpy;
from sklearn import metrics
from revoscalepy.functions.RxPredict import rx_predict;

mod = pickle.loads(lmodel2)
X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
y = numpy.ravel(InputDataSet[["tipped"]])

probArray = rx_predict(mod, X)
probList = probArray["tipped_Pred"].values 

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

## <a name="run-batch-scoring-using-a-select-query"></a>Exécuter le calcul de score par lot à l’aide d’une requête SELECT

Les procédures stockées **PredictTipSciKitPy** et **PredictTipRxPy** requièrent deux paramètres d’entrée: 

- Requête qui récupère les données pour la notation
- Nom d’un modèle formé

En passant ces arguments à la procédure stockée, vous pouvez sélectionner un modèle particulier ou modifier les données utilisées pour le calcul de score.

1. Pour utiliser le modèle **scikit-Learn** pour la notation, appelez la procédure stockée **PredictTipSciKitPy**, en passant le nom du modèle et la chaîne de requête en tant qu’entrées.

    ```sql
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    La procédure stockée retourne des probabilités prédites pour chaque voyage passé dans le cadre de la requête d’entrée. 
    
    Si vous utilisez SSMS (SQL Server Management Studio) pour exécuter des requêtes, les probabilités s’affichent sous la forme d’une table dans le volet **résultats** . Le volet **messages** génère la mesure de précision (AUC ou zone sous courbe) avec une valeur de environ 0,56.

2. Pour utiliser le modèle **revoscalepy** pour la notation, appelez la procédure stockée **PredictTipRxPy**, en passant le nom du modèle et la chaîne de requête en tant qu’entrées.

    ```sql
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="single-row-scoring"></a>Notation sur une seule ligne

Parfois, au lieu de la notation par lot, vous souhaiterez peut-être passer un seul cas, obtenir des valeurs d’une application et retourner un résultat unique en fonction de ces valeurs. Par exemple, vous pouvez configurer une feuille de calcul Excel, une application Web ou un rapport pour appeler la procédure stockée et lui transmettre des entrées tapées ou sélectionnées par les utilisateurs.

Dans cette section, vous allez apprendre à créer des prédictions uniques en appelant deux procédures stockées:

+ [PredictTipSingleModeSciKitPy](#predicttipsinglemodescikitpy) est conçu pour un score à une seule ligne à l’aide du modèle scikit-Learn.
+ [PredictTipSingleModeRxPy](#predicttipsinglemoderxpy) est conçu pour un score à une seule ligne à l’aide du modèle revoscalepy.
+ Si vous n’avez pas encore formé un modèle, revenez à l' [étape 5](sqldev-py5-train-and-save-a-model-using-t-sql.md)!

Les deux modèles prennent comme entrée une série de valeurs uniques, telles que le nombre de passagers, la distance de trajet, etc. Une fonction table, `fnEngineerFeatures`, est utilisée pour convertir les valeurs de latitude et de longitude des entrées en une nouvelle fonctionnalité, distance directe. La [leçon 4](sqldev-py4-create-data-features-using-t-sql.md) contient une description de cette fonction table.

Les deux procédures stockées créent un score basé sur le modèle Python.

> [!NOTE]
> 
> Il est important de fournir toutes les fonctionnalités d’entrée requises par le modèle python quand vous appelez la procédure stockée à partir d’une application externe. Pour éviter les erreurs, vous devrez peut-être effectuer un cast ou une conversion des données d’entrée en un type de données python, en plus de la validation du type de données et de la longueur des données.

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

Prenez une minute pour examiner le code de la procédure stockée qui effectue le calcul de score à l’aide du modèle **scikit-Learn** .

```sql
DROP PROCEDURE IF EXISTS PredictTipSingleModeSciKitPy;
GO

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
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
EXEC sp_execute_external_script 
  @language = N'Python',
  @script = N'
import pickle;
import numpy;

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

La procédure stockée suivante effectue un calcul de score à l’aide du modèle **revoscalepy** .

```sql
DROP PROCEDURE IF EXISTS PredictTipSingleModeRxPy;
GO

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
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
EXEC sp_execute_external_script 
  @language = N'Python',
  @script = N'
import pickle;
import numpy;
from revoscalepy.functions.RxPredict import rx_predict;

# Load model and unserialize
mod = pickle.loads(model)

# Get features for scoring from input data
X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]

# Score data to get tip prediction probability as a list (of float)

probArray = rx_predict(mod, X)

probList = []
probList = probArray["tipped_Pred"].values

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

### <a name="generate-scores-from-models"></a>Générer des scores à partir de modèles

Une fois les procédures stockées créées, il est facile de générer un score basé sur l’un ou l’autre modèle. Ouvrez simplement une nouvelle fenêtre de **requête** , puis tapez ou collez des paramètres pour chacune des colonnes de fonctionnalité. Les sept valeurs requises sont pour ces colonnes de fonctionnalités, dans l’ordre:
    
+ *passenger_count*
+ *trip_distance* v*trip_time_in_secs*
+ *pickup_latitude*
+ *pickup_longitude*
+ *dropoff_latitude*
+ *dropoff_longitude*

1. Pour générer une prédiction à l’aide du modèle **revoscalepy** , exécutez l’instruction suivante:
  
    ```sql
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

2. Pour générer un score à l’aide du modèle **scikit-Learn** , exécutez l’instruction suivante:

    ```sql
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'SciKit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

La sortie des deux procédures est une probabilité qu’un pourboire soit payé pour le trajet de taxi avec les paramètres ou les fonctionnalités spécifiés.

## <a name="conclusions"></a>Conclusions

Dans ce didacticiel, vous avez appris à utiliser du code python incorporé dans des procédures stockées. Grâce [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’intégration, il est beaucoup plus facile de déployer des modèles Python pour la prédiction et d’incorporer la reformation de modèle dans le cadre d’un flux de travail de données d’entreprise.

## <a name="previous-step"></a>Étape précédente

[Former et enregistrer un modèle python](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="see-also"></a>Voir aussi

[Extension Python dans SQL Server](../concepts/extension-python.md)
