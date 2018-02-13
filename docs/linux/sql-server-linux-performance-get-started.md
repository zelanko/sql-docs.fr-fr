---
title: "Prise en main des fonctionnalités de performances de SQL Server sur Linux | Documents Microsoft"
description: "Cet article fournit une présentation des fonctionnalités de performances de SQL Server pour Linux aux nouveaux utilisateurs à SQL Server. La plupart de ces exemples fonctionnent sur toutes les plateformes, mais le contexte de cet article est Linux."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.technology: database-engine
ms.assetid: 60036d26-4797-4872-9a9e-3552841c61be
ms.custom: sql-linux
ms.workload: Inactive
ms.openlocfilehash: 73b452cf99016b4b4f38c7debacadf32a270421d
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="walkthrough-for-the-performance-features-of-sql-server-on-linux"></a>Procédure pas à pas pour les fonctionnalités de performances de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Si vous êtes un utilisateur Linux qui est une nouveauté dans SQL Server, les tâches suivantes vous guident certaines des fonctionnalités de performances. Celles-ci ne sont pas uniques ou spécifiques à Linux, mais elle permet de vous donner une idée des zones pour approfondir vos recherches. Dans chaque exemple, un lien est fourni à la documentation de profondeur pour cette zone.

> [!NOTE]
> Les exemples suivants utilisent la base de données AdventureWorks. Pour obtenir des instructions sur la façon d’obtenir et installer cette base de données exemple, consultez [restaurer une base de données SQL Server à partir de Windows et Linux](sql-server-linux-migrate-restore-database.md).

## <a name="create-a-columnstore-index"></a>Créer un Index Columnstore
Un index columnstore est une technologie pour le stockage et l’interrogation de grands magasins de données dans un format de données en colonnes, appelé columnstore.  

1. Ajouter un index Columnstore à la table SalesOrderDetail en exécutant les commandes Transact-SQL suivantes :

   ```sql
   CREATE NONCLUSTERED COLUMNSTORE INDEX [IX_SalesOrderDetail_ColumnStore]
      ON Sales.SalesOrderDetail
      (UnitPrice, OrderQty, ProductID)
   GO
   ```

2. Exécutez la requête suivante qui utilise le Columnstore Index pour analyser la table :

   ```sql
   SELECT ProductID, SUM(UnitPrice) SumUnitPrice, AVG(UnitPrice) AvgUnitPrice,
      SUM(OrderQty) SumOrderQty, AVG(OrderQty) AvgOrderQty
   FROM Sales.SalesOrderDetail
      GROUP BY ProductID
      ORDER BY ProductID
   ```

3. Vérifiez que le Columnstore Index a été utilisé en recherchant l’object_id de l’index Columnstore et en vérifiant qu’il apparaît dans les statistiques d’utilisation de la table SalesOrderDetail :

   ```sql
   SELECT * FROM sys.indexes WHERE name = 'IX_SalesOrderDetail_ColumnStore'
   GO

   SELECT * 
   FROM sys.dm_db_index_usage_stats
      WHERE database_id = DB_ID('AdventureWorks')
      AND object_id = OBJECT_ID('AdventureWorks.Sales.SalesOrderDetail');
   ```
   
## <a name="use-in-memory-oltp"></a>Utiliser l’OLTP en mémoire
SQL Server fournit les fonctionnalités OLTP en mémoire qui peuvent améliorer considérablement les performances des systèmes d’applications.  Cette section du Guide d’évaluation vous guidera tout au long des étapes de création d’une table mémoire optimisée est stockée dans la mémoire et une procédure stockée compilée en mode natif qui peut accéder à la table sans avoir besoin d’être compilées ou interprétées.

### <a name="configure-database-for-in-memory-oltp"></a>Configurer la base de données pour OLTP en mémoire
1. Il est recommandé de définir la base de données à un niveau de compatibilité d’au moins 130 pour utiliser OLTP en mémoire.  Utilisez la requête suivante pour vérifier le niveau de compatibilité actuel d’AdventureWorks :  

   ```sql
   USE AdventureWorks
   GO
   SELECT d.compatibility_level
   FROM sys.databases as d
     WHERE d.name = Db_Name();
   GO
   ```
   
   Si nécessaire, mettez à jour le niveau à 130 :

   ```sql
   ALTER DATABASE CURRENT
   SET COMPATIBILITY_LEVEL = 130;
   GO
   ```

2. Une transaction impliquant une table basée sur disque et une table mémoire optimisée, il est essentiel que la partie mémoire optimisée de la transaction fonctionne au niveau d’isolation des transactions nommé SNAPSHOT.  Pour appliquer les fiable ce niveau pour les tables optimisées en mémoire dans une transaction entre conteneurs, exécutez la commande suivante :

   ```sql
   ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
   GO
   ```

3. Avant de pouvoir créer une table mémoire optimisée, vous devez d’abord créer un groupe de fichiers mémoire optimisé et un conteneur pour les fichiers de données :

   ```sql
   ALTER DATABASE AdventureWorks ADD FILEGROUP AdventureWorks_mod CONTAINS memory_optimized_data
   GO  
   ALTER DATABASE AdventureWorks ADD FILE (NAME='AdventureWorks_mod', FILENAME='/var/opt/mssql/data/AdventureWorks_mod') TO FILEGROUP AdventureWorks_mod
   GO
   ```

### <a name="create-a-memory-optimized-table"></a>Créer une Table optimisée en mémoire
Le magasin principal des tables optimisées en mémoire est la mémoire principale, de sorte qu’à la différence des tables sur disque, données n’a pas besoin de lire à partir du disque dans les mémoires tampons.  Pour créer une table optimisée en mémoire, utilisez le MEMORY_OPTIMIZED = ON clause.

1. Exécutez la requête suivante pour créer le dbo de la table mémoire optimisée. ShoppingCart.  Par défaut, les données sont rendues persistantes sur disque pour la durabilité (Notez que la durabilité peut également être définie pour conserver le schéma uniquement). 

   ```sql
   CREATE TABLE dbo.ShoppingCart ( 
   ShoppingCartId INT IDENTITY(1,1) PRIMARY KEY NONCLUSTERED,
   UserId INT NOT NULL INDEX ix_UserId NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000), 
   CreatedDate DATETIME2 NOT NULL, 
   TotalPrice MONEY
   ) WITH (MEMORY_OPTIMIZED=ON) 
   GO
   ```

2. Insérer des enregistrements dans la table :

   ```sql
   INSERT dbo.ShoppingCart VALUES (8798, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (23, SYSDATETIME(), 45.4) 
   INSERT dbo.ShoppingCart VALUES (80, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (342, SYSDATETIME(), 65.4) 
   ```

### <a name="natively-compiled-stored-procedure"></a>Procédure stockée compilée en mode natif
SQL Server prend en charge les procédures stockées compilées en mode natif qui accèdent aux tables optimisées en mémoire. Les instructions T-SQL sont compilées en code machine et stockées en tant que DLL natives, permettant l’accès aux données plus rapide et l’exécution des requêtes plus efficace que T-SQL traditionnel.   Les procédures stockées qui sont identifiées par NATIVE_COMPILATION sont compilées en mode natif. 

1. Exécutez le script suivant pour créer une procédure stockée compilée en mode natif qui insère un grand nombre d’enregistrements dans la table ShoppingCart :


   ```sql
   CREATE PROCEDURE dbo.usp_InsertSampleCarts @InsertCount int 
    WITH NATIVE_COMPILATION, SCHEMABINDING AS 
   BEGIN ATOMIC 
   WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')

   DECLARE @i int = 0

   WHILE @i < @InsertCount 
    BEGIN 
     INSERT INTO dbo.ShoppingCart VALUES (1, SYSDATETIME() , NULL) 
     SET @i += 1 
    END
   END 
   ```
2. Insérer 1 000 000 lignes :

   ```sql
   EXEC usp_InsertSampleCarts 1000000 
   ```

3. Vérifiez que les lignes ont été insérées :

   ```sql
   SELECT COUNT(*) FROM dbo.ShoppingCart 
   ```

### <a name="learn-more-about-in-memory-oltp"></a>En savoir plus sur OLTP en mémoire
Pour plus d’informations sur l’OLTP en mémoire, consultez les rubriques suivantes :

- [Démarrage rapide 1 : technologies OLTP en mémoire pour accélérer les performances Transact-SQL](../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)
- [Migration vers OLTP en mémoire](../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)
- [Table temporaire et variable de table plus rapides à l’aide de l’optimisation en mémoire](../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)
- [Surveiller l’utilisation de la mémoire et résoudre les problèmes connexes](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)
- [OLTP en mémoire (optimisation en mémoire)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)

## <a name="use-query-store"></a>Utilisez le magasin de requête
Magasin de requêtes collecte des informations détaillées sur les performances sur les requêtes, les plans d’exécution et les statistiques d’exécution.

Magasin de requêtes n’est pas actif par défaut et peut être activé avec ALTER DATABASE :

   ```sql
   ALTER DATABASE AdventureWorks SET QUERY_STORE = ON;
   ```

Exécutez la requête suivante pour retourner des informations sur les requêtes et plans du magasin de requêtes : 

   ```sql
   SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
   FROM sys.query_store_plan AS Pl
      JOIN sys.query_store_query AS Qry
         ON Pl.query_id = Qry.query_id
      JOIN sys.query_store_query_text AS Txt
         ON Qry.query_text_id = Txt.query_text_id ;
   ```

## <a name="query-dynamic-management-views"></a>Vues de gestion dynamique de requête
Vues de gestion dynamique retournent des informations d’état de serveur qui peuvent être utilisées pour surveiller l’intégrité d’une instance de serveur, diagnostiquer les problèmes et régler les performances.

Pour interroger la vue de gestion dynamique de statistiques dm_os_wait :

   ```sql
   SELECT wait_type, wait_time_ms
   FROM sys.dm_os_wait_stats;
   ```
