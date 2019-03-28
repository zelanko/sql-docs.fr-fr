---
title: Prédire les résultats potentiels à l’aide de modèles de Python - SQL Server Machine Learning
description: Didacticiel montrant comment faire fonctionner le script PYthon incorporé dans SQL Server procédures stockées avec les fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/02/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: de46594a5de2bee6e50786de25826c96da01ae53
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513066"
---
# <a name="run-predictions-using-python-embedded-in-a-stored-procedure"></a>Exécuter des prédictions à l’aide de Python incorporé dans une procédure stockée
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fait partie d’un didacticiel, [analytique en base de données Python pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md). 

Cette étape, vous allez apprendre à *opérationnaliser* les modèles que vous avez formé et enregistré à l’étape précédente.

Dans ce scénario, Opérationnalisation signifie du déploiement du modèle en production pour calculer les scores. L’intégration avec SQL Server rend cela assez facile, car vous pouvez incorporer le code Python dans une procédure stockée. Pour obtenir des prédictions dans le modèle basé sur les nouvelles entrées, simplement appeler la procédure stockée à partir d’une application et transmettre les nouvelles données.

Cette leçon illustre deux méthodes pour créer des prédictions basées sur un modèle Python : calcul de score et la notation de ligne par ligne du lot.

- **Notation de lot :** Pour fournir plusieurs lignes de données d’entrée, transmettre une requête SELECT en tant qu’argument à la procédure stockée. Le résultat est une table d’observations correspondant aux cas d’entrée.
- **Personne notation :** Transmettre un ensemble de valeurs de paramètres en tant qu’entrée.  La procédure stockée retourne une seule ligne ou valeur.

Tout le code Python que nécessaire pour calculer les scores est fourni dans le cadre des procédures stockées.

## <a name="batch-scoring"></a>Notation par lot

Les deux premières procédures stockées illustrent la syntaxe de base pour l’encapsulation d’un appel de prédiction de Python dans une procédure stockée. Les deux procédures stockées requièrent une table de données en tant qu’entrées.

- Le nom du modèle exact à utiliser est fourni en tant que paramètre d’entrée à la procédure stockée. La procédure stockée charge le modèle sérialisé à partir de la table de base de données `nyc_taxi_models`.table, à l’aide de l’instruction SELECT dans la procédure stockée.
- Le modèle sérialisé est stocké dans la variable Python `mod` pour un traitement ultérieur à l’aide de Python.
- Les nouveaux cas devant être notés sont obtenues à partir de la [!INCLUDE[tsql](../../includes/tsql-md.md)] requête spécifiée dans `@input_data_1`. Lors de la lecture des données de requête, les lignes sont enregistrées dans la trame de données par défaut, `InputDataSet`.
- Les deux procédures stockées utilisent des fonctions à partir de `sklearn` pour calculer une mesure de précision, AUC (aire sous la courbe). Mesures de précision telles que AUC ne peuvent être générés que si vous spécifiez également l’étiquette cible (le _tipped_ colonne). Prédictions n’avez pas besoin de l’étiquette cible (variable `y`), mais le calcul de mesures de précision.

    Par conséquent, si vous n’avez pas les étiquettes de cible pour les données à noter, vous pouvez modifier la procédure stockée pour supprimer les calculs AUC et retourner uniquement les probabilités d’info-bulle à partir de caractéristiques (variable `X` dans la procédure stockée).

### <a name="predicttipscikitpy"></a>PredictTipSciKitPy

Exécute le T-SQL suivant les instructions pour créer les procédures stockées. Cette procédure stockée requiert un modèle basé sur le scikit-Découvrez le package, car elle utilise des fonctions spécifiques à ce package :

+ La trame de données contenant des entrées est passée à la `predict_proba` fonction du modèle de régression logistique, `mod`. Le `predict_proba` (fonction) (`probArray = mod.predict_proba(X)`) retourne un **float** qui représente la probabilité qu’un pourboire (d’un montant quelconque) va être versé.

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

Cette procédure stockée utilise les mêmes entrées et crée le même type de résultats en tant que la procédure stockée précédente, mais utilise des fonctions à partir de la **revoscalepy** package fourni avec l’apprentissage de SQL Server.

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

## <a name="run-batch-scoring-using-a-select-query"></a>Exécuter la notation par lot à l’aide d’une requête SELECT

Les procédures stockées **PredictTipSciKitPy** et **PredictTipRxPy** nécessite deux paramètres d’entrée : 

- La requête qui Récupère les données pour calculer les scores
- Le nom d’un modèle formé

En transmettant les arguments à la procédure stockée, vous pouvez sélectionner un modèle particulier ou modifier les données utilisées pour calculer les scores.

1. Pour utiliser le **scikit-Découvrez** pour calculer les scores de modèle, appelez la procédure stockée **PredictTipSciKitPy**, en passant le nom de modèle et de chaîne de requête en tant qu’entrées.

    ```sql
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    La procédure stockée retourne les probabilités prédites pour chaque course qui a été passée dans le cadre de la requête d’entrée. 
    
    Si vous utilisez SSMS (SQL Server Management Studio) pour exécuter des requêtes, les probabilités apparaîtront en tant que table dans le **résultats** volet. Le **Messages** volet génère les mesures de précision (ASC ou zone sous courbe) avec une valeur de 0,56 environ.

2. Pour utiliser le **revoscalepy** pour calculer les scores de modèle, appelez la procédure stockée **PredictTipRxPy**, en passant le nom de modèle et de chaîne de requête en tant qu’entrées.

    ```sql
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="single-row-scoring"></a>Ligne unique de score

Au lieu de notation par lots, vous pouvez parfois à passer dans un cas unique, l’obtention de valeurs à partir d’une application et en retournant un résultat unique basé sur ces valeurs. Par exemple, vous pouvez configurer une feuille de calcul Excel, l’application web ou le rapport pour appeler la procédure stockée et passez-la à entrées sélectionnées par les utilisateurs ou non typé.

Dans cette section, vous allez apprendre à créer des prédictions uniques en appelant deux procédures stockées :

+ [PredictTipSingleModeSciKitPy](#PredictTipSingleModeSciKitPy) est conçu pour calculer les scores seule ligne à l’aide de la scikit-Découvrez le modèle.
+ [PredictTipSingleModeRxPy](#PredictTipSingleModeRxPy) est conçu pour calculer les scores seule ligne à l’aide du modèle revoscalepy.
+ Si vous n’avez pas formé un modèle encore, revenez au [étape 5](sqldev-py5-train-and-save-a-model-using-t-sql.md)!

Les deux prennent des modèles en tant qu’entrée d’une série de valeurs uniques, telles que le nombre de passagers, la distance de course et ainsi de suite. Une fonction table, `fnEngineerFeatures`, est utilisé pour convertir des valeurs de latitude et longitude à partir des entrées à une nouvelle fonctionnalité, la distance directe. [Leçon 4](sqldev-py4-create-data-features-using-t-sql.md) contient une description de cette fonction table.

Les deux procédures stockées créer un score basé sur le modèle de Python.

> [!NOTE]
> 
> Il est important que vous fournissez toutes les fonctionnalités d’entrée requises par le modèle de Python lorsque vous appelez la procédure stockée à partir d’une application externe. Pour éviter les erreurs, vous devrez peut-être effectuer un cast ou convertir les données d’entrée à un type de données Python, en plus de la validation de type de données et la longueur de données.

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

Prenez une minute pour examiner le code de la procédure stockée qui effectue le calcul de score à l’aide de la **scikit-Découvrez** modèle.

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

La procédure stockée suivante effectue la notation à l’aide du **revoscalepy** modèle.

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

Une fois que les procédures stockées ont été créées, il est facile de générer un score basé sur un modèle. Il suffit d’ouvrir un nouveau **requête** fenêtre et tapez ou collez des paramètres pour chacune des colonnes de fonctionnalité. Les sept requis sont des valeurs pour ces colonnes de fonctionnalité, dans l’ordre :
    
+ *passenger_count*
+ *trip_distance* v*trip_time_in_secs*
+ *pickup_latitude*
+ *pickup_longitude*
+ *dropoff_latitude*
+ *dropoff_longitude*

1. Pour générer une prédiction à l’aide de la **revoscalepy** modèle, exécutez cette instruction :
  
    ```sql
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

2. Pour générer un score à l’aide de la **scikit-Découvrez** modèle, exécutez cette instruction :

    ```sql
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'SciKit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

La sortie à partir de ces deux procédures est une probabilité d’un pourboire pour une course de taxi avec les paramètres spécifiés ou les fonctionnalités.

## <a name="conclusions"></a>Conclusions

Dans ce didacticiel, vous avez appris à utiliser du code Python incorporé dans des procédures stockées. L’intégration avec [!INCLUDE[tsql](../../includes/tsql-md.md)] rend beaucoup plus facile de déployer des modèles de Python pour la prédiction d’incorporer la REFORMATION du modèle en tant que partie d’un flux de travail de données d’entreprise.

## <a name="previous-step"></a>Étape précédente

[Former et enregistrer un modèle Python](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="see-also"></a>Voir aussi

[Extension de Python dans SQL Server](../concepts/extension-python.md)
