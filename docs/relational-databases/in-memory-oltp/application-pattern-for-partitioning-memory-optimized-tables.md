---
title: Modèle d’application - Partitionnement de tables à mémoire optimisée
description: Apprenez-en davantage sur le modèle de conception d’application d’OLTP en mémoire qui stocke les données actuelles et actives dans une table à mémoire optimisée et les données plus anciennes dans une table partitionnée.
ms.custom: seo-dt-2019,issue-PR=4700-14820
ms.date: 05/03/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 3f867763-a8e6-413a-b015-20e9672cc4d1
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8ff253b9164ca12d8d24dd5f7b362f4dfb47d548
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97465440"
---
# <a name="application-pattern-for-partitioning-memory-optimized-tables"></a>Modèle d'application pour partitionner des tables mémoire optimisées

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

[!INCLUDE[hek_2](../../includes/hek-2-md.md)] prend en charge un modèle de conception d’application qui prodigue des ressources de performances aux données relativement récentes. Ce modèle peut s’appliquer quand les données actuelles sont lues ou mises à jour de façon beaucoup plus fréquente que les données plus anciennes. Dans ce cas, les données actuelles sont dites *actives* ou *chaudes*, tandis que les données plus anciennes sont dites *froides*.

L’idée principale est de stocker les données *chaudes* dans une table à mémoire optimisée. Toutes les semaines ou tous les mois, les données plus anciennes devenues *froides* sont déplacées vers une table partitionnée. Les données de la table partitionnée sont stockées sur un lecteur ou autre disque dur, et non en mémoire.

En règle générale, cette conception se sert d’une clé **DateHeure** pour permettre au processus de déplacement de distinguer efficacement les données chaudes des données froides.

## <a name="advanced-partitioning"></a>Partitionnement avancé

La conception fait comme s’il existait une table partitionnée dotée également d’une partition à mémoire optimisée. Pour permettre à cette conception de fonctionner, vous devez veiller à ce que toutes les tables partagent un schéma commun. L’exemple de code présenté plus loin dans cet article en illustre la technique.

Les nouvelles données sont supposées être chaudes par définition. Les données chaudes sont insérées et mises à jour dans la table à mémoire optimisée. Les données froides sont conservées dans la table partitionnée classique. À intervalles réguliers, une procédure stockée ajoute une nouvelle partition. La partition contient les données froides les plus récentes qui ont été déplacées de la table à mémoire optimisée.

Si une opération a besoin uniquement de données chaudes, elle peut utiliser des procédures stockées compilées en mode natif pour accéder aux données. Les opérations susceptibles d’accéder à des données chaudes ou froides doivent utiliser du [!INCLUDE[tsql](../../includes/tsql-md.md)] interprété pour joindre la table à mémoire optimisée à la table partitionnée.

### <a name="add-a-partition"></a>Ajouter une partition

Les données devenues froides récemment doivent être déplacées dans la table partitionnée. Cet échange de partition périodique se déroule comme suit :

1. Pour les données contenues dans la table à mémoire optimisée, déterminez la valeur de DateHeure qui constitue la limite ou la démarcation entre les données chaudes et les données nouvellement froides.
2. Insérez les données nouvellement froides de la table OLTP en mémoire dans une table *cold\_staging*.
3. Supprimez ces mêmes données froides de la table à mémoire optimisée.
4. Faites basculer la table cold\_staging dans une partition.
5. Ajoutez la partition.

#### <a name="maintenance-window"></a>Fenêtre de maintenance

L’une des étapes précédentes consiste à supprimer les données nouvellement froides de la table à mémoire optimisée. Un certain temps s’écoule entre le moment où cette suppression se produit et où la nouvelle partition est ajoutée à la dernière étape. Pendant ce temps, aucune application ne peut lire les données nouvellement froides.

Pour obtenir un exemple, consultez [Partitionnement au niveau de l’application](../../relational-databases/in-memory-oltp/application-level-partitioning.md).

## <a name="code-sample"></a>Exemple de code

L’exemple Transact-SQL ci-dessous a été divisé en plusieurs blocs de code plus petits dans le seul but d’en faciliter la présentation. Vous pouvez les ajouter à un bloc de code plus grand à des fins de test.

Globalement, l’exemple T-SQL montre comment utiliser une table à mémoire optimisée avec une table sur disque partitionnée.

Les premières phases de l’exemple T-SQL créent la base de données avant de créer des objets comme les tables de la base de données. Les phases suivantes montrent comment déplacer les données d’une table à mémoire optimisée vers une table partitionnée.

### <a name="create-a-database"></a>Création d'une base de données

Cette section de l’exemple T-SQL crée une base de données de test. La base de données est configurée pour prendre en charge à la fois les tables à mémoire optimisée et les tables partitionnées.

```sql
CREATE DATABASE PartitionSample;
GO

-- Add a FileGroup, enabled for In-Memory OLTP.
-- Change file path as needed.

ALTER DATABASE PartitionSample
    ADD FILEGROUP PartitionSample_mod
    CONTAINS MEMORY_OPTIMIZED_DATA;

ALTER DATABASE PartitionSample
    ADD FILE(
        NAME = 'PartitionSample_mod',
        FILENAME = 'c:\data\PartitionSample_mod')
    TO FILEGROUP PartitionSample_mod;
GO
```

### <a name="create-a-memory-optimized-table-for-hot-data"></a>Créer une table à mémoire optimisée pour les données chaudes

Cette section crée la table à mémoire optimisée qui contient les données les plus récentes, qui sont principalement des données chaudes fixes.

```sql
USE PartitionSample;
GO

-- Create a memory-optimized table for the HOT Sales Order data.
-- Notice the index that uses datetime2.

CREATE TABLE dbo.SalesOrders_hot (
   so_id INT IDENTITY PRIMARY KEY NONCLUSTERED,
   cust_id INT NOT NULL,
   so_date DATETIME2 NOT NULL INDEX ix_date NONCLUSTERED,
   so_total MONEY NOT NULL,
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc)
) WITH (MEMORY_OPTIMIZED=ON);
GO
```

### <a name="create-a-partitioned-table-for-cold-data"></a>Créer une table partitionnée pour les données froides

Cette section crée la table partitionnée qui contient les données froides.

```sql
-- Create a partition and table for the COLD Sales Order data.
-- Notice the index that uses datetime2.

CREATE PARTITION FUNCTION [ByDatePF](datetime2) AS RANGE RIGHT
   FOR VALUES();
GO

CREATE PARTITION SCHEME [ByDateRange]
   AS PARTITION [ByDatePF]
   ALL TO ([PRIMARY]);
GO

CREATE TABLE dbo.SalesOrders_cold (
   so_id INT NOT NULL,
   cust_id INT NOT NULL,
   so_date DATETIME2 NOT NULL,
   so_total MONEY NOT NULL,
   CONSTRAINT PK_SalesOrders_cold PRIMARY KEY (so_id, so_date),
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc)
) ON [ByDateRange](so_date);
GO
```

### <a name="create-a-table-to-store-cold-data-during-move"></a>Créer une table pour stocker les données froides pendant le déplacement

Cette section crée la table cold\_staging. Une vue réunissant les données chaudes et froides des deux tables est également créée.

```sql
-- A table used to briefly stage the newly cold data, during moves to a partition.

CREATE TABLE dbo.SalesOrders_cold_staging (
   so_id INT NOT NULL,
   cust_id INT NOT NULL,
   so_date datetime2 NOT NULL,
   so_total MONEY NOT NULL,
   CONSTRAINT PK_SalesOrders_cold_staging PRIMARY KEY (so_id, so_date),
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc),
   CONSTRAINT CHK_SalesOrders_cold_staging CHECK (so_date >= '1900-01-01')
);
GO

-- A view, for retrieving the aggregation of hot plus cold data.

CREATE VIEW dbo.SalesOrders
AS SELECT so_id,
          cust_id,
          so_date,
          so_total,
          1 AS 'is_hot'
       FROM dbo.SalesOrders_hot
   UNION ALL
   SELECT so_id,
          cust_id,
          so_date,
          so_total,
          0 AS 'is_cold'
       FROM dbo.SalesOrders_cold;
GO
```

### <a name="create-the-stored-procedure"></a>Créer la procédure stockée

Cette section crée la procédure stockée que vous exécutez à intervalles réguliers. La procédure déplace les données nouvellement froides de la table à mémoire optimisée vers la table partitionnée.

```sql
-- A stored procedure to move all newly cold sales orders data
-- to its staging location.

CREATE PROCEDURE dbo.usp_SalesOrdersOffloadToCold @splitdate datetime2
   AS
   BEGIN
      BEGIN TRANSACTION;

      -- Insert the cold data as a temporary heap.
      INSERT INTO dbo.SalesOrders_cold_staging WITH (TABLOCKX)
      SELECT so_id , cust_id , so_date , so_total
         FROM dbo.SalesOrders_hot WITH (serializable)
         WHERE so_date <= @splitdate;

      -- Delete the moved data from the hot table.
      DELETE FROM dbo.SalesOrders_hot WITH (SERIALIZABLE)
         WHERE so_date <= @splitdate;

      -- Update the partition function, and switch in the new partition.
      ALTER PARTITION SCHEME [ByDateRange] NEXT USED [PRIMARY];

      DECLARE @p INT = (
        SELECT MAX(partition_number)
            FROM sys.partitions
            WHERE object_id = OBJECT_ID('dbo.SalesOrders_cold'));

      EXEC sp_executesql
        N'ALTER TABLE dbo.SalesOrders_cold_staging
            SWITCH TO dbo.SalesOrders_cold partition @i',
        N'@i int',
        @i = @p;

      ALTER PARTITION FUNCTION [ByDatePF]()
      SPLIT RANGE( @splitdate);

      -- Modify a constraint on the cold_staging table, to align with new partition.
      ALTER TABLE dbo.SalesOrders_cold_staging
         DROP CONSTRAINT CHK_SalesOrders_cold_staging;

      DECLARE @s nvarchar( 100) = CONVERT( nvarchar( 100) , @splitdate , 121);
      DECLARE @sql nvarchar( 1000) = N'alter table dbo.SalesOrders_cold_staging 
         add constraint CHK_SalesOrders_cold_staging check (so_date > ''' + @s + ''')';
      PRINT @sql;
      EXEC sp_executesql @sql;

      COMMIT;
END;
GO
```

### <a name="prepare-sample-data-and-demo-the-stored-procedure"></a>Préparer les exemples de données et exécuter la procédure stockée à titre de démonstration

Cette section génère des exemples de données, les insère, puis exécute la procédure stockée à titre de démonstration.

```sql
-- Insert sample values into the hot table.
INSERT INTO dbo.SalesOrders_hot VALUES(1,SYSDATETIME(), 1);
GO
INSERT INTO dbo.SalesOrders_hot VALUES(1, SYSDATETIME(), 1);
GO
INSERT INTO dbo.SalesOrders_hot VALUES(1, SYSDATETIME(), 1);
GO

-- Verify that the hot data is in the table, by selecting from the view.
SELECT * FROM dbo.SalesOrders;
GO

-- Treat all data in the hot table as cold data:
-- Run the stored procedure, to move (offload) all sales orders to date to cold storage.
DECLARE @t datetime2 = SYSDATETIME();
EXEC dbo.usp_SalesOrdersOffloadToCold @t;

-- Again, read hot plus cold data from the view.
SELECT * FROM dbo.SalesOrders;
GO

-- Retrieve the name of every partition.
SELECT OBJECT_NAME( object_id) , * FROM sys.dm_db_partition_stats ps
   WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold');

-- Insert more data into the hot table.
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);
GO
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);
GO
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);
GO

-- Read hot plus cold data from the view.
SELECT * FROM dbo.SalesOrders;
GO

-- Again, run the stored procedure, to move all sales orders to date to cold storage.
DECLARE @t datetime2 = SYSDATETIME();
EXEC dbo.usp_SalesOrdersOffloadToCold @t;

-- Read hot plus cold data from the view.
SELECT * FROM dbo.SalesOrders;
GO

-- Again, retrieve the name of every partition.
-- The stored procedure can modify the partitions.
SELECT OBJECT_NAME( object_id) , partition_number , row_count
  FROM sys.dm_db_partition_stats ps
  WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold')
    AND index_id = 1;
```

### <a name="drop-all-the-demo-objects"></a>Supprimer tous les objets de démonstration

N’oubliez pas de nettoyer la base de données de test de démonstration de votre système de test.

```sql
-- You must first leave the context of the PartitionSample database.

-- USE <A-Database-Name-Here>;
GO

DROP DATABASE PartitionSample;
GO
```

## <a name="see-also"></a>Voir aussi

[Tables à mémoire optimisée](./sample-database-for-in-memory-oltp.md)