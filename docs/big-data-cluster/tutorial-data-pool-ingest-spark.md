---
title: Ingérer des données avec des travaux Spark
titleSuffix: SQL Server big data clusters
description: Ce didacticiel montre comment ingérer des données dans le pool de données d’un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] à l’aide de travaux Spark dans Azure Data Studio.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5ffc2773144d2b1a170e2f087d7abf607af99ef6
ms.sourcegitcommit: 4fb6bc7c81a692a2df706df063d36afad42816af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73049861"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>Didacticiel : réception de données dans un pool de données SQL Server avec des travaux Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce didacticiel montre comment utiliser des travaux Spark pour charger des données dans le [pool de données](concept-data-pool.md) d’un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. 

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
> * Créer une table externe dans le pool de données
> * Créer un travail Spark pour charger des données à partir de HDFS
> * Interroger les résultats d’une table externe

> [!TIP]
> Si vous préférez, vous pouvez télécharger et exécuter un script pour les commandes de ce tutoriel. Pour obtenir des instructions, consultez les [exemples de pools de données](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) sur GitHub.

## <a id="prereqs"></a> Prérequis

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
   USE Sales
   GO
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

L’étape suivante consiste à créer un travail de streaming Spark afin de charger des données de parcours web issues du pool de stockage (HDFS) dans la table externe que vous avez créée dans le pool de données. Ces données ont été ajoutées à/clickstream_data dans [charger des exemples de données dans votre cluster Big Data](tutorial-load-sample-data.md).

1. Dans Azure Data Studio, connectez-vous à l’instance maître de votre cluster Big Data. Pour plus d’informations, consultez [Se connecter à un cluster Big Data](connect-to-big-data-cluster.md).

2. Créer un nouveau bloc-notes et sélectionner Spark | Scala comme noyau.

3. Exécuter le travail d’ingestion Spark
   1. Configurer les paramètres du connecteur Spark-SQL
      ```
      import org.apache.spark.sql.types._
      import org.apache.spark.sql.{SparkSession, SaveMode, Row, DataFrame}

      // Change per your installation
      val user= "username"
      val password= "****"
      val database =  "MyTestDatabase"
      val sourceDir = "/clickstream_data"
      val datapool_table = "web_clickstreams_spark_results"
      val datasource_name = "SqlDataPool"
      val schema = StructType(Seq(
      StructField("wcs_click_date_sk",IntegerType,true), StructField("wcs_click_time_sk",IntegerType,true), StructField("wcs_sales_sk",IntegerType,true), StructField("wcs_item_sk",IntegerType,true), 
      StructField("wcs_web_page_sk",IntegerType,true), StructField("wcs_user_sk",IntegerType,true)
      ))

      val hostname = "master-0.master-svc"
      val port = 1433
      val url = s"jdbc:sqlserver://${hostname}:${port};database=${database};user=${user};password=${password};"
      ```
   2. Définir et exécuter le travail Spark
      * Chaque travail se compose de deux parties : readStream et writeStream. Ci-dessous, nous créons une trame de données à l’aide du schéma défini ci-dessus, puis nous écrivons dans la table externe du pool de données.
      ```
      import org.apache.spark.sql.{SparkSession, SaveMode, Row, DataFrame}
      
      val df = spark.readStream.format("csv").schema(schema).option("header", true).load(sourceDir)
      val query = df.writeStream.outputMode("append").foreachBatch{ (batchDF: DataFrame, batchId: Long) => 
                batchDF.write
                 .format("com.microsoft.sqlserver.jdbc.spark")
                 .mode("append")
                  .option("url", url)
                  .option("dbtable", datapool_table)
                  .option("user", user)
                  .option("password", password)
                  .option("dataPoolDataSource",datasource_name).save()
               }.start()

      query.processAllAvailable()
      query.awaitTermination(40000)
      ```
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
1. Les données peuvent également être interrogées dans Spark. Par exemple, le code ci-dessous affiche le nombre d’enregistrements dans la table :
   ```
   def df_read(dbtable: String,
                url: String,
                dataPoolDataSource: String=""): DataFrame = {
        spark.read
             .format("com.microsoft.sqlserver.jdbc.spark")
             .option("url", url)
             .option("dbtable", dbtable)
             .option("user", user)
             .option("password", password)
             .option("dataPoolDataSource", dataPoolDataSource)
             .load()
             }

   val new_df = df_read(datapool_table, url, dataPoolDataSource=datasource_name)
   println("Number of rows is " +  new_df.count)
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
