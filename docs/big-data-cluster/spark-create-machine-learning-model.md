---
title: Créer et exporter des modèles avec MLeap d’apprentissage Spark
titleSuffix: SQL Server big data clusters
description: Utiliser PySpark pour former et créer des modèles d’apprentissage automatique avec Spark sur des clusters de données volumineuses de SQL Server (version préliminaire). Exporter avec MLeap et puis noter le modèle avec Java dans SQL Server.
author: lgongmsft
ms.author: lgong
ms.reviewer: mikeray
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: aa4c31eca725e8e662937259f078cf00a3441915
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727378"
---
# <a name="create-export-and-score-spark-machine-learning-models-on-sql-server-big-data-clusters"></a>Créer, exporter et noter les modèles d’apprentissage automatique Spark sur des clusters de données volumineuses de SQL Server

L’exemple suivant montre comment créer un modèle avec [Spark ML](https://spark.apache.org/docs/latest/ml-guide.html), exporter le modèle à [MLeap](http://mleap-docs.combust.ml/)et noter le modèle dans SQL Server avec sa [Extension de langage Java](../language-extensions/language-extensions-overview.md). Pour cela, dans le contexte d’un cluster de données volumineuses de SQL Server 2019.

Le diagramme suivant illustre le travail effectué dans cet exemple :

![Exportation de score de former avec spark](./media/spark-create-machine-learning-model/train-score-export-with-spark.png)

## <a name="prerequisites"></a>Prérequis

Tous les fichiers de cet exemple sont situés à [ https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml ](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml).

Pour exécuter l’exemple, vous devez également les conditions préalables suivantes :

- Un [cluster de données volumineux de SQL Server](deploy-get-started.md)

- [Outils de données volumineuses](deploy-big-data-tools.md)
   - **kubectl**
   - **curl**
   - **Azure Data Studio**

## <a name="model-training-with-spark-ml"></a>Apprentissage du modèle avec Spark ML

Pour cet exemple, les données de recensement (**AdultCensusIncome.csv**) est utilisé pour générer un modèle de pipeline Spark ML.

1. Utilisez le [mleap_sql_test/setup.sh](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/setup.sh) fichier à télécharger le jeu de données à partir d’internet et le placer sur HDFS dans votre cluster de données volumineux de SQL Server. Cela lui permet d’être accessibles par Spark.

1. Puis téléchargez l’exemple de notebook [train_score_export_ml_models_with_spark.ipynb](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb). À partir d’une ligne de commande PowerShell ou bash, exécutez la commande suivante pour télécharger le bloc-notes :

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb"
   ```

   Ce notebook contient des cellules avec les commandes requises pour cette section de l’exemple.

1. Ouvrez le bloc-notes dans Azure Data Studio et exécuter chaque bloc de code. Pour plus d’informations sur l’utilisation des blocs-notes, consultez [comment utiliser des blocs-notes en version préliminaire de SQL Server 2019](notebooks-guidance.md).

Les données sont tout d’abord lire dans Spark et fractionner en apprentissage et jeux de données de test. Puis le code effectue l’apprentissage d’un modèle de pipeline avec les données d’apprentissage. Enfin, elle exporte le modèle à une offre groupée MLeap.

> [!TIP]
> Vous pouvez également vérifier ou exécuter le code Python avec ces étapes en dehors de l’ordinateur portable dans le [mleap_sql_test/mleap_pyspark.py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_pyspark.py) fichier.

## <a name="model-scoring-with-sql-server"></a>Modèle de notation avec SQL Server

Maintenant que le modèle de pipeline Spark ML est dans une sérialisation courants [MLeap bundle](http://mleap-docs.combust.ml/core-concepts/mleap-bundles.html) format, vous pouvez noter le modèle dans Java sans la présence de Spark. 

Cet exemple utilise le [Extension de langage Java](../language-extensions/language-extensions-overview.md) dans SQL Server. Pour noter le modèle dans SQL Server, vous devez d’abord créer une application Java qui peut charger le modèle dans Java et noter. Vous trouverez l’exemple de code pour cette application Java dans le [dossier mssql-mleap-application](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mssql-mleap-app).

Après avoir généré l’exemple, vous pouvez utiliser Transact-SQL pour appeler l’application Java et évaluer le modèle avec une table de base de données. Ceci peut être observé dans trois [mleap_sql_test/mleap_sql_tests.py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_sql_tests.py) fichier source.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses, consultez [comment déployer des données volumineuses de SQL Server clusters sur Kubernetes](deployment-guidance.md)
