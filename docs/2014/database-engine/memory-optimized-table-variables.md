---
title: Variables de Table optimisé en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: bd102e95-53e2-4da6-9b8b-0e4f02d286d3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 485f481819a9712f822f969c04d8e7050ad43bae
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62774410"
---
# <a name="memory-optimized-table-variables"></a>Variables de table mémoire optimisée
  En plus des tables mémoire optimisées (pour un accès efficace aux données) et des procédures stockées compilées en mode natif (pour une exécution efficace des requêtes et de la logique métier), [!INCLUDE[hek_2](../includes/hek-2-md.md)] introduit un troisième type d'objet : le type de table mémoire optimisée. Une variable de table créée avec un type de table mémoire optimisée est une variable de table mémoire optimisée.  
  
 Les variables de table mémoire optimisée offrent les avantages suivants par rapport aux variables de table sur disque :  
  
-   Les variables sont uniquement stockées dans la mémoire. L'accès aux données est plus efficace car le type de table mémoire optimisée utilise le même algorithme et les mêmes structures de données mémoire optimisés utilisés pour les tables mémoire optimisées, en particulier lorsque les variables sont utilisées dans les procédures stockées compilées en mode natif.  
  
-   Avec les variables de table mémoire optimisée, tempdb n'est pas utilisé. Les variables de table ne sont pas stockées dans tempdb et n'utilisent aucune ressource dans tempdb.  
  
 Les scénarios d'utilisation typiques des variables de table mémoire optimisée sont les suivants :  
  
-   Stockage de résultats intermédiaires et création d'ensembles de résultats uniques en fonction de plusieurs requêtes dans les procédures stockées compilées en mode natif.  
  
-   Passage des paramètres de la table à des procédures stockées compilées en mode natif et à des procédures stockées interprétées.  
  
-   Remplacement des variables de table sur disque, et dans certains cas, des tables #temp locales sur une procédure stockée. Cela est particulièrement utile s'il y a beaucoup de contentions de tempdb dans le système.  
  
-   Les variables de table peuvent être utilisées pour simuler des curseurs dans les procédures stockées compilées en mode natif, ce qui peut vous aider à contourner les limitations concernant la surface d'exposition dans ces procédures.  
  
 Comme les tables mémoire optimisées, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] génère une DLL pour chaque type de table mémoire optimisée. (Compilation est appelée lorsque le type de table mémoire optimisée est créé et ne pas lorsque vous permet de créer des variables de table mémoire optimisée). Cette DLL contient les fonctions pour accéder aux index et récupérer des données des variables de table. Lorsqu'une variable de table mémoire optimisée est déclarée en fonction du type de table, une instance de la table et des structures d'index correspondant au type de table est créée dans la session utilisateur. La variable de table peut ensuite être utilisée de la même manière que les variables de table sur disque. Vous pouvez insérer, mettre à jour, et supprimer des lignes dans la variable de table, et utiliser des variables dans les requêtes [!INCLUDE[tsql](../includes/tsql-md.md)] . Vous pouvez également passer les variables dans les procédures stockées compilées en mode natif et interprétées, comme paramètres de table (TVP).  
  
 L'exemple suivant illustre un type de table mémoire optimisée tiré de l'exemple basé sur AdventureWorks de l'OLTP en mémoire ([Exemple d'OLTP en mémoire SQL Server 2014](https://msftdbprodsamples.codeplex.com/releases/view/114491)).  
  
```sql
CREATE TYPE Sales.SalesOrderDetailType_inmem
   AS TABLE
(
   OrderQty         smallint   NOT NULL,
   ProductID        int        NOT NULL,

   SpecialOfferID   int        NOT NULL
      INDEX  IX_SpecialOfferID  NONCLUSTERED,

   LocalID          int        NOT NULL,

   INDEX IX_ProductID HASH (ProductID)
      WITH ( BUCKET_COUNT = 8 )
)
WITH ( MEMORY_OPTIMIZED = ON );
```  
  
 L'exemple montre que la syntaxe des types de tables mémoire optimisées est similaire aux types de tables sur disque, avec les exceptions suivantes :  
  
-   `MEMORY_OPTIMIZED=ON` indique que le type est une table mémoire optimisée.  
  
-   Le type doit avoir au moins un index. Comme pour les tables mémoire optimisées, vous pouvez utiliser des index de hachage et non cluster.  
  
     Pour un index de hachage, le nombre de compartiments doit être égal à une à deux fois le nombre de clés d'index uniques attendu. Pour plus d’informations, consultez [déterminer le nombre de compartiments Correct pour les index de hachage](../relational-databases/indexes/indexes.md).  
  
-   Les restrictions de type de données et de contrainte sur les tables mémoire optimisées s'appliquent également aux types de table mémoire optimisée. Par exemple, dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] , les contraintes par défaut sont prises en charge, mais les contraintes de validation ne le sont pas.  
  
 Comme les tables mémoire optimisées, les variables de table mémoire optimisée :  
  
-   ne prennent pas en charge les plans parallèles ;  
  
-   doivent tenir dans la mémoire et n'utilisent pas de ressources de disque.  
  
 Les variables de table sur disque existent dans tempdb. Les variables de table mémoire optimisée existent dans la base de données utilisateur (mais elles ne consomment pas de stockage et ne sont pas récupérées).  
  
 Vous ne pouvez pas créer une variable de table mémoire optimisée avec la syntaxe in-line. Contrairement aux variables de table sur disque, vous devez créer d'abord un type.  
  
## <a name="table-valued-parameters"></a>Paramètres table  
 L'exemple de script suivant illustre la déclaration d'une variable de table comme type de table mémoire optimisée `Sales.SalesOrderDetailType_inmem`, l'insertion de trois lignes dans la variable, et le passage des variables comme TVP dans `Sales.usp_InsertSalesOrder_inmem`.  
  
```sql  
DECLARE @od Sales.SalesOrderDetailType_inmem,  
  @SalesOrderID uniqueidentifier,  
  @DueDate datetime2 = SYSDATETIME()  
  
INSERT @od (LocalID, ProductID, OrderQty, SpecialOfferID) VALUES  
  (1, 888, 2, 1),  
  (2, 450, 13, 1),  
  (3, 841, 1, 1)  
  
EXEC Sales.usp_InsertSalesOrder_inmem  
  @SalesOrderID = @SalesOrderID,  
  @DueDate = @DueDate,  
 @OnlineOrderFlag = 1,  
  @SalesOrderDetails = @od  
```  
  
 Les types de table mémoire optimisée peuvent être utilisés comme type pour les paramètres de table (TVP) de la procédure stockée et peuvent être référencés par des clients exactement comme des types de table et des TVP sur disque. Par conséquent, l'appel de procédures stockées avec des TVP mémoire optimisés et de procédures stockées compilées en mode natif, fonctionne exactement comme l'appel de procédures stockées interprétées avec des TVP sur disque.  
  
## <a name="temp-table-replacement"></a>Remplacement de la table #temp  
 L'exemple suivant illustre les types de table et les variables de table mémoire optimisée remplaçant les tables #temp locales sur une procédure stockée.  
  
```sql  
-- Using SQL procedure and temp table  
CREATE TABLE #tempTable (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
  
CREATE PROCEDURE sqlProc  
AS  
BEGIN  
  TRUNCATE TABLE #tempTable  
  
  INSERT #tempTable VALUES (1)  
  INSERT #tempTable VALUES (2)  
  INSERT #tempTable VALUES (3)  
  SELECT * FROM #tempTable  
END  
GO  
  
-- Using natively compiled stored procedure and table variable  
CREATE TYPE TT AS TABLE (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
GO  
  
CREATE PROCEDURE NCSPProc  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @tableVariable TT  
  INSERT @tableVariable VALUES (1)  
  INSERT @tableVariable VALUES (2)  
  INSERT @tableVariable VALUES (3)  
  SELECT c FROM @tableVariable  
END  
GO  
```  
  
## <a name="creating-a-single-result-set"></a>Création d'un seul ensemble de résultats  
 L'exemple suivant explique comment stocker des résultats intermédiaires et créer des ensembles de résultats uniques en fonction de plusieurs requêtes dans les procédures stockées compilées en mode natif. L'exemple calcule l'union `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2`.  
  
```sql  
CREATE DATABASE hk  
GO  
ALTER DATABASE hk ADD FILEGROUP hk_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE hk ADD FILE( NAME = 'hk_mod' , FILENAME = 'c:\data\hk_mod') TO FILEGROUP hk_mod;  
  
USE hk  
GO  
  
CREATE TYPE tab1 AS TABLE (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON)  
  
CREATE TABLE dbo.t1 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
CREATE TABLE dbo.t2 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
  
INSERT INTO dbo.t1 VALUES (1), (2)  
INSERT INTO dbo.t2 VALUES (3), (4)  
GO  
  
CREATE PROCEDURE dbo.p1  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS  
  BEGIN ATOMIC WITH ( TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english' )  
  
    DECLARE @t dbo.tab1  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t1;  
  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t2;  
  
    SELECT c1 FROM @t;  
  END  
GO  
  
EXEC dbo.p1  
GO  
```  
  
## <a name="memory-consumption-for-table-variables"></a>Consommation de mémoire pour les variables de table  
 La consommation de mémoire pour les variables de table est similaire aux tables mémoire optimisées, à l'exception des index non cluster. Si vous insérez de nombreuses lignes dans des variables de table mémoire optimisée avec des index non cluster et si les clés d'index sont longues, ces variables utiliseront une quantité démesurée de mémoire. Les index non cluster sur les grandes de variables de table nécessitent proportionnellement plus de mémoire qu'un index non cluster pour le même nombre de lignes insérées dans une table (plus de mémoire dans les pages d'index).  
  
 La mémoire pour les variables de table vient du pool de ressources du gouverneur de ressources de la base de données.  
  
 Contrairement aux tables mémoire optimisées, la mémoire consommée (lignes supprimées incluses) par les variables de table est libérée lorsque la variable de table sort de l'étendue.  
  
 La mémoire est prise en compte dans le cadre d'un seul consommateur de mémoire PGPOOL de la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge d’OLTP en mémoire par Transact-SQL](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
