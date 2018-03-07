---
title: "CREATE TABLE AS SELECT (entrepôt de données SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 10/07/2016
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d1e08f88-64ef-4001-8a66-372249df2533
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 429c2dc727d844c35943fa599e6fbcb911df04ac
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="create-table-as-select-azure-sql-data-warehouse"></a>CREATE TABLE AS SELECT (entrepôt de données SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

CREATE TABLE AS sélectionnez (SACT) est une des fonctionnalités de T-SQL plus importantes. Il s’agit d’une opération entièrement parallélisée qui crée une table basée sur la sortie d’une instruction SELECT. SACT est le moyen le plus rapide pour créer une copie d’une table.   
 
 Par exemple, utilisez SACT pour :  
  
-   Recréez la table avec une colonne de distribution de hachage différent.
-   Recréez la table comme étant répliqués.   
-   Créer un index columnstore sur certaines colonnes de la table.  
-   Requête ou importer des données externes.  

> [!NOTE]  
> Étant donné que SACT ajoute des fonctionnalités de création d’une table, cette rubrique tente ne pas répéter la rubrique CREATE TABLE. Au lieu de cela, il décrit les différences entre les instructions SACT et CREATE TABLE. Pour plus d’informations CREATE TABLE, consultez [CREATE TABLE (Azure SQL Data Warehouse)](https://msdn.microsoft.com/library/mt203953/) instruction. 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
<a name="syntax-bk"></a>

## <a name="syntax"></a>Syntaxe   

```  
CREATE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    [ ( column_name [ ,...n ] ) ]  
    WITH ( 
      <distribution_option> -- required
      [ , <table_option> [ ,...n ] ]    
    )  
    AS <select_statement>   
[;]  

<distribution_option> ::=
    { 
        DISTRIBUTION = HASH ( distribution_column_name ) 
      | DISTRIBUTION = ROUND_ROBIN 
      | DISTRIBUTION = REPLICATE
    }   

<table_option> ::= 
    {   
        CLUSTERED COLUMNSTORE INDEX --default for SQL Data Warehouse 
      | HEAP --default for Parallel Data Warehouse   
      | CLUSTERED INDEX ( { index_column_name [ ASC | DESC ] } [ ,...n ] ) --default is ASC 
    }  
    | PARTITION ( partition_column_name RANGE [ LEFT | RIGHT ] --default is LEFT  
        FOR VALUES ( [ boundary_value [,...n] ] ) ) 
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT select_criteria  

```  

<a name="arguments-bk"></a>
  
## <a name="arguments"></a>Arguments  
Pour plus d’informations, consultez la [section Arguments](https://msdn.microsoft.com/library/mt203953/#Arguments) dans CREATE TABLE.  

<a name="column-options-bk"></a>

### <a name="column-options"></a>Options de colonne
`column_name` [ ,...`n` ]   
 Noms de colonnes n’autorisent pas les [options de colonne](https://msdn.microsoft.com/library/mt203953/#ColumnOptions) mentionné dans CREATE TABLE.  Au lieu de cela, vous pouvez fournir une liste facultative d’un ou plusieurs noms de colonne pour la nouvelle table. Les colonnes de la nouvelle table utilisera les noms que vous spécifiez. Lorsque vous spécifiez des noms de colonnes, le nombre de colonnes dans la liste des colonnes doit correspondre au nombre de colonnes dans les résultats de select. Si vous ne spécifiez pas des noms de colonnes, la nouvelle table cible utilise les noms de colonnes dans les résultats de l’instruction select. 
  
 Vous ne pouvez pas spécifier d’autres options de colonne telles que les types de données, classement ou possibilité de valeur null. Chacun de ces attributs est dérivée à partir des résultats de la `SELECT` instruction. Toutefois, vous pouvez utiliser l’instruction SELECT pour modifier les attributs. Pour obtenir un exemple, consultez [SACT d’utilisation pour modifier les attributs de colonne](#ctas-change-column-attributes-bk).   

<a name="table-distribution-options-bk"></a>

### <a name="table-distribution-options"></a>Options de distribution de table

`DISTRIBUTION` = `HASH`( *distribution_column_name* ) | ROUND_ROBIN | RÉPLIQUER      
L’instruction SACT requiert une option de distribution et n’a pas de valeurs par défaut. Cela est différent de CREATE TABLE qui a des valeurs par défaut. 

Pour plus d’informations et pour comprendre comment choisir la meilleure colonne de distribution, consultez le [options de distribution de la Table](https://msdn.microsoft.com/library/mt203953/#TableDistributionOptions) section dans CREATE TABLE. 

<a name="table-partition-options-bk"></a>

### <a name="table-partition-options"></a>Options de partition de table
L’instruction SACT crée une table non partitionnée par défaut, même si la table source est partitionnée. Pour créer une table partitionnée avec l’instruction SACT, vous devez spécifier l’option de partition. 

Pour plus d’informations, consultez la [les options de partition de Table](https://msdn.microsoft.com/library/mt203953/#TablePartitionOptions) section dans CREATE TABLE.

<a name="select-options-bk"></a>

### <a name="select-options"></a>Sélectionnez les options
L’instruction select est la différence fondamentale entre SACT et CREATE TABLE.  

 `WITH` *common_table_expression*  
 Spécifie un jeu de résultats nommé temporaire, désigné par le terme d'expression de table commune (CTE, Common Table Expression). Pour plus d’informations, consultez [avec common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 `SELECT` *select_criteria*  
 Remplit la nouvelle table avec les résultats d’une instruction SELECT. *select_criteria* est le corps de l’instruction SELECT qui détermine les données à copier vers la nouvelle table. Pour plus d’informations sur les instructions SELECT, consultez [SELECT &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
<a name="permissions-bk"></a>  
  
## <a name="permissions"></a>Autorisations  
SACT requiert `SELECT` autorisation sur les objets référencés dans les *select_criteria*.

Pour les autorisations créer une table, consultez [autorisations](https://msdn.microsoft.com/library/mt203953/#Permissions) dans CREATE TABLE. 
  
<a name="general-remarks-bk"></a>
  
## <a name="general-remarks"></a>Remarques d'ordre général
Pour plus d’informations, consultez [Remarques d’ordre général](https://msdn.microsoft.com/library/mt203953/#GeneralRemarks) dans CREATE TABLE.

<a name="limitations-bk"></a>

## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
Azure SQL Data Warehouse effectue pas encore prise en charge automatique créer ou automatiquement les statistiques de mise à jour.  Pour obtenir les meilleures performances de vos requêtes, il est important créer des statistiques sur toutes les colonnes de toutes les tables après l’exécution de SACT et toutes les modifications importantes se produisent dans les données. Pour plus d’informations, consultez [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).

[SET ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/statements/set-rowcount-transact-sql.md) n’a aucun effet sur SACT. Pour obtenir un comportement similaire, utilisez [TOP &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
 
Pour plus d’informations, consultez [Limitations et Restrictions](https://msdn.microsoft.com/library/mt203953/#LimitationsRestrictions) dans CREATE TABLE.

<a name="locking-behavior-bk"></a>
  
## <a name="locking-behavior"></a>Comportement de verrouillage  
 Pour plus d’informations, consultez [comportement de verrouillage](https://msdn.microsoft.com/library/mt203953/#LockingBehavior) dans CREATE TABLE.
 
<a name="performance-bk"></a>
 
 ## <a name="performance"></a>Performance 

Pour une table de hachage distribué, vous pouvez utiliser SACT pour choisir une colonne différente de distribution pour obtenir de meilleures performances pour les jointures et agrégations. Si vous choisissez qu'une colonne de distribution différent n’est pas votre objectif, vous devez les meilleurs SACT si vous spécifiez la même colonne de distribution dans la mesure où cela évitera de redistribution de manière unique les lignes. 

Si vous utilisez SACT pour créer la table et de performances ne sont pas un facteur, vous pouvez spécifier `ROUND_ROBIN` pour éviter d’avoir à choisir une colonne de distribution.

Pour éviter le déplacement des données dans les requêtes suivantes, vous pouvez spécifier `REPLICATE` au prix de stockage pour le chargement d’une copie complète de la table sur chaque nœud de calcul.  


<a name="examples-copy-table-bk"></a>

## <a name="examples-for-copying-a-table"></a>Exemples pour la copie d’une table

<a name="ctas-copy-table-bk"></a>

### <a name="a-use-ctas-to-copy-a-table"></a>A. Utilisez SACT pour copier une table 
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse

Par exemple le plus souvent utilisé pour `CTAS` crée une copie d’une table afin que vous puissiez modifier le DDL. Si par exemple vous avez créé votre table en tant que `ROUND_ROBIN` et maintenant que vous souhaitez modifier dans une table distribuée sur une colonne, `CTAS` est la façon de modifier la colonne de distribution. `CTAS`peut également être utilisé pour modifier les types de partitionnement, l’indexation ou de colonne.

Supposons que vous avez créé cette table en utilisant le type de distribution par défaut de `ROUND_ROBIN` distribuées car aucune colonne de distribution a été spécifié dans le `CREATE TABLE`.

```sql
CREATE TABLE FactInternetSales
(
    ProductKey int NOT NULL,
    OrderDateKey int NOT NULL,
    DueDateKey int NOT NULL,
    ShipDateKey int NOT NULL,
    CustomerKey int NOT NULL,
    PromotionKey int NOT NULL,
    CurrencyKey int NOT NULL,
    SalesTerritoryKey int NOT NULL,
    SalesOrderNumber nvarchar(20) NOT NULL,
    SalesOrderLineNumber tinyint NOT NULL,
    RevisionNumber tinyint NOT NULL,
    OrderQuantity smallint NOT NULL,
    UnitPrice money NOT NULL,
    ExtendedAmount money NOT NULL,
    UnitPriceDiscountPct float NOT NULL,
    DiscountAmount float NOT NULL,
    ProductStandardCost money NOT NULL,
    TotalProductCost money NOT NULL,
    SalesAmount money NOT NULL,
    TaxAmt money NOT NULL,
    Freight money NOT NULL,
    CarrierTrackingNumber nvarchar(25),
    CustomerPONumber nvarchar(25)
);
```

Maintenant, vous souhaitez créer une copie de cette table avec un index columnstore en cluster afin que vous pouvez tirer parti des performances de tables columnstore en cluster. Également, vous souhaitez distribuer cette table sur ProductKey dans la mesure où vous comptez jointures sur cette colonne et que vous souhaitez éviter le déplacement des données au cours des jointures sur ProductKey. Enfin, vous souhaitez également ajouter le partitionnement sur OrderDateKey afin que vous pouvez rapidement supprimer les anciennes données en supprimant les anciennes partitions. Voici l’instruction SACT copiez votre ancienne table dans une nouvelle table.

```sql
CREATE TABLE FactInternetSales_new
WITH
(
    CLUSTERED COLUMNSTORE INDEX,
    DISTRIBUTION = HASH(ProductKey),
    PARTITION
    (
        OrderDateKey RANGE RIGHT FOR VALUES
        (
        20000101,20010101,20020101,20030101,20040101,20050101,20060101,20070101,20080101,20090101,
        20100101,20110101,20120101,20130101,20140101,20150101,20160101,20170101,20180101,20190101,
        20200101,20210101,20220101,20230101,20240101,20250101,20260101,20270101,20280101,20290101
        )
    )
)
AS SELECT * FROM FactInternetSales;
```

Enfin, vous pouvez renommer vos tables pour l’échange dans votre nouvelle table et puis supprimez votre ancienne table.

```sql
RENAME OBJECT FactInternetSales TO FactInternetSales_old;
RENAME OBJECT FactInternetSales_new TO FactInternetSales;

DROP TABLE FactInternetSales_old;
```

<a name="examples-column-bk"></a>

## <a name="examples-for-column-options"></a>Exemples d’options de colonne

<a name="ctas-change-column-attributes-bk"></a>

### <a name="b-use-ctas-to-change-column-attributes"></a>B. SACT permet de modifier les attributs de colonne 
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse

Cet exemple utilise SACT pour modifier les types de données, possibilité de valeur null et le classement de plusieurs colonnes dans la table DimCustomer2.  
  
```  
-- Original table 
CREATE TABLE [dbo].[DimCustomer2] (  
    [CustomerKey] int NOT NULL,  
    [GeographyKey] int NULL,  
    [CustomerAlternateKey] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL  
)  
WITH (CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH([CustomerKey]));  
  
-- CTAS example to change data types, nullability, and column collations  
CREATE TABLE test  
WITH (HEAP, DISTRIBUTION = ROUND_ROBIN)  
AS  
SELECT  
    CustomerKey AS CustomerKeyNoChange,  
    CustomerKey*1 AS CustomerKeyChangeNullable,  
    CAST(CustomerKey AS DECIMAL(10,2)) AS CustomerKeyChangeDataTypeNullable,  
    ISNULL(CAST(CustomerKey AS DECIMAL(10,2)),0) AS CustomerKeyChangeDataTypeNotNullable,  
    GeographyKey AS GeographyKeyNoChange,  
    ISNULL(GeographyKey,0) AS GeographyKeyChangeNotNullable,  
    CustomerAlternateKey AS CustomerAlternateKeyNoChange,  
    CASE WHEN CustomerAlternateKey = CustomerAlternateKey 
        THEN CustomerAlternateKey END AS CustomerAlternateKeyNullable,  
    CustomerAlternateKey COLLATE Latin1_General_CS_AS_KS_WS AS CustomerAlternateKeyChangeCollation  
FROM [dbo].[DimCustomer2]  
  
-- Resulting table 
CREATE TABLE [dbo].[test] (
    [CustomerKeyNoChange] int NOT NULL, 
    [CustomerKeyChangeNullable] int NULL, 
    [CustomerKeyChangeDataTypeNullable] decimal(10, 2) NULL, 
    [CustomerKeyChangeDataTypeNotNullable] decimal(10, 2) NOT NULL, 
    [GeographyKeyNoChange] int NULL, 
    [GeographyKeyChangeNotNullable] int NOT NULL, 
    [CustomerAlternateKeyNoChange] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL, 
    [CustomerAlternateKeyNullable] nvarchar(15) COLLATE SQL_Latin1_General_CP1_CI_AS NULL, 
    [CustomerAlternateKeyChangeCollation] nvarchar(15) COLLATE Latin1_General_CS_AS_KS_WS NOT NULL
)
WITH (DISTRIBUTION = ROUND_ROBIN);
```
 
Dans la dernière étape, vous pouvez utiliser [renommer &#40; Transact-SQL &#41; ](../../t-sql/statements/rename-transact-sql.md) pour basculer les noms de table. Cela rend DimCustomer2 être la nouvelle table.

```
RENAME OBJECT DimCustomer2 TO DimCustomer2_old;
RENAME OBJECT test TO DimCustomer2;

DROP TABLE DimCustomer2_old;
```

<a name="examples-table-distribution-bk"></a>

## <a name="examples-for-table-distribution"></a>Exemples pour la distribution de la table

<a name="ctas-change-distribution-method-bk"></a>

### <a name="c-use-ctas-to-change-the-distribution-method-for-a-table"></a>C. Utilisez SACT pour modifier la méthode de distribution pour une table
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse

Cet exemple montre comment modifier la méthode de distribution pour une table. Pour afficher les mécanismes de la procédure à suivre, il devient une table de hachage distribué alternée et puis modifications à la table alternée hachage distribué. La table finale correspond à la table d’origine. 

Dans la plupart des cas vous n’avez pas besoin de modifier une table de hachage distribué à une table de tourniquet. Plus souvent, vous devrez peut-être modifier une table de tourniquet pour une table de hachage distribuée. Par exemple, vous pouvez initialement charger une nouvelle table en tant qu’alternée et déplacer ultérieurement à une table de hachage distribué pour obtenir de meilleures performances de jointure.

Cet exemple utilise la base de données AdventureWorksDW. Pour charger la version de l’entrepôt de données SQL, consultez [charger des exemples de données dans l’entrepôt de données SQL](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-load-sample-databases/)
 
```
-- DimSalesTerritory is hash-distributed.
-- Copy it to a round-robin table.
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN  
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];

```  
Ensuite, modifiez à une table de hachage distribuée.

```
-- You just made DimSalesTerritory a round-robin table.
-- Change it back to the original hash-distributed table. 
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH(SalesTerritoryKey) 
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];
```
 
<a name="ctas-change-to-replicated-bk"></a>

### <a name="d-use-ctas-to-convert-a-table-to-a-replicated-table"></a>D. Permet de convertir une table à une table répliquée SACT  
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse 

Cet exemple s’applique pour la conversion des tables de hachage distribué ou de tourniquet à une table répliquée. Cet exemple utilise la méthode précédente de la modification de la distribution type plus loin.  DimSalesTerritory étant une dimension et probablement une plus petite table, vous pouvez choisir de recréer la table comme étant répliqués pour éviter le déplacement des données lors de la jointure à d’autres tables. 

```
-- DimSalesTerritory is hash-distributed.
-- Copy it to a replicated table.
CREATE TABLE [dbo].[myTable]   
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = REPLICATE 
  )  
AS SELECT * FROM [dbo].[DimSalesTerritory]; 

-- Switch table names

RENAME OBJECT [dbo].[DimSalesTerritory] to [DimSalesTerritory_old];
RENAME OBJECT [dbo].[myTable] TO [DimSalesTerritory];

DROP TABLE [dbo].[DimSalesTerritory_old];
```
 
### <a name="e-use-ctas-to-create-a-table-with-fewer-columns"></a>E. SACT permet de créer une table avec moins de colonnes
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse 

L’exemple suivant crée une table distribuée alternée nommée `myTable (c, ln)`. La nouvelle table contient uniquement deux colonnes. Il utilise les alias de colonne dans l’instruction SELECT pour les noms des colonnes.  
  
```  
CREATE TABLE myTable  
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN  
  )  
AS SELECT CustomerKey AS c, LastName AS ln  
    FROM dimCustomer;  
  
```  

<a name="examples-query-hints-bk"></a>

## <a name="examples-for-query-hints"></a>Exemples d’indicateurs de requête

<a name="ctas-query-hint-bk"></a>

### <a name="f-use-a-query-hint-with-create-table-as-select-ctas"></a>F. Utilisez un indicateur de requête avec CREATE TABLE AS sélectionnez (SACT)  
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse
  
Cette requête affiche la syntaxe de base pour l’utilisation d’un indicateur de jointure de requête avec l’instruction SACT. Une fois la requête est envoyée, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] s’applique la stratégie de jointure de hachage lorsqu’il génère le plan de requête pour chaque point de distribution individuel. Pour plus d’informations sur l’indicateur de requête de jointure de hachage, consultez [Clause OPTION &#40; Transact-SQL &#41; ](../../t-sql/queries/option-clause-transact-sql.md).  
  
```  
CREATE TABLE dbo.FactInternetSalesNew  
WITH   
  (   
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = ROUND_ROBIN   
  )  
AS SELECT T1.* FROM dbo.FactInternetSales T1 JOIN dbo.DimCustomer T2  
ON ( T1.CustomerKey = T2.CustomerKey )  
OPTION ( HASH JOIN );  
```  

<a name="examples-external-tables"></a>

## <a name="examples-for-external-tables"></a>Exemples pour les tables externes

<a name="ctas-azure-blob-storage-bk"></a>

### <a name="g-use-ctas-to-import-data-from-azure-blob-storage"></a>G. Utilisez SACT pour importer des données à partir du stockage d’objets Blob Azure  
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse  

Pour importer des données à partir d’une table externe, utilisez simplement CREATE TABLE AS SELECT pour sélectionner à partir de la table externe. La syntaxe permettant de sélectionner des données dans une table externe en [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] est identique à la syntaxe de sélection des données à partir d’une table normale.  
  
 L’exemple suivant définit une table externe des données dans un compte de stockage d’objets blob Azure. Il utilise ensuite le CREATE TABLE AS SELECT pour sélectionner à partir de la table externe. Il importe les données à partir des fichiers de texte délimité de stockage blob Azure et stocke les données dans un nouveau [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] table.  
  
```  
--Use your own processes to create the text-delimited files on Azure blob storage.  
--Create the external table called ClickStream.  
CREATE EXTERNAL TABLE ClickStreamExt (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
    LOCATION='/logs/clickstream/2015/',  
    DATA_SOURCE = MyAzureStorage,  
    FILE_FORMAT = TextFileFormat)  
;  
  
--Use CREATE TABLE AS SELECT to import the Azure blob storage data into a new   
--SQL Data Warehouse table called ClickStreamData  
CREATE TABLE ClickStreamData   
WITH  
  (  
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH (user_IP)  
  )  
AS SELECT * FROM ClickStreamExt  
;  
```  

<a name="ctas-import-Hadoop-bk"></a>
  
### <a name="h-use-ctas-to-import-hadoop-data-from-an-external-table"></a>H. Utilisez SACT pour importer des données Hadoop à partir d’une table externe  
S’applique à :[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
Pour importer des données à partir d’une table externe, utilisez simplement CREATE TABLE AS SELECT pour sélectionner à partir de la table externe. La syntaxe permettant de sélectionner des données dans une table externe en [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] est identique à la syntaxe de sélection des données à partir d’une table normale.  
  
 L’exemple suivant définit une table externe sur un cluster Hadoop. Il utilise ensuite le CREATE TABLE AS SELECT pour sélectionner à partir de la table externe. Il importe les données à partir des fichiers de texte délimité Hadoop et stocke les données dans un nouveau [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] table.  
  
```  
-- Create the external table called ClickStream.  
CREATE EXTERNAL TABLE ClickStreamExt (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
    LOCATION = 'hdfs://MyHadoop:5000/tpch1GB/employee.tbl',  
    FORMAT_OPTIONS ( FIELD_TERMINATOR = '|')  
)  
;  
  
-- Use your own processes to create the Hadoop text-delimited files 
-- on the Hadoop Cluster.  
  
-- Use CREATE TABLE AS SELECT to import the Hadoop data into a new 
-- table called ClickStreamPDW  
CREATE TABLE ClickStreamPDW   
WITH  
  (  
    CLUSTERED COLUMNSTORE INDEX,  
    DISTRIBUTION = HASH (user_IP)  
  )  
AS SELECT * FROM ClickStreamExt  
;   
```  
 
<a name="examples-workarounds-bk"></a>
 
## <a name="examples-using-ctas-to-replace-sql-server-code"></a>Exemples d’utilisation de SACT pour remplacer le code de SQL Server

SACT permet de contourner certaines fonctionnalités non prises en charge. En plus de pouvoir exécuter votre code dans l’entrepôt de données, une réécriture du code existant pour utiliser SACT généralement améliore les performances. Il s’agit d’un résultat de sa conception entièrement parallélisée. 

> [!NOTE]
> Essayez de vous demander « SACT premier ». Si vous pensez que vous pouvez résoudre un problème à l’aide `CTAS` puis qui est généralement la meilleure approche, même si vous écrivez des données en conséquence.
>

<a name="ctas-replace-select-into-bk"></a>

### <a name="i-use-ctas-instead-of-selectinto"></a>I. Utilisez SACT au lieu de sélectionner... DANS  
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse

Code de SQL Server utilise généralement SELECT... INTO pour remplir une table avec les résultats d’une instruction SELECT. Il s’agit d’un exemple d’un serveur SQL SELECT... DANS l’instruction.

```sql
SELECT *
INTO    #tmp_fct
FROM    [dbo].[FactInternetSales]
```

Cette syntaxe n’est pas pris en charge dans SQL Data Warehouse et Parallel Data Warehouse. Cet exemple montre comment réécrivez l’instruction SELECT précédente... DANS l’instruction comme une instruction SACT. Vous pouvez choisir l’une des options de DISTRIBUTION décrites dans la syntaxe SACT. Cet exemple utilise la méthode de distribution ROUND_ROBIN.

```sql
CREATE TABLE #tmp_fct
WITH
(
    DISTRIBUTION = ROUND_ROBIN
)
AS
SELECT  *
FROM    [dbo].[FactInternetSales]
;
```

<a name="ctas-replace-implicit-joins-bk"></a>

### <a name="j-use-ctas-and-implicit-joins-to-replace-ansi-joins-in-the-from-clause-of-an-update-statement"></a>J. Permet de remplacer des jointures ANSI dans SACT et jointures implicites le `FROM` clause d’une `UPDATE` instruction  
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse  

Vous pouvez trouver qu'une mise à jour complexes qui s’attache à l’aide de ANSI syntaxe de jointure pour effectuer la mise à jour ou la suppression de plus de deux tables.

Imaginez que vous deviez mettre à jour cette table :

```sql
CREATE TABLE [dbo].[AnnualCategorySales]
(   [EnglishProductCategoryName]    NVARCHAR(50)    NOT NULL
,   [CalendarYear]                  SMALLINT        NOT NULL
,   [TotalSalesAmount]              MONEY           NOT NULL
)
WITH
(
    DISTRIBUTION = ROUND_ROBIN
)
;
```

La requête d’origine peut avoir recherché quelque chose comme ceci :

```sql
UPDATE  acs
SET     [TotalSalesAmount] = [fis].[TotalSalesAmount]
FROM    [dbo].[AnnualCategorySales]     AS acs
JOIN    (
        SELECT  [EnglishProductCategoryName]
        ,       [CalendarYear]
        ,       SUM([SalesAmount])              AS [TotalSalesAmount]
        FROM    [dbo].[FactInternetSales]       AS s
        JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
        JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
        JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
        JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
        WHERE   [CalendarYear] = 2004
        GROUP BY
                [EnglishProductCategoryName]
        ,       [CalendarYear]
        ) AS fis
ON  [acs].[EnglishProductCategoryName]  = [fis].[EnglishProductCategoryName]
AND [acs].[CalendarYear]                = [fis].[CalendarYear]
;
```

Étant donné que l’entrepôt de données SQL ne prend pas en charge les jointures de ANSI dans les `FROM` clause d’une `UPDATE` instruction, vous ne pouvez pas utiliser ce code de SQL Server sur sans quelques modifications apportées.

Vous pouvez utiliser une combinaison d’un `CTAS` et une jointure implicite pour remplacer ce code :

```sql
-- Create an interim table
CREATE TABLE CTAS_acs
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT  ISNULL(CAST([EnglishProductCategoryName] AS NVARCHAR(50)),0)    AS [EnglishProductCategoryName]
,       ISNULL(CAST([CalendarYear] AS SMALLINT),0)                      AS [CalendarYear]
,       ISNULL(CAST(SUM([SalesAmount]) AS MONEY),0)                     AS [TotalSalesAmount]
FROM    [dbo].[FactInternetSales]       AS s
JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
WHERE   [CalendarYear] = 2004
GROUP BY
        [EnglishProductCategoryName]
,       [CalendarYear]
;

-- Use an implicit join to perform the update
UPDATE  AnnualCategorySales
SET     AnnualCategorySales.TotalSalesAmount = CTAS_ACS.TotalSalesAmount
FROM    CTAS_acs
WHERE   CTAS_acs.[EnglishProductCategoryName] = AnnualCategorySales.[EnglishProductCategoryName]
AND     CTAS_acs.[CalendarYear]               = AnnualCategorySales.[CalendarYear]
;

--Drop the interim table
DROP TABLE CTAS_acs
;
```

<a name="ctas-replace-ansi-joins-bk"></a>

### <a name="k-use-ctas-to-specify-which-data-to-keep-instead-of-using-ansi-joins-in-the-from-clause-of-a-delete-statement"></a>K. SACT permet de spécifier les données à conserver au lieu d’utiliser ANSI joint dans la clause FROM d’une instruction DELETE  
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse  

Parfois, la meilleure approche pour la suppression des données consiste à utiliser `CTAS`. Au lieu de simplement la suppression des données, sélectionnez les données que vous souhaitez conserver. Cette particulièrement vrai pour `DELETE` instructions qui utilisent ansi jointures de la syntaxe de jointure depuis l’entrepôt de données SQL ne prend pas en charge ANSI dans les `FROM` clause d’un `DELETE` instruction.

Un exemple d’une instruction DELETE converti est le suivant :

```sql
CREATE TABLE dbo.DimProduct_upsert
WITH
(   Distribution=HASH(ProductKey)
,   CLUSTERED INDEX (ProductKey)
)
AS -- Select Data you wish to keep
SELECT     p.ProductKey
,          p.EnglishProductName
,          p.Color
FROM       dbo.DimProduct p
RIGHT JOIN dbo.stg_DimProduct s
ON         p.ProductKey = s.ProductKey
;

RENAME OBJECT dbo.DimProduct        TO DimProduct_old;
RENAME OBJECT dbo.DimProduct_upsert TO DimProduct;
```

<a name="ctas-simplify-merge-bk"></a>

### <a name="l-use-ctas-to-simplify-merge-statements"></a>L. Permet de simplifier les instructions merge SACT  
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse  

Instructions de fusion peuvent être remplacées, au moins en partie, à l’aide de `CTAS`. Vous pouvez consolider les `INSERT` et `UPDATE` dans une instruction unique. Tous les enregistrements supprimés doit être clôturé dans une deuxième instruction.

Un exemple d’un `UPSERT` est le suivant :

```sql
CREATE TABLE dbo.[DimProduct_upsert]
WITH
(   DISTRIBUTION = HASH([ProductKey])
,   CLUSTERED INDEX ([ProductKey])
)
AS
-- New rows and new versions of rows
SELECT      s.[ProductKey]
,           s.[EnglishProductName]
,           s.[Color]
FROM      dbo.[stg_DimProduct] AS s
UNION ALL  
-- Keep rows that are not being touched
SELECT      p.[ProductKey]
,           p.[EnglishProductName]
,           p.[Color]
FROM      dbo.[DimProduct] AS p
WHERE NOT EXISTS
(   SELECT  *
    FROM    [dbo].[stg_DimProduct] s
    WHERE   s.[ProductKey] = p.[ProductKey]
)
;

RENAME OBJECT dbo.[DimProduct]          TO [DimProduct_old];
RENAME OBJECT dbo.[DimpProduct_upsert]  TO [DimProduct];

```

<a name="ctas-data-type-and-nullability-bk"></a>

### <a name="m-explicitly-state-data-type-and-nullability-of-output"></a>M. Déclarer explicitement le type de données et la possibilité de valeur null de sortie  
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse  

Lorsque vous migrez le code SQL Server à SQL Data Warehouse, vous constaterez que vous exécutez sur ce type de modèle de codage :

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455

CREATE TABLE result
(result DECIMAL(7,2) NOT NULL
)
WITH (DISTRIBUTION = ROUND_ROBIN)

INSERT INTO result
SELECT @d*@f
;
```

Vous pensez instinctivement vous devez migrer ce code à un SACT et vous serait correcte. Toutefois, il existe un masqué problème ici.

Le code suivant ne génère pas le même résultat :

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455
;

CREATE TABLE ctas_r
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT @d*@f as result
;
```

Notez que la colonne « result » reprend les valeurs de type et la possibilité de valeur NULL des données de l’expression. Cela peut entraîner subtiles écarts dans les valeurs si vous ne faites pas attention.

Essayez ce qui suit comme exemple :

```sql
SELECT result,result*@d
from result
;

SELECT result,result*@d
from ctas_r
;
```

La valeur stockée pour le résultat est différente. L’erreur devient importante, plus la valeur persistante dans la colonne de résultats est utilisée dans d’autres expressions.

![Résultats de CREATE TABLE AS SELECT](../../t-sql/statements/media/create-table-as-select-results.png)

Cela est particulièrement important pour les migrations de données. Bien que la seconde requête est sans doute plus précise, il existe un problème. Les données doivent être différentes par rapport au système source et qui mène aux questions de l’intégrité de la migration. Il s’agit d’une des ces rares cas où la réponse « incorrecte » est réellement celui qui convient !

La raison pour laquelle que nous voir cette disparité entre les deux résultats est à effectuer un cast de type implicite. Dans le premier exemple, le tableau définit la définition de colonne. Lorsque la ligne est insérée une conversion de type implicite se produit. Dans le deuxième exemple il n’existe aucune conversion de type implicite comme l’expression définit le type de données de la colonne. Notez également que la colonne dans le deuxième exemple a été définie comme une colonne acceptant les valeurs NULL, tandis que dans le premier exemple il n’a pas. Lorsque la table a été créée dans les valeurs de colonne NULL premier exemple a été définie explicitement. Dans le deuxième exemple qu'il simplement était à l’expression et, par défaut cela aurait pour résultat dans une définition de valeur NULL.  

Pour résoudre ces problèmes vous devez définir explicitement la conversion de type et la possibilité de valeur NULL dans le `SELECT` partie de la `CTAS` instruction. Vous ne pouvez pas définir ces propriétés dans la partie de la table create.

L’exemple ci-dessous montre comment la corriger le code :

```sql
DECLARE @d decimal(7,2) = 85.455
,       @f float(24)    = 85.455

CREATE TABLE ctas_r
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT ISNULL(CAST(@d*@f AS DECIMAL(7,2)),0) as result
```

Notez les points suivants :
- CAST ou CONVERT pourrait avoir été utilisé
- ISNULL est utilisée pour forcer la possibilité de valeur null pas COALESCE
- ISNULL est la fonction externe
- La deuxième partie de la ISNULL est une constante c'est-à-dire 0

> [!NOTE]
> La possibilité de valeur null à définir correctement il est essentiel d’utiliser `ISNULL` et non `COALESCE`. `COALESCE`n’est pas une fonction déterministe et par conséquent, le résultat de l’expression sera toujours NULLable. `ISNULL`est différent. Elle est déterministe. Par conséquent, lors de la deuxième partie de la `ISNULL` la fonction est une constante ou un littéral, la valeur résultante est non NULL.

Ce Conseil n’est pas seulement utile pour assurer l’intégrité de vos calculs. Il est également important pour le basculement de partition de table. Imaginez que vous disposez de cette table définie en tant que votre fait :

```sql
CREATE TABLE [dbo].[Sales]
(
    [date]      INT     NOT NULL
,   [product]   INT     NOT NULL
,   [store]     INT     NOT NULL
,   [quantity]  INT     NOT NULL
,   [price]     MONEY   NOT NULL
,   [amount]    MONEY   NOT NULL
)
WITH
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101,20020101
                    ,20030101,20040101,20050101
                    )
                )
)
;
```

Toutefois, le champ de valeur est une expression calculée, il n’est pas partie de la source de données.

Pour créer votre jeu de données partitionné, vous pouvez souhaiter procéder :

```sql
CREATE TABLE [dbo].[Sales_in]
WITH    
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101
                    )
                )
)
AS
SELECT
    [date]    
,   [product]
,   [store]
,   [quantity]
,   [price]   
,   [quantity]*[price]  AS [amount]
FROM [stg].[source]
OPTION (LABEL = 'CTAS : Partition IN table : Create')
;
```

La requête s’exécute parfaitement. Un problème se pose lorsque vous essayez d’effectuer le basculement de partition. Les définitions de table ne correspondent pas. Pour rendre les définitions de table correspond à la SACT doit être modifiée.

```sql
CREATE TABLE [dbo].[Sales_in]
WITH    
(   DISTRIBUTION = HASH([product])
,   PARTITION   (   [date] RANGE RIGHT FOR VALUES
                    (20000101,20010101
                    )
                )
)
AS
SELECT
    [date]    
,   [product]
,   [store]
,   [quantity]
,   [price]   
,   ISNULL(CAST([quantity]*[price] AS MONEY),0) AS [amount]
FROM [stg].[source]
OPTION (LABEL = 'CTAS : Partition IN table : Create');
```

Par conséquent, vous pouvez voir que la cohérence des types et la gestion des propriétés de la possibilité de valeur NULL sur un SACT est meilleure ingénierie recommandé. Il vous aide à maintenir l’intégrité de vos calculs et garantit également que le basculement de partition est possible.
 
## <a name="see-also"></a>Voir aussi  
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
 [CREATE EXTERNAL TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CRÉER une TABLE &#40; Entrepôt de données SQL Azure &#41; ](../../t-sql/statements/create-table-azure-sql-data-warehouse.md) [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [DROP EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [ALTER EXTERNAL TABLE &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/4ae1b23c-67f6-41d0-b614-7a8de914d145)  
  
  


