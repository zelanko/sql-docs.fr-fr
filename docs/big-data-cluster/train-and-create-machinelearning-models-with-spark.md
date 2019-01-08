---
title: Modèles ML de train/créer avec Spark
titleSuffix: SQL Server 2019 big data clusters
description: Utiliser PySpark pour former et créer des modèles d’apprentissage automatique avec Spark sur des clusters de données volumineuses de SQL Server (version préliminaire).
author: lgongmsft
ms.author: shivprashant
ms.manager: craigg
ms.reviewer: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: c1a23ebb390c2276d1ce47c2936b8fe682a4e9b7
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53213098"
---
# <a name="train-and-create-machine-learning-models-with-spark"></a>Former et créer des modèles d’apprentissage automatique avec Spark

Spark dans le cluster de données volumineux de SQL Server permet d’intelligence artificielle et l’apprentissage. L’exemple montre comment à la formation d’un modèle d’apprentissage à l’aide de Python dans Spark (PySpark) à l’aide des données stockées dans HDFS. 

L’exemple est un guide étape par étape avec les extraits de code qui peut être utilisé à partir d’un bloc-notes de Studio de données Azure et chaque étape d’une exécution de cellule à la fois. Pour plus d’informations sur la façon de se connecter avec Spark à partir de l’ordinateur portable reportez-vous [ici](notebooks-guidance.md)

Dans l’exemple :

1. Démarrer avec **comprendre les données et la prédiction souhaité**
2. **Charger les données dans HDFS et préparer les données** de création du modèle
3. **Sélectionner les fonctionnalités à utiliser**
4. **Fractionner les données en tant que jeu d’apprentissage et de test**
5. Rassemblé un **pipeline ml et un modèle de build**
6. Utiliser le modèle créé à **élaborer des prédictions**
7. Dans la dernière étape, **conserver le modèle créé ensuite d’utiliser**.

Apprentissage E2E implique plusieurs étapes supplémentaires, par exemple, l’exploration de données, fonctionnalité sélection et un principal du composant l’analyse, sélection d’un modèle. Nombre de ces étapes sont ignorés ici par souci de concision.

## <a name="step-1---understanding-the-data-and-prediction-desired"></a>Étape 1 : comprendre les données et la prédiction souhaité

Cet exemple utilise les données de revenu de recensement des adultes de [ici]( https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv ). Dans `AdultCensusIncome.csv`, chaque ligne représente la plage de revenus et autres caractéristiques telles que l’âge, hours-per-week, éducation, profession etc. pour un adulte donné. Générer un modèle capable de prédire si la plage de revenus. Le modèle prend l’âge et les heures par semaine, en tant que fonctionnalités et prédire si le revenu > 50 K ou < 50 K. 

## <a name="step-2---upload-the-data-to-hdfs-and-basic-explorations-on-data"></a>Étape 2 : charger les données dans HDFS et explorations de base de données
Se connecter à la passerelle HDFS/Spark à partir d’Azure Data Studio et créez un répertoire appelé `spark_ml` sous HDFS. Télécharger [AdultCensusIncome.csv]( https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv ) pour votre ordinateur local et le télécharger vers HDFS. Télécharger `AdultCensusIncome.csv` dans le dossier que vous avez créé.


À présent, écrire du code. Vous pouvez copier le code ci-dessous et collez-le dans les cellules individuelles d’un ordinateur portable dans Azure Data Studio. 

Le code ci-après lit le fichier CSV dans Spark data frame. Façon plus précise qui il compte le nombre de lignes et de colonnes et afficher les données chargées.

```python
datafile = "/spark_ml/AdultCensusIncome.csv"

#Read the data to a spark data frame.
data_all = spark.read.format('csv').options(header='true', inferSchema='true', ignoreLeadingWhiteSpace='true', ignoreTrailingWhiteSpace='true').load(datafile)
print("Number of rows: {},  Number of coulumns : {}".format(data_all.count(), len(data_all.columns)))

#Replace "-" with "_" in column names
columns_new = [col.replace("-", "_") for col in data_all.columns]
data_all = data_all.toDF(*columns_new)

#Print Schema and show top 5 row
data_all.printSchema() 
data_all.show(5)
```

## <a name="step-3---select-features-to-use"></a>Étape 3 : sélectionner les fonctionnalités à utiliser

Dans cette étape, utilisez ce qui suit deux termes
1. `Label`    -Fait référence à la valeur à prédire. Cela est représenté en tant que colonne dans les données.  
2. `Features` -Fait référence aux caractéristiques des données à prédire. Également appelée ultérieurement en tant que `predictors` 

Dans cet exemple `Label`, est la **income** colonne. Par souci de simplicité, choisissez **âge** et **hours_per_week** comme `Features`. En réalité les fonctionnalités sont choisies en appliquant quelques techniques de corrélation pour comprendre ce qui caractérisent mieux l’étiquette de prédiction.

```python
# Choose feature columns and the label column.
label = "income"
xvars = ["age", "hours_per_week"] #all numeric

print("label = {}".format(label))
print("features = {}".format(xvars))

select_cols = xvars
select_cols.append(label)
data = data_all.select(select_cols)

```

## <a name="step-4---split-as-training-and-test-set"></a>Étape 4 : fractionner en tant que jeu d’apprentissage et de test

Utiliser 75 % de lignes pour former le modèle et le reste de 25 % pour évaluer le modèle. En outre, conserver le train et tester des jeux de données pour le stockage HDFS. L’étape n’est pas nécessaire, mais il est affichée pour montrer l’enregistrement et le chargement avec le format ORC. Autres formats, par exemple, `Parquet `peut également être utilisé.

Validez cette étape, que vous devez voir deux répertoires créés avec le nom AdultCensusIncomeTrain et AdultCensusIncomeTest

```python

# Split data into train and test.
train, test = data.randomSplit([0.75, 0.25], seed=123)

print("train ({}, {})".format(train.count(), len(train.columns)))
print("test ({}, {})".format(test.count(), len(test.columns)))

train_data_path = "/spark_ml/AdultCensusIncomeTrain"
test_data_path = "/spark_ml/AdultCensusIncomeTest"

train.write.mode('overwrite').orc(train_data_path)
test.write.mode('overwrite').orc(test_data_path)
print("train and test datasets saved to {} and {}".format(train_data_path, test_data_path))

```

## <a name="step-5---put-together-a-pipeline-and-build-a-model"></a>Étape 5 : rassemblé un pipeline et générer un modèle
[Pipeline Spark ML](https://spark.apache.org/docs/2.3.1/ml-pipeline.html) autoriser pour toutes les étapes de séquence comme un flux de travail et le rendre plus facile à faire des essais avec différents algorithmes et leurs paramètres. Le code suivant construit d’abord les étapes et réunit ces étapes dans le pipeline de Ml.  LogisticRegression est utilisée pour créer le modèle.

```python
from pyspark.ml import Pipeline, PipelineModel
from pyspark.ml.feature import OneHotEncoder, StringIndexer, VectorAssembler
from pyspark.ml.classification import LogisticRegression

reg = 0.1
print("Using LogisticRegression model with Regularization Rate of {}.".format(reg))

# create a new Logistic Regression model.
lr = LogisticRegression(regParam=reg)

dtypes = dict(train.dtypes)
dtypes.pop(label)

si_xvars = []
ohe_xvars = []
featureCols = []
for idx,key in enumerate(dtypes):
    if dtypes[key] == "string":
        featureCol = "-".join([key, "encoded"])
        featureCols.append(featureCol)
        
        tmpCol = "-".join([key, "tmp"])
        si_xvars.append(StringIndexer(inputCol=key, outputCol=tmpCol, handleInvalid="skip")) #, handleInvalid="keep"
        ohe_xvars.append(OneHotEncoder(inputCol=tmpCol, outputCol=featureCol))
    else:
        featureCols.append(key)

# string-index the label column into a column named "label"
si_label = StringIndexer(inputCol=label, outputCol='label')

# assemble the encoded feature columns in to a column named "features"
assembler = VectorAssembler(inputCols=featureCols, outputCol="features")

```

À présent, rassemblé le pipeline. 

```python
# put together the pipeline
stages = []
stages.extend(si_xvars)
stages.extend(ohe_xvars)
stages.append(si_label)
stages.append(assembler)
stages.append(lr)
pipe = Pipeline(stages=stages)
print("Pipeline Created")

```

Maintenant que le pipeline est créé, l’utiliser pour former le modèle.

```python
# train the model
model = pipe.fit(train)
print("Model Trained")
print("Model is ", model)
print("Model Stages", model.stages)

```

## <a name="step-6---predict-using-the-model-and-evaluate-the-model-accuracy"></a>Étape 6 : prédiction à l’aide du modèle et évaluer la précision du modèle
Le code ci-dessous utilise le jeu de données de test pour prédire le résultat à l’aide du modèle créé à l’étape précédente. Il mesure la précision du modèle avec `areaUnderROC` et `areaUnderPR` métrique.

```python
from pyspark.ml.evaluation import BinaryClassificationEvaluator
# make prediction
pred = model.transform(test)

# evaluate. note only 2 metrics are supported out of the box by Spark ML.
bce = BinaryClassificationEvaluator(rawPredictionCol='rawPrediction')
au_roc = bce.setMetricName('areaUnderROC').evaluate(pred)
au_prc = bce.setMetricName('areaUnderPR').evaluate(pred)

print("Area under ROC: {}".format(au_roc))
print("Area Under PR: {}".format(au_prc))
```


## <a name="step-7---persist-the-models-to-hdfs"></a>Étape 7 : conserver les modèles à HDFS
Enfin, conserver le modèle dans HDFS pour une utilisation ultérieure. Après cette étape le modèle créé enregistré en tant que /spark_ml/AdultCensus.mml

```python
##NOTE: by default the model is saved to and loaded from path

model_name = "AdultCensus.mml"
model_fs = "/spark_ml/" + model_name

model.write().overwrite().save(model_fs)
print("saved model to {}".format(model_fs))

# load the model file (from dbfs)
model2 = PipelineModel.load(model_fs)
assert str(model2) == str(model)
print("loaded model from {}".format(model_fs))
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la prise en main avec les blocs-notes PySpark, consultez [l’utilisation de blocs-notes](notebooks-guidance.md).