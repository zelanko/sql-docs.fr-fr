---
title: Comment recevoir des données dans un pool de données SQL Server avec des travaux Spark | Microsoft Docs
description: Ce didacticiel montre comment recevoir des données dans le pool de données d’un cluster de données volumineuses de SQL Server 2019 (version préliminaire) à l’aide de travaux Spark dans Azure Data Studio.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/16/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: d4ee9037e1762f11a569c94e416fcf5e45449d46
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644192"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>Didacticiel : Recevoir des données dans un pool de données SQL Server avec des travaux Spark

Ce didacticiel montre comment utiliser des travaux Spark pour charger des données dans le [pool de données](concept-data-pool.md) d’un cluster de données volumineuses de SQL Server 2019 (version préliminaire). 

Dans ce didacticiel, vous allez découvrir comment :

> [!div class="checklist"]
> * Créer une table externe dans le pool de données.
> * Créer un travail Spark pour charger des données à partir de HDFS.
> * Interroger les résultats dans la table externe.

> [!TIP]
> Si vous préférez, vous pouvez télécharger et exécuter un script pour les commandes de ce didacticiel. Pour obtenir des instructions, consultez le [pools de données exemples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) sur GitHub.

## <a id="prereqs"></a> Conditions préalables

* [Déployer un cluster de données volumineuses sur Kubernetes](deployment-guidance.md).
* [Installer Azure Data Studio et l’extension de SQL Server 2019](deploy-big-data-tools.md).
* [Charger des exemples de données dans le cluster](#sampledata).

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-external-table-in-the-data-pool"></a>Créer une table externe dans le pool de données

Les étapes suivantes créent une table externe dans le pool de données nommé **web_clickstreams_spark_results**. Cette table peut ensuite servir en tant qu’emplacement de réception des données dans le cluster de données volumineuses.

1. Dans Azure Data Studio, connectez-vous à l’instance principale de SQL Server de votre cluster big data. Pour plus d’informations, consultez [se connecter à l’instance principale de SQL Server](deploy-big-data-tools.md#master).

1. Double-cliquez sur la connexion dans le **serveurs** fenêtre pour afficher le tableau de bord du serveur pour l’instance principale de SQL Server. Sélectionnez **nouvelle requête**.

   ![Requête d’instance principale de SQL Server](./media/tutorial-data-pool-ingest-spark/sql-server-master-instance-query.png)

1. Créer une table externe nommée **web_clickstreams_spark_results** dans le pool de données. Le `SqlDataPool` source de données est un type de source de données spécial qui peut être utilisé à partir de l’instance principale de n’importe quel cluster big data.

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
  
1. Dans CTP 2.0, la création du pool de données est asynchrone, mais il n’existe aucun moyen de déterminer quand il se termine encore. Veuillez patienter deux minutes pour vous assurer que le pool de données est créé avant de continuer.

## <a name="start-a-spark-streaming-job"></a>Démarrer un travail de diffusion en continu de Spark

L’étape suivante consiste à créer un travail qui charge les données de parcours web du pool de stockage (HDFS) de diffusion en continu de Spark dans la table externe que vous avez créé dans le pool de données.

1. Dans Azure Data Studio, connectez-vous à la passerelle HDFS/Spark de votre cluster big data. Pour plus d’informations, consultez [se connecter à la passerelle HDFS/Spark](deploy-big-data-tools.md#hdfs).

1. Double-cliquez sur la connexion de passerelle HDFS/Spark dans le **serveurs** fenêtre. Puis sélectionnez **nouveau travail Spark**.

   ![Nouveau travail Spark](media/tutorial-data-pool-ingest-spark/hdfs-new-spark-job.png)

1. Dans le **nouveau travail** fenêtre, entrez un nom dans la **nom de la tâche** champ.

1. Dans le **les fichiers Jar/py** liste déroulante, sélectionnez **HDFS**. Puis entrez le chemin d’accès de fichier jar suivantes :

   ```text
   /jar/mssql-spark-lib-assembly-1.0.jar
   ```

1. Dans le **Arguments** , entrez le texte suivant, en spécifiant le mot de passe à l’instance principale de SQL Server dans le `<your_password>` espace réservé. 

   ```text
   mssql-master-pool-0.service-master-pool 1433 sa <your_password> sales web_clickstreams_spark_results hdfs:///clickstream_data csv false
   ```

   Le tableau suivant décrit chaque argument :

   | Argument | Description |
   |---|---|
   | nom de serveur | Utilisation de SQL Server pour la lecture du schéma de table |
   | Numéro de port | Port SQL Server écoute (1433 par défaut) |
   | username | Nom d’utilisateur SQL Server |
   | password | Mot de passe de connexion SQL Server |
   | nom de la base de données | Base de données cible |
   | nom de la table externe | Table à utiliser pour les résultats |
   | Répertoire source pour la diffusion en continu | Cela doit être un URI complet, tel que « hdfs : / / / clickstream_data » |
   | format d’entrée | Cela peut être « csv », « parquet » ou « json » |
   | Activer le point de contrôle | True ou False |

1. Appuyez sur **Submit** pour envoyer la tâche.

   ![Envoyer des travaux Spark](media/tutorial-data-pool-ingest-spark/spark-new-job-settings.png)

## <a name="query-the-data"></a>Interroger les données

Les étapes suivantes montrent que le travail de diffusion en continu Spark chargé les données à partir de HDFS dans le pool de données.

1. Avant d’interroger les données ingérées, examinez la sortie de l’historique de tâche pour voir que la tâche est terminée.

   ![Historique des travaux de Spark](media/tutorial-data-pool-ingest-spark/spark-task-history.png)

1. Revenez à la fenêtre de requête d’instance principale de SQL Server que vous avez ouvert au début de ce didacticiel...

1. Exécutez la requête suivante pour examiner les données ingérées.

   ```sql
   USE Sales
   GO
   SELECT count(*) FROM [web_clickstreams_spark_results];
   SELECT TOP 10 * FROM [web_clickstreams_spark_results];
   ```

## <a name="clean-up"></a>Nettoyer

Utilisez la commande suivante pour supprimer les objets de base de données créés dans ce didacticiel.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_spark_results];
```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment exécuter un exemple de notebook dans Azure Data Studio :
> [!div class="nextstepaction"]
> [Exécuter un exemple de notebook](tutorial-notebook-spark.md)
