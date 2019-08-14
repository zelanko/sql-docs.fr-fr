---
title: Ingérer des données avec des travaux Spark
titleSuffix: SQL Server big data clusters
description: Ce tutoriel montre comment ingérer des données dans le pool de données d’un cluster Big Data SQL Server 2019 (préversion) à l’aide de travaux Spark dans Azure Data Studio.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
ms.date: 06/26/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6d0ea6d4fb7a3aea9788c089ad68cb3bf523837f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67957813"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>Tutoriel : Ingérer des données dans un pool de données SQL Server avec des travaux Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce tutoriel montre comment utiliser des travaux Spark pour charger des données dans le [pool de données](concept-data-pool.md) d’un cluster Big Data SQL Server 2019 (préversion). 

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
> * Créer une table externe dans le pool de données
> * Créer un travail Spark pour charger des données à partir de HDFS
> * Interroger les résultats d’une table externe

> [!TIP]
> Si vous préférez, vous pouvez télécharger et exécuter un script pour les commandes de ce tutoriel. Pour obtenir des instructions, consultez les [exemples de pools de données](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) sur GitHub.

## <a id="prereqs"></a> Conditions préalables

- [Outils Big Data](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Extension SQL Server 2019**
- [Charger des exemples de données dans votre cluster Big Data](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Créer une table externe dans le pool de données

Les étapes suivantes permettent de créer une table externe nommée **web_clickstreams_spark_results** dans le pool de données. Cette table peut ensuite être utilisée en tant qu’emplacement d’ingestion des données dans le cluster Big Data.

1. Dans Azure Data Studio, connectez-vous à l’instance maître SQL Server de votre cluster Big Data. Pour plus d’informations, consultez [Se connecter à l’instance maître SQL Server](connect-to-big-data-cluster.md#master).

1. Double-cliquez sur la connexion dans la fenêtre **Serveurs** pour afficher le tableau de bord de serveur de l’instance maître SQL Server. Sélectionnez **Nouvelle requête**.

   ![Requête d’instance maître SQL Server](./media/tutorial-data-pool-ingest-spark/sql-server-master-instance-query.png)

1. Créez une source de données externe dans le pool de données, si elle n’existe pas déjà.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://controller-svc/default');
   ```

1. Créez une table externe nommée **web_clickstreams_spark_results** dans le pool de données.

   ```sql
   USE Sales
   GO
   IF NOT EXISTS(SELECT * FROM sys.external_tables WHERE name = 'web_clickstreams_spark_results')
      CREATE EXTERNAL TABLE [web_clickstreams_spark_results]
      ("wcs_click_date_sk" BIGINT , "wcs_click_time_sk" BIGINT , "wcs_sales_sk" BIGINT , "wcs_item_sk" BIGINT , "wcs_web_page_sk" BIGINT , "wcs_user_sk" BIGINT)
      WITH
      (
         DATA_SOURCE = SqlDataPool,
         DISTRIBUTION = ROUND_ROBIN
      );
   ```
  
1. Dans la version CTP 3.1, la création du pool de données est asynchrone. Toutefois, il n’existe aucun moyen de déterminer quand l’opération a été effectuée. Attendez deux minutes pour vérifier que le pool de données a bien été créé avant de continuer.

## <a name="start-a-spark-streaming-job"></a>Démarrer un travail de streaming Spark

L’étape suivante consiste à créer un travail de streaming Spark afin de charger des données de parcours web issues du pool de stockage (HDFS) dans la table externe que vous avez créée dans le pool de données.

1. Dans Azure Data Studio, connectez-vous à l’instance maître de votre cluster Big Data. Pour plus d’informations, consultez [Se connecter à un cluster de Big Data](connect-to-big-data-cluster.md).

1. Double-cliquez sur la connexion de passerelle HDFS/Spark dans la fenêtre **Serveurs**. Ensuite, sélectionnez **New Spark Job** (Nouveau travail Spark).

   ![Nouveau travail Spark](media/tutorial-data-pool-ingest-spark/hdfs-new-spark-job.png)

1. Dans la fenêtre **New Job** (Nouveau travail), entrez un nom dans le champ **Job name** (Nom du travail).

1. Dans la liste déroulante **Jar/py File** (Fichier jar/py), sélectionnez **HDFS**. Entrez ensuite le chemin du fichier jar suivant :

   ```text
   /jar/mssql-spark-lib-assembly-1.0.jar
   ```

1. Dans le champ **Main Class** (Classe principale), entrez `FileStreaming`.

1. Dans le champ **Arguments**, entrez le texte suivant, en spécifiant le mot de passe de l’instance maître SQL Server dans l’espace réservé `<your_password>`. 

   ```text
   --server mssql-master-pool-0.service-master-pool --port 1433 --user sa --password <your_password> --database sales --table web_clickstreams_spark_results --source_dir hdfs:///clickstream_data --input_format csv --enable_checkpoint false --timeout 380000
   ```

   La table ci-dessous décrit chaque argument :

   | Argument | Description |
   |---|---|
   | nom de serveur | Utilisé par SQL Server pour lire le schéma de la table |
   | Numéro de port | Le port via lequel SQL Server écoute (par défaut, 1433) |
   | username | Nom d’utilisateur du compte de connexion SQL Server |
   | password | Mot de passe du compte de connexion SQL Server |
   | nom de la base de données | Base de données cible |
   | Nom de la table externe | Table à utiliser pour les résultats |
   | Répertoire source pour le streaming | Il doit s’agir d’un URI complet, tel que « hdfs:///clickstream_data ». |
   | Format d’entrée | Il peut s’agir du format .csv, .parquet ou .json. |
   | Activer le point de contrôle | True ou False |
   | délai d'expiration | Durée d’exécution du travail (en millisecondes) avant fermeture |

1. Appuyez sur **Submit** pour envoyer le travail.

   ![Envoi d’un travail Spark](media/tutorial-data-pool-ingest-spark/spark-new-job-settings.png)

## <a name="query-the-data"></a>Interroger les données

Les étapes suivantes montrent que le travail de streaming Spark a chargé les données HDFS dans le pool de données.

1. Avant d’interroger les données ingérées, consultez l’historique des tâches pour vérifier que le travail est bien terminé.

   ![Historique des travaux Spark](media/tutorial-data-pool-ingest-spark/spark-task-history.png)

1. Revenez à la fenêtre de la requête de l’instance maître SQL Server que vous avez ouverte au début de ce tutoriel.

1. Exécutez la requête suivante pour vérifier les données ingérées.

   ```sql
   USE Sales
   GO
   SELECT count(*) FROM [web_clickstreams_spark_results];
   SELECT TOP 10 * FROM [web_clickstreams_spark_results];
   ```

## <a name="clean-up"></a>Nettoyer

Utilisez la commande suivante pour supprimer les objets de base de données créés dans ce tutoriel.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_spark_results];
```

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur l’exécution d’un exemple de notebook dans Azure Data Studio :
> [!div class="nextstepaction"]
> [Exécuter un exemple de notebook](tutorial-notebook-spark.md)
