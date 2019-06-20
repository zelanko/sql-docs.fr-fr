---
title: Exporter des modèles de Spark ML avec MLeap
titleSuffix: SQL Server big data clusters
description: Découvrez comment exporter des modèles avec MLeap d’apprentissage Spark.
author: lgongmsft
ms.author: lgong
ms.reviewer: jroth
manager: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: e831345e82310b51e5802af70c91b0d397e66c90
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822457"
---
# <a name="export-spark-machine-learning-models-with-mleap"></a>Exporter des modèles avec MLeap d’apprentissage Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Un scénario d’apprentissage classique implique l’apprentissage du modèle sur Spark et la notation en dehors de Spark. Exporter des modèles dans un format portable où il peut être utilisé en dehors de Spark. [MLeap](https://github.com/combust/mleap) est un format d’échange de ce modèle. Il permet à Spark pipelines d’apprentissage et de modèles à exporter en tant que formats portables et utilisé dans n’importe quel système de JVM avec le `Mleap` runtime.

Ce guide explique comment vous pouvez exporter vos modèles de spark à l’aide de Mleap. Les étapes sont résumées ci-dessous et détaillés avec du code dans la section suivante.

1. Commencez par créer un modèle de Spark. Pour cette utilisation **d’apprentissage et de création d’apprentissage de modèle avec Spark [ici.](train-and-create-machinelearning-models-with-spark.md)**
2. Ensuite, nous allons **importer les données training\test et le modèle**
3. **Exporter le modèle en tant que `Mleap` bundle**. Cette offre groupée exportée est désormais utilisable pour la notation en dehors de spark.
4. Pour valider, nous allons importer le `Mleap` regrouper arrière à nouveau et l’utiliser pour la notation dans Spark.

## <a name="step-1---start-by-creating-a-spark-model"></a>Étape 1 : démarrer en créant un modèle Spark
Exécutez [d’apprentissage et de création d’apprentissage de modèle avec Spark](train-and-create-machinelearning-models-with-spark.md) pour créer des ensembles de formation/test et de modèle et rendre persistantes dans le stockage HDFS. Le modèle doit être exporté en tant que `AdultCensus.mml` sous le `spark_ml` directory.

## <a name="step-2---import-the-trainingtest-data-and-the-model"></a>Étape 2 : importer les données training\test et le modèle

Étape 1 créé le `AdultCensus.mml`, qui est un modèle spark. 

Dans cette étape, importez le modèle de spark.

```python
import mleap.pyspark
from mleap.pyspark.spark_support import SimpleSparkSerializer
from pyspark.ml import PipelineModel

model_name = "AdultCensus.mml"
model_fs = "/spark_ml/" + model_name

print("load pyspark model from hbfs")
model = PipelineModel.load(model_fs)
print("Model is " , model)
print("Model stages", model.stages)
```

## <a name="step-3---export-the-model-as-mleap-bundle"></a>Étape 3 : exporter le modèle en tant que `Mleap` bundle

Exporter le modèle Spark en tant qu’un portable `Mleap` de modèle et le rendre persistant dans le stockage local. Validez cette étape, le modèle est disponible dans un ordinateur portable `Mleap` mettre en forme et peut être utilisé en dehors de Spark.

```python
import os

#Get the train and test datasets

# Write the train and test data sets to intermediate storage

train_data_path = "/spark_ml/AdultCensusIncomeTrain"
test_data_path = "/spark_ml/AdultCensusIncomeTest"

train = spark.read.orc(train_data_path)
test = spark.read.orc(test_data_path)

print("train: ({}, {})".format(train.count(), len(train.columns)))
train.printSchema()

print("test: ({}, {})".format(test.count(), len(test.columns)))
test.printSchema()

# serialize the model to a zip file in JSON format
model_name_export = "adult_census_pipeline.zip"
model_name_path = os.getcwd()
model_file = os.path.join(model_name_path, model_name_export)

# serialize the model to a zip file in JSON format
model_name_export = "adult_census_pipeline.zip"
model_name_path = os.getcwd()
model_file = os.path.join(model_name_path, model_name_export)

# remove an old model file, if needed.
try:
    os.remove(model_file)
except OSError:
    pass

model_file_path = "jar:file:{}".format(model_file)
model.serializeToBundle(model_file_path, model.transform(train))

```

Conserver le `Mleap` regroupement depuis le système local à hdfs

```python
print("persist the mleap bundle from local to hdfs")
from subprocess import Popen, PIPE
proc = Popen(["hadoop", "fs", "-put", "-f", model_file, os.path.join("/spark_ml", model_name_export)], stdout=PIPE, stderr=PIPE)
s_output, s_err = proc.communicate()
if(s_err):
    print("Error when storing to HDFS")
```

## <a name="step-3---validate-by-importing-the-mleap-bundle-and-scoring-in-spark"></a>Étape 3 : valider à l’importation du `Mleap` bundle et score dans Spark
À l’étape 2, nous avons déjà le modèle exporté pour un ordinateur portable `Mleap` format qui peut être utilisé en dehors de Spark. Dans cette étape, nous importons le `Mleap` sérialisé dans Spark et utilisez-la dans Spark Score sur le jeu de test.
   
```python
model_deserialized = PipelineModel.deserializeFromBundle(model_file_path)
print("The deserialized model is ", model_deserialized)
print("The deserialized model stages are", model_deserialized.stages)

from pyspark.ml.evaluation import BinaryClassificationEvaluator

# make prediction
pred = model_deserialized.transform(test)


# evaluate. note only 2 metrics are supported out of the box by Spark ML.
bce = BinaryClassificationEvaluator(rawPredictionCol='rawPrediction')
au_roc = bce.setMetricName('areaUnderROC').evaluate(pred)
au_prc = bce.setMetricName('areaUnderPR').evaluate(pred)

print("Results of using the model score test set")
print("Area under ROC: {}".format(au_roc))
print("Area Under PR: {}".format(au_prc))
```

## <a name="references"></a>References

* [Mise en route avec les blocs-notes PySpark](notebooks-guidance.md)
* [Apprentissage et de création de modèle d’apprentissage automatique avec Spark](train-and-create-machinelearning-models-with-spark.md)
