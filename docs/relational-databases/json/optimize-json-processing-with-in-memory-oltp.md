---
title: "Optimiser le traitement JSON avec OLTP en mémoire | Microsoft Docs"
ms.custom: 
ms.date: 02/03/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9c5adb1-3209-4186-bc10-8e41a26f5e57
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4e0331c288665fd9f69444d0d14366dfa69a668f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="optimize-json-processing-with-in-memory-oltp"></a>Optimiser le traitement JSON avec OLTP en mémoire
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

SQL Server et Azure SQL Database vous permettent de travailler avec du texte au format JSON. Pour améliorer les performances de vos requêtes OLTP qui traitent des données JSON, vous pouvez stocker des documents JSON dans des tables optimisées en mémoire en utilisant des colonnes de chaîne standard (type NVARCHAR).

## <a name="store-json-in-memory-optimized-tables"></a>Stocker des données JSON dans des tables optimisées en mémoire
L’exemple suivant montre une table optimisée en mémoire `Product` avec deux colonnes JSON, `Tags` et `Data` :

```tsql
CREATE SCHEMA xtp;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED, --standard column
    Name nvarchar(400) NOT NULL, --standard column
    Price float, --standard column

    Tags nvarchar(400),--json stored in string column
    Data nvarchar(4000) --json stored in string column

) WITH (MEMORY_OPTIMIZED=ON);
```
Le stockage des données JSON dans des tables optimisées en mémoire améliore les performances des requêtes en tirant parti de l’accès aux données en mémoire sans verrou.

## <a name="optimize-json-with-additional-in-memory-features"></a>Optimiser JSON avec des fonctionnalités en mémoire supplémentaires
Les nouvelles fonctionnalités disponibles dans SQL Server et Azure SQL Database vous permettent d’intégrer les fonctionnalités JSON avec les technologies OLTP en mémoire existantes. Vous pouvez par exemple effectuer les opérations suivantes :
 - valider la structure des documents JSON stockés dans des tables optimisées en mémoire à l’aide des contraintes CHECK compilées en mode natif ;
 - exposer et typer fortement les valeurs stockées dans les documents JSON à l’aide de colonnes calculées ;
 - indexer les valeurs des documents JSON à l’aide d’index optimisés en mémoire ;
 - compiler en mode natif les requêtes SQL qui utilisent des valeurs de documents JSON ou mettre en forme les résultats au format de texte JSON.

## <a name="validate-json-columns"></a>Valider des colonnes JSON
SQL Server et Azure SQL Database vous permettent d’ajouter des contraintes CHECK compilées en mode natif qui valident le contenu de documents JSON stockés dans une colonne de chaîne, comme indiqué dans l’exemple suivant.

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Tags nvarchar(400)
            CONSTRAINT [Tags should be formatted as JSON]
                CHECK (ISJSON(Tags)=1),
    Data nvarchar(4000)

) WITH (MEMORY_OPTIMIZED=ON);
```

La contrainte CHECK compilée en mode natif peut être ajoutée à des tables existantes qui contiennent des colonnes JSON :

```tsql
ALTER TABLE xtp.Product
    ADD CONSTRAINT [Data should be JSON]
        CHECK (ISJSON(Data)=1)
```

Avec les contraintes JSON CHECK compilées en mode natif, vous pouvez faire en sorte que le texte JSON stocké dans vos tables optimisées en mémoire soit correctement mis en forme.

## <a name="expose-json-values-using-computed-columns"></a>Exposer les valeurs JSON à l’aide de colonnes calculées
Les colonnes calculées vous permettent d’exposer les valeurs d’un texte JSON et d’accéder à ces valeurs sans avoir à réévaluer les expressions qui extraient une valeur du texte JSON ni à analyser de nouveau la structure JSON. Les valeurs exposées sont fortement typées et conservés physiquement dans les colonnes calculées. L’accès aux valeurs JSON à l’aide de colonnes calculées persistantes est plus rapide que l’accès aux valeurs dans le document JSON.

L’exemple suivant montre comment exposer les deux valeurs suivantes à partir de la colonne JSON `Data` :
-   Le pays où un produit est fabriqué.
-   Le coût de fabrication du produit.

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float)

) WITH (MEMORY_OPTIMIZED=ON);
```

Les colonnes calculées `MadeIn` et `Cost` sont mises à jour chaque fois que le document JSON stocké dans la colonne `Data` est modifié.

## <a name="index-values-in-json-columns"></a>Valeurs d’index dans les colonnes JSON
SQL Server et Azure SQL Database vous permettent d’indexer les valeurs des colonnes JSON à l’aide des index optimisés en mémoire. Les valeurs JSON qui sont indexées doivent être exposées et fortement typées à l’aide de colonnes calculées, comme illustré dans l’exemple suivant.

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float) PERSISTED,

    INDEX [idx_Product_MadeIn] NONCLUSTERED (MadeIn)

) WITH (MEMORY_OPTIMIZED=ON)

ALTER TABLE Product
    ADD INDEX [idx_Product_Cost] NONCLUSTERED HASH(Cost)
        WITH (BUCKET_COUNT=20000)
```
Les valeurs des colonnes JSON peuvent être indexées à l’aide des index standard NONCLUSTERED et HASH.
-   Les index NONCLUSTERED optimisent les requêtes qui sélectionnent des plages de lignes selon une valeur JSON ou trient les résultats par valeurs JSON.
-   Les index HASH offrent des performances optimales lorsqu’une ou plusieurs lignes sont extraites en spécifiant la valeur exacte à rechercher.

## <a name="native-compilation-of-json-queries"></a>Compilation native des requêtes JSON
Enfin, la compilation native des procédures, des fonctions et des déclencheurs Transact-SQL qui contiennent des requêtes avec des fonctions JSON améliore les performances des requêtes et réduit les cycles processeur requis pour exécuter les procédures. L’exemple suivant montre une procédure compilée en mode natif qui utilise plusieurs fonctions JSON - JSON_VALUE, OPENJSON et JSON_MODIFY.

```tsql
CREATE PROCEDURE xtp.ProductList(@ProductIds nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    SELECT ProductID,Name,Price,Data,Tags, JSON_VALUE(data,'$.MadeIn') AS MadeIn
    FROM xtp.Product
        JOIN OPENJSON(@ProductIds)
            ON ProductID = value

END;

CREATE PROCEDURE xtp.UpdateProductData(@ProductId int, @Property nvarchar(100), @Value nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    UPDATE xtp.Product
    SET Data = JSON_MODIFY(Data, @Property, @Value)
    WHERE ProductID = @ProductId;

END
```

## <a name="next-steps"></a>Étapes suivantes
JSON dans les modules natifs OLTP en mémoire améliore les performances de la fonctionnalité JSON intégrée qui est disponible dans SQL Server et Azure SQL Database.

Pour en savoir plus sur les principaux scénarios d’utilisation de JSON, consultez les ressources suivantes :

-   [Blog TechNet](https://blogs.technet.microsoft.com/dataplatforminsider/2016/01/05/json-in-sql-server-2016-part-1-of-4/)
-   [Documentation MSDN](https://msdn.microsoft.com/library/dn921897.aspx)
-   [Vidéo Channel 9](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

Pour en savoir plus sur les différents scénarios d’intégration de JSON dans votre application, consultez les ressources suivantes :
-   Regardez les démonstrations de cette [vidéo Channel 9](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds).
-   Recherchez un scénario correspondant à votre cas d’usage dans les [billets de blog sur JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/).
-   Recherchez des exemples dans notre [référentiel GitHub](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/json/).


