---
title: Configurer PolyBase pour accéder à des données externes avec des types génériques ODBC | Microsoft Docs
ms.custom: ''
ms.date: 10/16/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 98e06e3199d4ce8750a4a5956aec6d97c141b33b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53214254"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Configurer PolyBase pour accéder à des données externes dans SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

PolyBase dans SQL Server 2019 vous permet de vous connecter à des sources de données compatibles avec ODBC par le biais du connecteur ODBC. 

## <a name="prerequisites"></a>Conditions préalables requises

Notez que la fonctionnalité = peut être utilisée uniquement sur SQL Server pour Windows. 

Si vous n’avez pas installé PolyBase, consultez [Installation de PolyBase](polybase-installation.md).

Commencez par télécharger et installer le pilote ODBC de la source de données à laquelle vous souhaitez vous connecter, sur chacun des nœuds PolyBase. Une fois que le pilote est correctement installé, vous pouvez tester le pilote dans « Administrateur de sources de données ODBC ».

![Groupes de scale-out PolyBase](../../relational-databases/polybase/media/polybase-odbc-admin.png) 

> **IMPORTANT !**
> 
> Pour améliorer les performances des requêtes, vérifiez que le regroupement des connexions est activé pour le pilote. Vous pouvez activer cette option sous « Administrateur de sources de données ODBC ».
> 
> **Remarque**
> 
> Le nom du pilote (entouré ci-dessus) doit être spécifié lors de la création de la source de données externe (étape 3 ci-dessous).

## <a name="create-an-external-table"></a>Créer une table externe

Pour interroger les données d’une source de données ODBC, vous devez créer des tables externes afin de référencer les données externes. Cette section fournit un exemple de code pour créer des tables externes.

Ces objets vont être créés dans cette section :

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) 
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)

1. Créez une clé principale pour la base de données, si celle-ci n’en a pas. C’est nécessaire pour chiffrer le secret des informations d’identification.

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password';  
     ```
    ## <a name="arguments"></a>Arguments
    PASSWORD ='password'

    Mot de passe utilisé pour chiffrer la clé principale dans la base de données. Le mot de passe doit remplir les critères de la stratégie de mot de passe Windows de l’ordinateur qui héberge l’instance SQL Server.

1. Créez des informations d’identification incluses dans l’étendue de la base de données pour accéder à la source ODBC.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL credential_name
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. Créez une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

     ```sql
    /*  LOCATION: Location string should be of format '<type>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( 
    LOCATION = odbc://<ODBC server address>[:<port>],
    CONNECTION_OPTIONS = 'SSL=0;sslAllowInvalidCertificates=1;Driver={<Name of Installed Driver>};HOST=%s;AUTHMECH=0',
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = credential_name
    );

     ```


1.  Créez des tables externes qui représentent les données stockées dans la source de données externe à l’aide de [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
     ```sql
     /*  LOCATION: ODBC data source table/view
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE customer(
     C_CUSTKEY INT NOT NULL,
     C_NAME VARCHAR(25) NOT NULL,
     C_ADDRESS VARCHAR(40) NOT NULL,
     C_NATIONKEY INT NOT NULL,
     C_PHONE CHAR(15) NOT NULL,
     C_ACCTBAL DECIMAL(15,2) NOT NULL,
     C_MKTSEGMENT CHAR(10) NOT NULL,
     C_COMMENT VARCHAR(117) NOT NULL
      )
      WITH (
      LOCATION='customer',
      DATA_SOURCE= external_data_source_name
     );
      ```

1. **Facultatif :** Créez des statistiques sur une table externe.

    Pour des performances de requêtes optimales, nous vous recommandons de créer des statistiques sur les colonnes de table externe, en particulier celles utilisées pour les jointures, les filtres et les agrégats.

     ```sql
      CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
     ```

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur PolyBase, consultez [Vue d’ensemble de SQL Server PolyBase](polybase-guide.md).
