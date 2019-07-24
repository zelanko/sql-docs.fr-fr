---
title: Leçon 4 prédire les résultats potentiels à l’aide de modèles R
description: Didacticiel illustrant comment faire fonctionner un script R incorporé dans des procédures stockées SQL Server avec des fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 159fb29bf560e755fdc605330d7d20369f55ba08
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345900"
---
# <a name="lesson-4-run-predictions-using-r-embedded-in-a-stored-procedure"></a>Leçon 4 : Exécuter des prédictions à l’aide de R Embedded dans une procédure stockée
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fait partie d’un didacticiel pour les développeurs SQL sur l’utilisation de R dans SQL Server.

Au cours de cette étape, vous allez apprendre à utiliser le modèle par rapport à de nouvelles observations afin de prédire les résultats potentiels. Le modèle est encapsulé dans une procédure stockée qui peut être appelée directement par d’autres applications. La procédure pas à pas illustre plusieurs façons d’effectuer une notation:

- Mode de calcul de **score par lot**: Utilisez une requête SELECT comme entrée de la procédure stockée. La procédure stockée retourne une table d’observations correspondant aux cas d’entrée.

- **Mode de calcul des scores individuels**: Transmettez un ensemble de valeurs de paramètres individuelles comme entrée.  La procédure stockée retourne une seule ligne ou valeur.

Tout d’abord, examinons le fonctionnement du calcul de score en général.

## <a name="basic-scoring"></a>Score de base

La procédure stockée **RxPredict** illustre la syntaxe de base pour l’encapsulation d’un appel RxPredict RevoScaleR dans une procédure stockée.

```sql
CREATE PROCEDURE [dbo].[RxPredict] (@model varchar(250), @inquery nvarchar(max))
AS 
BEGIN 

DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);  
EXEC sp_execute_external_script @language = N'R',
  @script = N' 
    mod <- unserialize(as.raw(model)); 
    print(summary(mod)) 
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE); 
    str(OutputDataSet) 
    print(OutputDataSet) 
    ', 
  @input_data_1 = @inquery, 
  @params = N'@model varbinary(max)',
  @model = @lmodel2 
  WITH RESULT SETS ((Score float));
END
GO
```

+ L’instruction SELECT obtient le modèle sérialisé de la base de données et stocke le modèle dans la variable `mod` r pour un traitement ultérieur à l’aide de R.

+ Les nouveaux cas de notation sont obtenus à partir [!INCLUDE[tsql](../../includes/tsql-md.md)] de la requête `@inquery`spécifiée dans, le premier paramètre de la procédure stockée. Lors de la lecture des données de requête, les lignes sont enregistrées dans la trame de données par défaut, `InputDataSet`. Cette trame de données est transmise à la fonction [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) dans [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), qui génère les scores.
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    Une trame de données ne pouvant contenir qu’une seule ligne, vous pouvez utiliser le même code pour le calcul de score unique ou de lot.
  
+ La valeur retournée par `rxPredict` la fonction est un **float** qui représente la probabilité que le pilote obtient une info-bulle d’une quantité quelconque.

## <a name="batch-scoring-a-list-of-predictions"></a>Notation par lots (une liste de prédictions)

Un scénario plus courant consiste à générer des prédictions pour plusieurs observations en mode batch. Dans cette étape, voyons comment fonctionne la notation par lot.

1.  Commencez par obtenir un plus petit ensemble de données d’entrée à utiliser. Cette requête crée une liste « top 10 » des trajets avec le nombre de passagers et d’autres caractéristiques nécessaires pour établir une prédiction.
  
    ```sql
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **Exemples de résultats**
    
    ```sql
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

2. Créez une procédure stockée  appelée RxPredictBatchOutput [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]dans.

    ```sql
    CREATE PROCEDURE [dbo].[RxPredictBatchOutput] (@model varchar(250), @inquery nvarchar(max))
    AS
    BEGIN
    DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);
    EXEC sp_execute_external_script 
      @language = N'R',
      @script = N'
        mod <- unserialize(as.raw(model));
        print(summary(mod))
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);
        str(OutputDataSet)
        print(OutputDataSet)
      ',
      @input_data_1 = @inquery,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

3.  Fournissez le texte de la requête dans une variable et transmettez-le en tant que paramètre à la procédure stockée:

    ```sql
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'
    
    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[RxPredictBatchOutput] @model = 'RxTrainLogit_model', @inquery = @query_string;
    ```
  
La procédure stockée retourne une série de valeurs représentant la prédiction de chacun des 10 meilleurs voyages. Toutefois, les trajets les plus importants sont également des voyages à passagers uniques avec une distance de trajet relativement brève, pour laquelle le pilote est peu susceptible d’obtenir un pourboire.
  

> [!TIP]
> 
> Au lieu de renvoyer uniquement les résultats «Oui-Conseil» et «sans pourboire», vous pouvez également renvoyer le score de probabilité pour la prédiction, puis appliquer une clause WHERE aux valeurs de la colonne _score_ pour classer le score comme «susceptible d’être noté» ou «improbable», à l’aide d’un valeur de seuil telle que 0,5 ou 0,7. Cette étape n’est pas incluse dans la procédure stockée, mais elle est facile à implémenter.

## <a name="single-row-scoring-of-multiple-inputs"></a>Notation sur une seule ligne de plusieurs entrées

Parfois, vous souhaitez transmettre plusieurs valeurs d’entrée et obtenir une seule prédiction basée sur ces valeurs. Par exemple, vous pouvez configurer une feuille de calcul Excel, une application Web ou un rapport de Reporting Services pour appeler la procédure stockée et fournir des entrées tapées ou sélectionnées par les utilisateurs à partir de ces applications.

Dans cette section, vous allez apprendre à créer des prédictions uniques à l’aide d’une procédure stockée qui prend plusieurs entrées, telles que le nombre de passagers, la distance du trajet, etc. La procédure stockée crée un score basé sur le modèle R stocké précédemment.
  
Si vous appelez la procédure stockée à partir d’une application externe, assurez-vous que les données correspondent aux exigences du modèle R. Vous pourriez par exemple vérifier que les données d’entrée peuvent être transtypées ou converties en un type de données R, ou valider le type de données et la longueur des données. 

1. Créez une procédure stockée **RxPredictSingleRow**.
  
    ```sql
    CREATE PROCEDURE [dbo].[RxPredictSingleRow] @model varchar(50), @passenger_count int = 0, @trip_distance float = 0, @trip_time_in_secs int = 0, @pickup_latitude float = 0, @pickup_longitude float = 0, @dropoff_latitude float = 0, @dropoff_longitude float = 0
    AS
    BEGIN
    DECLARE @inquery nvarchar(max) = N'SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs,  @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)';
    DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);
    EXEC sp_execute_external_script  
      @language = N'R',
      @script = N'  
        mod <- unserialize(as.raw(model));  
        print(summary(mod));  
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
        str(OutputDataSet);
        print(OutputDataSet); 
        ',  
      @input_data_1 = @inquery,  
      @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float', @model = @lmodel2, @passenger_count =@passenger_count, @trip_distance=@trip_distance, @trip_time_in_secs=@trip_time_in_secs, @pickup_latitude=@pickup_latitude, @pickup_longitude=@pickup_longitude, @dropoff_latitude=@dropoff_latitude, @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
    END
    ```

2. Essayez-la en fournissant les valeurs manuellement.
  
    Ouvrez une nouvelle fenêtre de **requête** et appelez la procédure stockée, en fournissant des valeurs pour chacun des paramètres. Les paramètres représentent les colonnes de fonctionnalités utilisées par le modèle et sont requises.

    ```sql
    EXEC [dbo].[RxPredictSingleRow] @model = 'RxTrainLogit_model',
    @passenger_count = 1,
    @trip_distance = 2.5,
    @trip_time_in_secs = 631,
    @pickup_latitude = 40.763958,
    @pickup_longitude = -73.973373,
    @dropoff_latitude =  40.782139,
    @dropoff_longitude = -73.977303
    ```

    Vous pouvez utiliser cette forme plus petite prise en charge pour les [paramètres d’une procédure stockée](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters):
  
    ```sql
    EXEC [dbo].[RxPredictSingleRow] 'RxTrainLogit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. Les résultats indiquent que la probabilité d’obtention d’une info-bulle est faible (zéro) sur ces 10 voyages les plus importants, car tous sont des trajets de passagers uniques sur une distance relativement courte.

## <a name="conclusions"></a>Conclusions

Cela conclut le didacticiel. Maintenant que vous avez appris à incorporer du code R dans des procédures stockées, vous pouvez étendre ces pratiques pour créer vos propres modèles. L’intégration à [!INCLUDE[tsql](../../includes/tsql-md.md)] simplifie grandement le déploiement de modèles R pour la prédiction et l’incorporation de la reformation de modèle dans le cadre d’un workflow de données d’entreprise.

## <a name="previous-lesson"></a>Leçon précédente

[Leçon 3 : Former et enregistrer un modèle R à l’aide de T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)
