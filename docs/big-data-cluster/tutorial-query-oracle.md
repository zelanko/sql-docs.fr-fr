---
title: Interroger des données externes dans Oracle
titleSuffix: SQL Server 2019 big data clusters
description: Ce didacticiel montre comment interroger des données Oracle à partir d’un cluster de données volumineuses de SQL Server 2019 (version préliminaire). Vous créez une table externe sur les données dans Oracle et puis exécutez une requête.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/12/2018
ms.topic: tutorial
ms.custom: seodec18
ms.openlocfilehash: f7a367a41814a7cb590276b10fcfb7c4c8697011
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432152"
---
# <a name="tutorial-query-oracle-from-a-sql-server-big-data-cluster"></a>Didacticiel : Interroger Oracle à partir d’un cluster de données volumineux de SQL Server

Ce didacticiel montre comment interroger des données Oracle à partir d’un cluster de données volumineux de SQL Server 2019. Pour exécuter ce didacticiel, vous devez avoir accès à un serveur Oracle. Si vous n’avez pas accès, ce didacticiel peut vous donner une idée du fonctionne de la virtualisation des données pour les sources de données externes dans un cluster de données volumineux de SQL Server.

Dans ce didacticiel, vous allez découvrir comment :

> [!div class="checklist"]
> * Créer une table externe pour les données dans une base de données Oracle externe.
> * Joindre ces données avec les données de valeur élevée dans l’instance principale.

> [!TIP]
> Si vous préférez, vous pouvez télécharger et exécuter un script pour les commandes de ce didacticiel. Pour obtenir des instructions, consultez le [échantillons de virtualisation des données](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) sur GitHub.

## <a id="prereqs"></a> Conditions préalables

- [Outils de données volumineuses](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Extension de SQL Server 2019**
- [Charger des exemples de données dans votre cluster de données volumineux](tutorial-load-sample-data.md)

## <a name="create-an-oracle-table"></a>Créer une table Oracle

Les étapes suivantes créent un exemple de table nommé `INVENTORY` dans Oracle.

1. Se connecter à une instance Oracle et de la base de données que vous souhaitez utiliser pour ce didacticiel.

1. Exécutez l’instruction suivante pour créer le `INVENTORY` table :

   ```sql
    CREATE TABLE "INVENTORY"
    (
        "INV_DATE" NUMBER(10,0) NOT NULL,
        "INV_ITEM" NUMBER(10,0) NOT NULL,
        "INV_WAREHOUSE" NUMBER(10,0) NOT NULL,
        "INV_QUANTITY_ON_HAND" NUMBER(10,0)
    );

    CREATE INDEX INV_ITEM ON HR.INVENTORY(INV_ITEM);
    ```

1. Importer le contenu de la **inventory.csv** fichier dans cette table. Ce fichier a été créé par les exemples de scripts de création dans le [conditions préalables](#prereqs) section.

## <a name="create-an-external-data-source"></a>Créer une source de données externe

La première étape consiste à créer une source de données externe qui peut accéder à votre serveur Oracle.

1. Dans Azure Data Studio, connectez-vous à l’instance principale de SQL Server de votre cluster big data. Pour plus d’informations, consultez [se connecter à l’instance principale de SQL Server](connect-to-big-data-cluster.md#master).

1. Double-cliquez sur la connexion dans le **serveurs** fenêtre pour afficher le tableau de bord du serveur pour l’instance principale de SQL Server. Sélectionnez **nouvelle requête**.

   ![Requête d’instance principale de SQL Server](./media/tutorial-query-oracle/sql-server-master-instance-query.png)

1. Exécutez la commande Transact-SQL suivante pour modifier le contexte pour le **Sales** base de données dans l’instance principale.

   ```sql
   USE Sales
   GO
   ```

1. Créer une information d’identification de niveau base de données pour se connecter au serveur Oracle. Fournir des informations d’identification appropriées à votre serveur Oracle dans l’instruction suivante.

   ```sql
   CREATE DATABASE SCOPED CREDENTIAL [OracleCredential]
   WITH IDENTITY = '<oracle_user,nvarchar(100),SYSTEM>', SECRET = '<oracle_user_password,nvarchar(100),manager>';
   ```

1. Créer une source de données externe qui pointe vers le serveur Oracle.

   ```sql
   CREATE EXTERNAL DATA SOURCE [OracleSalesSrvr]
   WITH (LOCATION = 'oracle://<oracle_server,nvarchar(100)>',CREDENTIAL = [OracleCredential]);
   ```

## <a name="create-an-external-table"></a>Créer une table externe

Ensuite, créez une table externe nommée **iventory_ora** via la `INVENTORY` table sur le serveur Oracle.

```sql
CREATE EXTERNAL TABLE [inventory_ora]
    ([inv_date] DECIMAL(10,0) NOT NULL, [inv_item] DECIMAL(10,0) NOT NULL,
    [inv_warehouse] DECIMAL(10,0) NOT NULL, [inv_quantity_on_hand] DECIMAL(10,0))
WITH (DATA_SOURCE=[OracleSalesSrvr],
        LOCATION='<oracle_service_name,nvarchar(30),xe>.<oracle_schema,nvarchar(128),HR>.<oracle_table,nvarchar(128),INVENTORY>');
```

> [!NOTE]
> Les noms de colonnes et les noms de table utilise SQL ANSI identificateur entre guillemets lors de l’interrogation par rapport à Oracle. Par conséquent, les noms respectent la casse. Il est important de spécifier le nom dans la définition de table externe qui correspond à la casse des noms de table et de colonne dans les métadonnées d’Oracle.

## <a name="query-the-data"></a>Interroger les données

Exécutez la requête suivante pour joindre les données le `iventory_ora` table externe avec les tables local `Sales` base de données.

```sql
SELECT TOP(100) w.w_warehouse_name, i.inv_item, SUM(i.inv_quantity_on_hand) as total_quantity
  FROM [inventory_ora] as i
  JOIN item as it
    ON it.i_item_sk = i.inv_item
  JOIN warehouse as w
    ON w.w_warehouse_sk = i.inv_warehouse
 WHERE it.i_category = 'Books' and i.inv_item BETWEEN 1 and 18000 --> get items within specific range
 GROUP BY w.w_warehouse_name, i.inv_item;
```

## <a name="clean-up"></a>Nettoyer

Utilisez la commande suivante pour supprimer les objets de base de données créés dans ce didacticiel.

```sql
DROP EXTERNAL TABLE [inventory_ora];
DROP EXTERNAL DATA SOURCE [OracleSalesSrvr] ;
DROP DATABASE SCOPED CREDENTIAL [OracleCredential];
```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment recevoir des données dans le pool de données :
> [!div class="nextstepaction"]
> [Charger des données dans le pool de données](tutorial-data-pool-ingest-sql.md)
