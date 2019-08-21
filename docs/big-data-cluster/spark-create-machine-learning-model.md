---
title: Créer et exporter des modèles de Machine Learning Spark avec MLeap
titleSuffix: SQL Server big data clusters
description: Utilisez PySpark pour former et créer machine learning des modèles avec Spark [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] on (version préliminaire). Exportez avec MLeap, puis marquez le modèle avec Java dans SQL Server.
author: RogPodge
ms.author: roliu
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bba570a4ac68cf5a4d1405d4152669ed9ed211a0
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653414"
---
# <a name="create-export-and-score-spark-machine-learning-models-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Créer, exporter et noter les modèles Spark Machine Learning sur[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

L’exemple suivant montre comment générer un modèle avec [Spark ml](https://spark.apache.org/docs/latest/ml-guide.html), exporter le modèle vers [MLeap](http://mleap-docs.combust.ml/)et noter le modèle dans SQL Server avec son extension de [langage Java](../language-extensions/language-extensions-overview.md). Cela s’effectue dans le contexte d’un cluster SQL Server 2019 Big Data.

Le diagramme suivant illustre le travail effectué dans cet exemple:

![Former l’exportation du score avec Spark](./media/spark-create-machine-learning-model/train-score-export-with-spark.png)

## <a name="prerequisites"></a>Prérequis

Tous les fichiers de cet exemple se trouvent [https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml)dans.

Pour exécuter l’exemple, vous devez également disposer des éléments suivants:

- Un [cluster SQL Server Big Data](deploy-get-started.md)

- [Outils Big Data](deploy-big-data-tools.md)
   - **kubectl**
   - **curl**
   - **Azure Data Studio**

## <a name="model-training-with-spark-ml"></a>Apprentissage de modèle avec Spark ML

Pour cet exemple, les données de recensement (**AdultCensusIncome. csv**) sont utilisées pour générer un modèle de pipeline Spark ml.

1. Utilisez le fichier [mleap_sql_test/Setup. sh](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/setup.sh) pour télécharger le jeu de données à partir d’Internet et le placer sur HDFS dans votre cluster SQL Server Big Data. Cela lui permet d’accéder à Spark.

1. Téléchargez ensuite l’exemple de bloc-notes [train_score_export_ml_models_with_spark. ipynb](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb). À partir d’une ligne de commande PowerShell ou bash, exécutez la commande suivante pour télécharger le bloc-notes:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb"
   ```

   Ce bloc-notes contient des cellules avec les commandes requises pour cette section de l’exemple.

1. Ouvrez le bloc-notes dans Azure Data Studio et exécutez chaque bloc de code. Pour plus d’informations sur l’utilisation des notebooks, consultez [Guide pratique pour utiliser des notebooks dans SQL Server 2019 en préversion](notebooks-guidance.md).

Les données sont d’abord lues dans Spark et sont divisées en jeux de données d’apprentissage et de test. Ensuite, le code forme un modèle de pipeline avec les données d’apprentissage. Enfin, il exporte le modèle vers un bundle MLeap.

> [!TIP]
> Vous pouvez également consulter ou exécuter le code python associé à ces étapes en dehors du bloc-notes dans le fichier [mleap_sql_test/mleap_pyspark. py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/mleap_pyspark.py) .

## <a name="model-scoring-with-sql-server"></a>Notation de modèle avec SQL Server

Maintenant que le modèle de pipeline Spark ML est dans un format de [Bundle MLeap](http://mleap-docs.combust.ml/core-concepts/mleap-bundles.html) de sérialisation courant, vous pouvez noter le modèle en Java sans la présence de Spark. 

Cet exemple utilise l' [extension de langage Java](../language-extensions/language-extensions-overview.md) dans SQL Server. Pour noter le modèle dans SQL Server, vous devez d’abord créer une application Java qui peut charger le modèle dans Java et la noter. Vous pouvez trouver l’exemple de code pour cette application Java dans le [dossier MSSQL-mleap-App](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mssql-mleap-app).

Après avoir généré l’exemple, vous pouvez utiliser Transact-SQL pour appeler l’application Java et noter le modèle avec une table de base de données. Cela peut être observé dans le fichier source [mleap_sql_test/mleap_sql_tests. py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/mleap_sql_tests.py) .

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [comment [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] déployer sur Kubernetes](deployment-guidance.md)
