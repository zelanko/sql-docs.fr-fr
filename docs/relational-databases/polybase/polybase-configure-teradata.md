---
title: Configurer PolyBase pour accéder à des données externes dans Teradata | Microsoft Docs
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
ms.openlocfilehash: b1baf1655619a3bc4b61939e2de8310956c9678d
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874271"
---
# <a name="configure-polybase-to-access-external-data-in-teradata"></a>Configurer PolyBase pour accéder à des données externes dans Teradata

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’article explique comment utiliser PolyBase sur une instance SQL Server pour interroger des données externes dans Teradata.

## <a name="prerequisites"></a>Prérequis

Si vous n’avez pas installé PolyBase, consultez [Installation de PolyBase](polybase-installation.md). Cet article décrit les prérequis pour l’installation.

Pour utiliser PolyBase sur Teradata, VC++ Redistributable est nécessaire. 
 
## <a name="configure-an-external-table"></a>Configurer une table externe

Pour interroger les données d’une source de données Teradata, vous devez créer des tables externes pour référencer les données externes. Cette section fournit un exemple de code pour créer ces tables externes. 
 
Nous vous recommandons de créer des statistiques sur les colonnes de la table externe. En particulier celles utilisées pour les jointures, les filtres et les agrégats, pour des performances de requêtes optimales.

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
     CREATE DATABASE SCOPED CREDENTIAL TeradataCredentials 
     WITH IDENTITY = 'username', Secret = 'password'
     ```

1. Créez une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Spécifiez l’emplacement de la source de données externe et les informations d’identification pour Teradata.

     ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE TeradataInstance
    WITH ( 
    LOCATION = teradata://TeradataServer,
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = TeradataCredentials
    );

     ```

1. Créez des schémas pour les données externes.

     ```sql
     CREATE SCHEMA teradata;
     GO
     ```

1.  Créez des tables externes qui représentent les données stockées dans le système Teradata externe [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
     ```sql
     /*  LOCATION: Teradata table/view in '<database_name>.<object_name>' format
      *  DATA_SOURCE: the external data source, created above.
      */
     CREATE EXTERNAL TABLE teradata.lineitem(
      L_ORDERKEY INT NOT NULL,
      L_PARTKEY INT NOT NULL,
     L_SUPPKEY INT NOT NULL,
     L_LINENUMBER INT NOT NULL,
     L_QUANTITY DECIMAL(15,2) NOT NULL,
     L_EXTENDEDPRICE DECIMAL(15,2) NOT NULL,
     L_DISCOUNT DECIMAL(15,2) NOT NULL,
     L_TAX DECIMAL(15,2) NOT NULL,
     L_RETURNFLAG CHAR NOT NULL,
     L_LINESTATUS CHAR NOT NULL,
     L_SHIPDATE DATE NOT NULL,
     L_COMMITDATE DATE NOT NULL,
     L_RECEIPTDATE DATE NOT NULL,
     L_SHIPINSTRUCT CHAR(25) NOT NULL,
     L_SHIPMODE CHAR(10) NOT NULL,
     L_COMMENT VARCHAR(44) NOT NULL
     )
     WITH (
     LOCATION='tpch.lineitem',
     DATA_SOURCE=TeradataInstance
     );
     ```

1. Créez des statistiques sur une table externe pour des performances optimisées.

     ```sql
      CREATE STATISTICS LineitemOrderKeyStatistics ON teradata.lineitem(L_ORDERKEY) WITH FULLSCAN; 
      ```



## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur PolyBase, consultez [Vue d’ensemble de SQL Server PolyBase](polybase-guide.md).
