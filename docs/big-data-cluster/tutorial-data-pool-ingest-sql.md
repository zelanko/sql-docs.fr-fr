---
title: Ingérer des données dans un pool de données SQL Server
titleSuffix: SQL Server big data clusters
description: Ce tutoriel montre comment ingérer des données dans le pool de données d’un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f2ae96a04da69835b4b13886637cf87e62996b57
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653310"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-transact-sql"></a>Tutoriel : Ingérer des données dans un pool de données SQL Server avec Transact-SQL

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce tutoriel montre comment utiliser Transact-SQL pour charger des données dans le [pool de données](concept-data-pool.md) d’un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Avec [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], vous pouvez ingérer et distribuer les données de différentes sources parmi des instances de pool de données.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
> * Créer une table externe dans le pool de données
> * Insérer des exemples de données de parcours web dans la table de pool de données
> * Joindre les données de la table de pool de données à des tables locales

> [!TIP]
> Si vous préférez, vous pouvez télécharger et exécuter un script pour les commandes de ce tutoriel. Pour obtenir des instructions, consultez les [exemples de pools de données](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) sur GitHub.

## <a id="prereqs"></a> Conditions préalables

- [Outils Big Data](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Extension SQL Server 2019**
- [Charger des exemples de données dans votre cluster Big Data](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Créer une table externe dans le pool de données

Les étapes suivantes permettent de créer une table externe nommée **web_clickstream_clicks_data_pool** dans le pool de données. Cette table peut ensuite être utilisée en tant qu’emplacement d’ingestion des données dans le cluster Big Data.

1. Dans Azure Data Studio, connectez-vous à l’instance maître SQL Server de votre cluster Big Data. Pour plus d’informations, consultez [Se connecter à l’instance maître SQL Server](connect-to-big-data-cluster.md#master).

1. Double-cliquez sur la connexion dans la fenêtre **Serveurs** pour afficher le tableau de bord de serveur de l’instance maître SQL Server. Sélectionnez **Nouvelle requête**.

   ![Requête d’instance maître SQL Server](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. Exécutez la commande Transact-SQL suivante pour remplacer le contexte par celui de la base de données **Sales** dans l’instance maître.

   ```sql
   USE Sales
   GO
   ```

1. Créez une source de données externe dans le pool de données, si elle n’existe pas déjà.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://controller-svc/default');
   ```

1. Créez une table externe nommée **web_clickstream_clicks_data_pool** dans le pool de données.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_tables WHERE name = 'web_clickstream_clicks_data_pool')
      CREATE EXTERNAL TABLE [web_clickstream_clicks_data_pool]
      ("wcs_user_sk" BIGINT , "i_category_id" BIGINT , "clicks" BIGINT)
      WITH
      (
         DATA_SOURCE = SqlDataPool,
         DISTRIBUTION = ROUND_ROBIN
      );
   ```
  
1. Dans la version CTP 3.1, la création du pool de données est asynchrone. Toutefois, il n’existe aucun moyen de déterminer quand l’opération a été effectuée. Attendez deux minutes pour vérifier que le pool de données a bien été créé avant de continuer.

## <a name="load-data"></a>Charger les données

Les étapes suivantes permettent d’ingérer des exemples de données de parcours web dans le pool de données à l’aide de la table externe créée au cours des étapes précédentes.

1. Utilisez une instruction `INSERT INTO` pour insérer les résultats de la requête dans le pool de données (table externe **web_clickstream_clicks_data_pool**).

   ```sql
   INSERT INTO web_clickstream_clicks_data_pool
   SELECT wcs_user_sk, i_category_id, COUNT_BIG(*) as clicks
     FROM sales.dbo.web_clickstreams_hdfs
   INNER JOIN sales.dbo.item it ON (wcs_item_sk = i_item_sk
                           AND wcs_user_sk IS NOT NULL)
   GROUP BY wcs_user_sk, i_category_id
   HAVING COUNT_BIG(*) > 100;
   ```

1. Inspectez les données insérées à l’aide de deux requêtes SELECT.

   ```sql
   SELECT count(*) FROM [dbo].[web_clickstream_clicks_data_pool]
   SELECT TOP 10 * FROM [dbo].[web_clickstream_clicks_data_pool]  
   ```

## <a name="query-the-data"></a>Interroger les données

Joignez les résultats stockés provenant de la requête du pool de données aux données locales de la table **Sales**.

```sql
SELECT TOP (100)
   w.wcs_user_sk,
   SUM( CASE WHEN i.i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
   SUM( CASE WHEN w.i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
   SUM( CASE WHEN w.i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
   SUM( CASE WHEN w.i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
   SUM( CASE WHEN w.i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
   SUM( CASE WHEN w.i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
   SUM( CASE WHEN w.i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
   SUM( CASE WHEN w.i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
   SUM( CASE WHEN w.i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
   SUM( CASE WHEN w.i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
FROM [dbo].[web_clickstream_clicks_data_pool] as w
INNER JOIN (SELECT DISTINCT i_category_id, i_category FROM item) as i
   ON i.i_category_id = w.i_category_id
GROUP BY w.wcs_user_sk;
```

## <a name="clean-up"></a>Nettoyer

Utilisez la commande suivante pour supprimer les objets de base de données créés dans ce tutoriel.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstream_clicks_data_pool];
```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment ingérer des données dans le pool de données avec des travaux Spark :
> [!div class="nextstepaction"]
> [Ingérer des données avec des travaux Spark](tutorial-data-pool-ingest-spark.md)
