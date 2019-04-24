---
title: Configurer PolyBase pour accéder à des données externes dans Oracle | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 4a7484acf7a63b5c2a6804e1f3f7914cabaf8524
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59476644"
---
# <a name="configure-polybase-to-access-external-data-in-oracle"></a>Configurer PolyBase pour accéder à des données externes dans Oracle

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’article explique comment utiliser PolyBase sur une instance SQL Server pour interroger des données externes dans Oracle.

## <a name="prerequisites"></a>Conditions préalables requises

Si vous n’avez pas installé PolyBase, consultez [Installation de PolyBase](polybase-installation.md).

## <a name="configure-an-external-table"></a>Configurer une table externe

Pour interroger les données d’une source de données Oracle, vous devez créer des tables externes pour référencer les données externes. Cette section fournit un exemple de code pour créer ces tables externes. 
 
Les commandes Transact-SQL suivantes sont utilisées dans cette section :

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Créez une clé principale pour la base de données si celle-ci n’en a pas. C’est nécessaire pour chiffrer le secret des informations d’identification.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password';  
   ```

   > [!NOTE]
   > `PASSWORD` est le mot de passe utilisé pour chiffrer la clé principale dans la base de données. Il doit remplir les critères de la stratégie de mot de passe Windows de l’ordinateur qui héberge l’instance SQL Server.

1. Créez des informations d’identification incluses dans l’étendue de la base de données.

   ```sql
   /*  
   * Specify credentials to external data source
   * IDENTITY: user name for external source.  
   * SECRET: password for external source.
   */
   CREATE DATABASE SCOPED CREDENTIAL credential_name
   WITH IDENTITY = 'username', Secret = 'password';
   ```

1. Créez une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Spécifiez l’emplacement de la source de données externe et les informations d’identification de la source de données Oracle.

   ```sql
   /* 
   * LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
   * PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
   * CONNECTION_OPTIONS: Specify driver location
   * CREDENTIAL: the database scoped credential, created above.
   */  
   CREATE EXTERNAL DATA SOURCE external_data_source_name
   WITH ( 
     LOCATION = 'oracle://<server address>[:<port>]',
     -- PUSHDOWN = ON | OFF,
     CREDENTIAL = credential_name)
   ```

1. Utilisez [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) pour créer des tables externes qui représentent les données stockées dans le système Oracle externe.

   ```sql
   /*
   * LOCATION: Oracle table/view in '<database_name>.<schema_name>.<object_name>' format
   * DATA_SOURCE: the external data source, created above.
   */
   CREATE EXTERNAL TABLE customers(
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
    LOCATION='customer',
    DATA_SOURCE=  external_data_source_name
   );
   ```

1. **Facultatif :** créez des statistiques sur la table externe avec la commande suivante.

   ```sql
   CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
   ```

   > [!TIP]
   > Il est recommandé de créer des statistiques sur les colonnes de tables externes, en particulier celles utilisées pour les jointures, les filtres et les agrégats. Il en résulte des performances de requête optimales.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur PolyBase, consultez [Vue d’ensemble de SQL Server PolyBase](polybase-guide.md).
