---
title: Interroger des données HDFS dans le pool de stockage
titleSuffix: SQL Server big data clusters
description: Ce didacticiel montre comment interroger des données HDFS dans un cluster de données volumineuses de SQL Server 2019 (version préliminaire). Vous créez une table externe sur les données dans le pool de stockage et puis exécutez une requête.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d24c5b2089160236f4dcfaf5acf00e2426137f89
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66770801"
---
# <a name="tutorial-query-hdfs-in-a-sql-server-big-data-cluster"></a>Tutoriel : Requête HDFS dans un cluster de données volumineux de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce didacticiel montre comment interroger des données HDFS dans un cluster de données volumineuses de SQL Server 2019 (version préliminaire).

Dans ce didacticiel, vous allez découvrir comment :

> [!div class="checklist"]
> * Créer une table externe pointant vers les données HDFS dans un cluster de données volumineux.
> * Joindre ces données avec les données de valeur élevée dans l’instance principale.

> [!TIP]
> Si vous préférez, vous pouvez télécharger et exécuter un script pour les commandes de ce didacticiel. Pour obtenir des instructions, consultez le [échantillons de virtualisation des données](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) sur GitHub.

## <a id="prereqs"></a> Conditions préalables

- [Outils de données volumineuses](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Extension de SQL Server 2019**
- [Charger des exemples de données dans votre cluster de données volumineux](tutorial-load-sample-data.md)

## <a name="create-an-external-table-to-hdfs"></a>Créer une table externe à HDFS

Le pool de stockage contient des données de parcours web dans un fichier CSV stockée dans HDFS. Utilisez les étapes suivantes pour définir une table externe qui peut accéder aux données dans ce fichier.

1. Dans Azure Data Studio, connectez-vous à l’instance principale de SQL Server de votre cluster big data. Pour plus d’informations, consultez [se connecter à l’instance principale de SQL Server](connect-to-big-data-cluster.md#master).

1. Double-cliquez sur la connexion dans le **serveurs** fenêtre pour afficher le tableau de bord du serveur pour l’instance principale de SQL Server. Sélectionnez **nouvelle requête**.

   ![Requête d’instance principale de SQL Server](./media/tutorial-query-hdfs-storage-pool/sql-server-master-instance-query.png)

1. Exécutez la commande Transact-SQL suivante pour modifier le contexte pour le **Sales** base de données dans l’instance principale.

   ```sql
   USE Sales
   GO
   ```

1. Définissez le format du fichier CSV pour lire à partir de HDFS. Appuyez sur F5 pour exécuter l’instruction.

   ```sql
   CREATE EXTERNAL FILE FORMAT csv_file
   WITH (
       FORMAT_TYPE = DELIMITEDTEXT,
       FORMAT_OPTIONS(
           FIELD_TERMINATOR = ',',
           STRING_DELIMITER = '"',
           FIRST_ROW = 2,
           USE_TYPE_DEFAULT = TRUE)
   );
   ```

1. Créer une source de données externe au pool de stockage si elle n’existe pas déjà.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
   BEGIN
     CREATE EXTERNAL DATA SOURCE SqlStoragePool
     WITH (LOCATION = 'sqlhdfs://controller-svc:8080/default');
   END
   ```

1. Créer une table externe qui peut lire le `/clickstream_data` du pool de stockage. Le **SqlStoragePool** est accessible à partir de l’instance principale d’un cluster de données volumineuses.

   ```sql
   CREATE EXTERNAL TABLE [web_clickstreams_hdfs]
   ("wcs_click_date_sk" BIGINT , "wcs_click_time_sk" BIGINT , "wcs_sales_sk" BIGINT , "wcs_item_sk" BIGINT , "wcs_web_page_sk" BIGINT , "wcs_user_sk" BIGINT)
   WITH
   (
       DATA_SOURCE = SqlStoragePool,
       LOCATION = '/clickstream_data',
       FILE_FORMAT = csv_file
   );
   GO
   ```

## <a name="query-the-data"></a>Interroger les données

Exécutez la requête suivante pour joindre les données HDFS le `web_clickstream_hdfs` table externe avec les données relationnelles dans local `Sales` base de données.

```sql
SELECT  
    wcs_user_sk,
    SUM( CASE WHEN i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
    SUM( CASE WHEN i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
    SUM( CASE WHEN i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
    SUM( CASE WHEN i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
    SUM( CASE WHEN i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
    SUM( CASE WHEN i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
    SUM( CASE WHEN i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
    SUM( CASE WHEN i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
    SUM( CASE WHEN i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
    SUM( CASE WHEN i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
  FROM [dbo].[web_clickstreams_hdfs]
  INNER JOIN item it ON (wcs_item_sk = i_item_sk
                        AND wcs_user_sk IS NOT NULL)
GROUP BY  wcs_user_sk;
GO
```

## <a name="clean-up"></a>Nettoyer

Utilisez la commande suivante pour supprimer la table externe utilisée dans ce didacticiel.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_hdfs];
GO
```

## <a name="next-steps"></a>Étapes suivantes

Passez à l’article suivant pour apprendre à interroger Oracle à partir d’un cluster de données volumineux.
> [!div class="nextstepaction"]
> [Interroger des données externes dans Oracle](tutorial-query-oracle.md)
