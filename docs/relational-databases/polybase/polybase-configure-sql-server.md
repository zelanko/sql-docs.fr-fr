---
title: Configurer PolyBase pour accéder à des données externes dans SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
ms.reviewer: jroth
manager: craigg
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: fe5fd6f1842e02d85f6dcd9ee53884ff4cd289e2
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64776076"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Configurer PolyBase pour accéder à des données externes dans SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment utiliser PolyBase sur une instance de SQL Server pour interroger des données externes dans une autre instance SQL Server.

## <a name="prerequisites"></a>Conditions préalables requises

Si vous n’avez pas installé PolyBase, consultez [Installation de PolyBase](polybase-installation.md). Cet article décrit les prérequis pour l’installation.

La [clé principale](../../t-sql/statements/create-master-key-transact-sql.md) doit être créée avant les informations d’identification incluses dans l’étendue de la base de données. 

## <a name="configure-a-sql-server-external-data-source"></a>Configurer une source de données externes SQL Server

Pour interroger les données d’une source de données SQL Server, vous devez créer des tables externes pour référencer les données externes. Cette section fournit un exemple de code pour créer ces tables externes. 
 
Pour des performances de requêtes optimales, créez des statistiques sur les colonnes de tables externes, en particulier celles utilisées pour les jointures, les filtres et les agrégats.

Les commandes Transact-SQL suivantes sont utilisées dans cette section :

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1.  Créez des informations d’identification incluses dans l’étendue de la base de données pour accéder à la source MongoDB.

    ```sql
    /*  specify credentials to external data source
    *  IDENTITY: user name for external source.  
    *  SECRET: password for external source.
    */
    CREATE DATABASE SCOPED CREDENTIAL SqlServerCredentials   
    WITH IDENTITY = 'username', Secret = 'password';
    ```

1. Créez une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

    ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *  CREDENTIAL: the database scoped credential, created above.
    */
    CREATE EXTERNAL DATA SOURCE SQLServerInstance
    WITH ( LOCATION = 'sqlserver://SqlServer',
    -- PUSHDOWN = ON | OFF,
    CREDENTIAL = SQLServerCredentials);
    ```

1. **Facultatif :** Créez des statistiques sur une table externe.

    Pour des performances de requêtes optimales, nous vous recommandons de créer des statistiques sur les colonnes de table externe, en particulier celles utilisées pour les jointures, les filtres et les agrégats.

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN;
    ```

>[!IMPORTANT] 
>Une fois que vous avez créé une source de données externes, vous pouvez utiliser la commande [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) afin de créer une table requêtable sur cette source.

## <a name="sql-server-connector-compatible-types"></a>Types compatibles avec le connecteur SQL Server

Vous pouvez établir une connexion avec d’autres sources de données qui reconnaissent les connexions SQL Server. Utilisez le connecteur SQL Server PolyBase pour créer une table externe pour Azure SQL Data Warehouse et Azure SQL Database. Pour accomplir cette tâche, suivez les étapes indiquées précédemment. Vérifiez que les informations d’identification incluses dans l’étendue de la base de données, l’adresse du serveur, le port et la chaîne d’emplacement sont bien ceux de la source de données compatible à laquelle vous souhaitez vous connecter.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur PolyBase, consultez [Vue d’ensemble de SQL Server PolyBase](polybase-guide.md).
