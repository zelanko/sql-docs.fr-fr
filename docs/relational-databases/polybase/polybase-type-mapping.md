---
title: Mappage des types avec PolyBase | Microsoft Docs
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: aboke
manager: craigg
ms.openlocfilehash: 67ecc3a75da04849d6b23d0b07f6e650c2825b0b
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67731794"
---
# <a name="type-mapping-with-polybase"></a>Mappage des types avec PolyBase

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit le mappage entre des sources de données externes PolyBase et SQL Server. Vous pouvez utiliser ces informations pour définir correctement les tables externes avec la commande Transact-SQL [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).

## <a name="overview"></a>Vue d’ensemble

Lors de la création d’une table externe avec PolyBase, les définitions de colonne, notamment les types de données et le nombre de colonnes, doivent correspondre aux données des fichiers externes. En cas de non correspondance, les lignes du fichier sont rejetées lors de l’interrogation des données.  
  
Pour les tables externes qui référencent des fichiers provenant de sources de données externes, les définitions de colonne et de type doivent correspondre exactement au schéma du fichier externe. Lorsque vous définissez des types de données qui référencent des données stockées dans Hadoop/Hive, utilisez les mappages suivants entre les types de données SQL et Hive, et castez le type en un type de données SQL lorsque vous sélectionnez des données. Les types incluent toutes les versions de Hive, sauf indication contraire.

> [!NOTE]  
> SQL Server ne prend pas en charge la valeur de données *infinie* Hive lors des conversions. Si vous l’utilisez, PolyBase échoue et émet une erreur de conversion de type de données.

## <a name="hadoop-type-mapping-reference"></a>Informations de référence sur le mappage des types Hadoop

| Type de données SQL | Type de données .NET            | Type de données Hive | Type de données Hadoop/Java | Commentaires                       |
| ------------- | ------------------------- | -------------- | --------------------- | ------------------------------ |
| TINYINT       | Byte                      | TINYINT        | ByteWritable          | Pour les nombres non signés.     |
| SMALLINT      | Int16                     | SMALLINT       | ShortWritable         |
| INT           | Int32                     | INT            | IntWritable           |
| BIGINT        | Int64                     | BIGINT         | LongWritable          |
| bit           | Booléen                   | boolean        | BooleanWritable       |
| FLOAT         | Double                    | double         | DoubleWritable        |
| REAL          | Unique                    | FLOAT          | FloatWritable         |
| money         | Décimal                   | double         | DoubleWritable        |
| SMALLMONEY    | Décimal                   | double         | DoubleWritable        |
| NCHAR         | String<br /><br /> Char[] | chaîne         | Varchar               |
| NVARCHAR      | String<br /><br /> Char[] | chaîne         | Varchar               |
| char          | String<br /><br /> Char[] | chaîne         | Varchar               |
| varchar       | String<br /><br /> Char[] | chaîne         | Varchar               |
| binary        | Byte[]                    | binary         | BytesWritable         | S’applique à Hive 0.8 et versions ultérieures |
| varbinary     | Byte[]                    | binary         | BytesWritable         | S’applique à Hive 0.8 et versions ultérieures |
| Date          | DateTime                  | TIMESTAMP      | TimestampWritable     |
| smalldatetime | DateTime                  | TIMESTAMP      | TimestampWritable     |
| datetime2     | DateTime                  | TIMESTAMP      | TimestampWritable     |
| DATETIME      | DateTime                  | TIMESTAMP      | TimestampWritable     |
| time          | TimeSpan                  | TIMESTAMP      | TimestampWritable     |
| Décimal       | Décimal                   | Décimal        | BigDecimalWritable    | S’applique à Hive 0.11 et versions ultérieures |

<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

## <a name="oracle-type-mapping-reference"></a>Informations de référence sur le mappage des types Oracle

| Type de données Oracle | Type SQL Server | 
| -------------    | --------------- |
|float             |float            |
|NUMBER            |Décimal          |
|LONG              |nvarchar         |
|BINARY_FLOAT      |Real             | 
|BINARY_DOUBLE     |float            | 
|CHAR              |Char             |
|VARCHAR2          |Varchar          | 
|NVARCHAR2         |nvarchar         | 
|RAW               |Varbinary        |
|LONG RAW          |Varbinary        | 
|BLOB              |Varbinary        |
|CLOB              |Varchar          |
|NCLOB             | nvarchar        | 
|ROWID             |Varchar          |
|UROWID            |Varchar          | 
|DATE              |Datetime2        |
|timestamp         |Datetime2        | 

**Incompatibilité des types** 

**Float :** Oracle prend en charge une précision en virgule flottante de 126, ce qui est considérablement inférieur à ce que SQL Server prend en charge (53). Ainsi, **Float (1-53)** peut être mappé directement. Au delà, des données sont perdues en raison de la troncation.

**TimeStamp :** Timestamp et Timestamp with local timezone dans Oracle prennent une précision de 9 décimales pour les secondes, tandis que le type SQL Server DateTime2 prend en charge une précision de seulement 7 décimales. 




## <a name="mongodb-type-mapping"></a>Mappage de type MongoDB

| Type de données BSON     | Type SQL Server |
| ------------------ | --------------- |
| Double             | float           |
| String             | nvarchar        |
| Données binaires        | nvarchar        |
| ID de l'objet          | nvarchar        |
| Booléen            | bit             |
| Date               | Datetime2       |
| Entier de 32 bits     | Int             |
| Horodateur          | nvarchar        |
| Entier de 64 bits     | BigInt          |
|Decimal 128         | Décimal         | 
| DBPointer          | nvarchar        |
| Javascript         | nvarchar        |
| Clé maximale            | nvarchar        |
| Clé minimale            | nvarchar        |
| Symbole             | nvarchar        |
| Expression régulière | nvarchar        |
| Non défini/NULL     | nvarchar        |


MongoDB utilise les documents BSON pour stocker les enregistrements de données. Contrairement aux scénarios précédents, BSON est sans schéma et prend en charge l’incorporation de documents et de tableaux dans d’autres documents. Cela apporte plus de souplesse à l’utilisateur. 


## <a name="teradata-type-mapping-reference"></a>Informations de référence sur le mappage des types Teradata

| Type de données Teradata | Type SQL Server | 
| -------------      | -------------   |
|INTEGER             |Int              |
|SMALLINT            |SmallInt         |
|bigint              |BigInt           |
|BYTEINT             |SmallInt         |
|DECIMAL             |Décimal          |
|FLOAT               |Décimal          |
|BYTE                |Binaire           |
|VARBYTE             |Varbinary        |
|BLOB                |varbinary        |
|CHAR                |Nchar            |
|CLOB                |nvarchar         |
|VARCHAR             |nvarchar         |
|Graphic             |Nchar            |
|JSON                |nvarchar         |
|VARGRAPHIC          |nvarchar         |
|DATE                |Date             |
|timestamp           |Datetime2        |
|TIME                |Time             |
|TIME WITH TIME ZONE |Time             |
|TIMESTAMP WITH TIME ZONE|Time         |

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’utilisation de ces paramètres, consultez l’article de référence sur Transact-SQL pour [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
