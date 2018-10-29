---
title: Configurer PolyBase pour accéder à des données externes dans Oracle | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 515a77ebc9e29ba6e629472b446b486355336e1c
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874285"
---
# <a name="configure-polybase-to-access-external-data-in-oracle"></a>Configurer PolyBase pour accéder à des données externes dans Oracle

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’article explique comment utiliser PolyBase sur une instance SQL Server pour interroger des données externes dans Oracle.

## <a name="prerequisites"></a>Conditions préalables requises

Si vous n’avez pas installé PolyBase, consultez [Installation de PolyBase](polybase-installation.md). Cet article décrit les prérequis pour l’installation.

## <a name="configure-an-external-table"></a>Configurer une table externe

Pour interroger les données d’une source de données Oracle, vous devez créer des tables externes pour référencer les données externes. Cette section fournit un exemple de code pour créer ces tables externes. 
 
Pour des performances de requêtes optimales, nous vous recommandons de créer des statistiques sur les colonnes de table externe, en particulier celles utilisées pour les jointures, les filtres et les agrégats.

Voici les objets de création qui vont être utilisés dans cette section :

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) 
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)


1. Créez une clé principale sur la base de données. C’est nécessaire pour chiffrer le secret des informations d’identification.

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
     ```

1. Créez des informations d’identification incluses dans l’étendue de la base de données.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
      CREATE DATABASE SCOPED CREDENTIAL OracleCredentials 
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. Créez une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Spécifiez l’emplacement de la source de données externe et les informations d’identification de la source de données Oracle.

     ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE OracleInstance
    WITH ( 
    LOCATION = oracle://OracleServer,
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = TeradataCredentials
    );

     ```

1. Créez des schémas pour les données externes.
 
     ```sql
     CREATE SCHEMA oracle;
     GO
     ```

1.  Créez des tables externes qui représentent les données stockées dans le système Oracle externe [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
      ```sql
      /*  LOCATION: Oracle table/view in '<database_name>.<schema_name>.<object_name>' format
     *  DATA_SOURCE: the external data source, created above.
     */
      CREATE EXTERNAL TABLE oracle.orders(
      [O_ORDERKEY] DECIMAL(38) NOT NULL,
     [O_CUSTKEY] DECIMAL(38) NOT NULL,
     [O_ORDERSTATUS] CHAR COLLATE Latin1_General_BIN NOT NULL,
     [O_TOTALPRICE] DECIMAL(15,2) NOT NULL,
     [O_ORDERDATE] DATETIME2(0) NOT NULL,
     [O_ORDERPRIORITY] CHAR(15) COLLATE Latin1_General_BIN NOT NULL,
     [O_CLERK] CHAR(15) COLLATE Latin1_General_BIN NOT NULL,
     [O_SHIPPRIORITY] DECIMAL(38) NOT NULL,
     [O_COMMENT] VARCHAR(79) COLLATE Latin1_General_BIN NOT NULL
     )
     WITH (
      LOCATION='TPCH..ORDERS',
      DATA_SOURCE=OracleInstance
     );
     ```

1. Créez des statistiques sur une table externe pour des performances optimisées.

     ```sql
      CREATE STATISTICS OrdersOrderKeyStatistics ON oracle.orders(O_ORDERKEY) WITH FULLSCAN;
     ```

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur PolyBase, consultez [Vue d’ensemble de SQL Server PolyBase](polybase-guide.md).
