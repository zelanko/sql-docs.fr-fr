---
title: Recevoir des données dans un pool de données SQL Server
titleSuffix: SQL Server 2019 big data clusters
description: Ce didacticiel montre comment recevoir des données dans le pool de données d’un cluster de données volumineuses de SQL Server 2019 (version préliminaire) avec la procédure stockée de sp_data_pool_table_insert_data.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 086db0838eb02b0e83ffbb2f00b92d39e1e4d202
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017667"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-transact-sql"></a>Didacticiel : Recevoir des données dans un pool de données SQL Server avec Transact-SQL

Ce didacticiel montre comment utiliser Transact-SQL pour charger des données dans le [pool de données](concept-data-pool.md) d’un cluster de données volumineuses de SQL Server 2019 (version préliminaire). Avec les clusters de données volumineuses de SQL Server, à partir de diverses sources ingérées et de données distribuées sur des instances de pool de données.

Dans ce didacticiel, vous allez découvrir comment :

> [!div class="checklist"]
> * Créer une table externe dans le pool de données.
> * Insérer des exemples de données de parcours web dans la table de pool de données.
> * Joindre des données dans la table de pool de données avec des tables locales.

> [!TIP]
> Si vous préférez, vous pouvez télécharger et exécuter un script pour les commandes de ce didacticiel. Pour obtenir des instructions, consultez le [pools de données exemples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) sur GitHub.

## <a id="prereqs"></a> Conditions préalables

- [Outils de données volumineuses](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Extension de SQL Server 2019**
- [Charger des exemples de données dans votre cluster de données volumineux](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Créer une table externe dans le pool de données

Les étapes suivantes créent une table externe dans le pool de données nommé **web_clickstream_clicks_data_pool**. Cette table peut ensuite servir en tant qu’emplacement de réception des données dans le cluster de données volumineuses.

1. Dans Azure Data Studio, connectez-vous à l’instance principale de SQL Server de votre cluster big data. Pour plus d’informations, consultez [se connecter à l’instance principale de SQL Server](connect-to-big-data-cluster.md#master).

1. Double-cliquez sur la connexion dans le **serveurs** fenêtre pour afficher le tableau de bord du serveur pour l’instance principale de SQL Server. Sélectionnez **nouvelle requête**.

   ![Requête d’instance principale de SQL Server](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. Exécutez la commande Transact-SQL suivante pour modifier le contexte pour le **Sales** base de données dans l’instance principale.

   ```sql
   USE Sales
   GO
   ```

1. Créer une table externe nommée **web_clickstream_clicks_data_pool** dans le pool de données. Le `SqlDataPool` source de données est un type de source de données spécial qui peut être utilisé à partir de l’instance principale de n’importe quel cluster big data.

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
  
1. Dans CTP 2.3, la création du pool de données est asynchrone, mais il n’existe aucun moyen de déterminer quand il se termine encore. Veuillez patienter deux minutes pour vous assurer que le pool de données est créé avant de continuer.

## <a name="load-data"></a>Charger des données

Les étapes suivantes ingérer les données de parcours web exemple dans le pool de données à l’aide de la table externe créée dans les étapes précédentes.

1. Définir des variables de la requête que vous souhaitez utiliser pour insérer des données dans le pool de données. Utilisez ensuite le **modèle... sp_data_pool_table_insert_data** procédure stockée pour insérer les résultats de la requête dans le pool de données (le **web_clickstream_clicks_data_pool** table externe).

   ```sql
   DECLARE @db_name SYSNAME = 'Sales'
   DECLARE @schema_name SYSNAME = 'dbo'
   DECLARE @table_name SYSNAME = 'web_clickstream_clicks_data_pool'
   DECLARE @query NVARCHAR(MAX) = '
   SELECT wcs_user_sk, i_category_id, COUNT_BIG(*) as clicks
   FROM sales.dbo.web_clickstreams
   INNER JOIN sales.dbo.item it ON (wcs_item_sk = i_item_sk
      AND wcs_user_sk IS NOT NULL)
   GROUP BY wcs_user_sk, i_category_id
   HAVING COUNT_BIG(*) > 100;'

   EXEC model..sp_data_pool_table_insert_data @db_name, @schema_name, @table_name, @query
   ```

1. Inspecter les données insérées avec deux requêtes SELECT.

   ```sql
   SELECT count(*) FROM [dbo].[web_clickstream_clicks_data_pool]
   SELECT TOP 10 * FROM [dbo].[web_clickstream_clicks_data_pool]  
   ```

## <a name="query-the-data"></a>Interroger les données

Joindre les résultats stockés à partir de la requête dans le pool de données avec des données locales dans le **Sales** table.

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

Utilisez la commande suivante pour supprimer les objets de base de données créés dans ce didacticiel.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstream_clicks_data_pool];
```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment recevoir des données dans le pool de données avec des travaux Spark :
> [!div class="nextstepaction"]
> [Recevoir des données avec des travaux Spark](tutorial-data-pool-ingest-spark.md)
