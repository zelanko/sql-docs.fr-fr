---
title: Configurer PolyBase pour accéder à des données externes dans MongoDB | Microsoft Docs
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
ms.openlocfilehash: 39889d49702394f0aec8f79c328e28ba318c9864
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806739"
---
# <a name="configure-polybase-to-access-external-data-in-mongodb"></a>Configurer PolyBase pour accéder à des données externes dans MongoDB

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’article explique comment utiliser PolyBase sur une instance SQL Server pour interroger des données externes dans MongoDB.

## <a name="prerequisites"></a>Conditions préalables requises

Si vous n’avez pas installé PolyBase, consultez [Installation de PolyBase](polybase-installation.md).

## <a name="configure-an-external-table"></a>Configurer une table externe

Pour interroger les données d’une source de données MongoDB, vous devez créer des tables externes pour référencer les données externes. Cette section fournit un exemple de code pour créer ces tables externes.

Voici les objets de création qui vont être utilisés dans cette section :

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

1.   Créez des informations d’identification incluses dans l’étendue de la base de données pour accéder à la source MongoDB.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL credential_name 
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1.  Créez une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

     ```sql
     /*  LOCATION: Location string should be of format '<type>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH (
    LOCATION = mongodb://<server>[:<port>],
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = credential_name
    );
     ```

1.  Créez des tables externes qui représentent les données stockées dans le système MongoDB externe [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).

     ```sql
     /*  LOCATION: MongoDB table/view in '<database_name>.<schema_name>.<object_name>' format
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE customers(
     [O_ORDERKEY] DECIMAL(38) NOT NULL,
     [O_CUSTKEY] DECIMAL(38) NOT NULL,
     [O_ORDERSTATUS] CHAR COLLATE Latin1_General_BIN NOT NULL,
     [O_TOTALPRICE] DECIMAL(15,2) NOT NULL,
     [O_ORDERDATE] DATETIME2(0) NOT NULL,
     [O_COMMENT] VARCHAR(79) COLLATE Latin1_General_BIN NOT NULL
     )
     WITH (
     LOCATION='customer',
     DATA_SOURCE= external_data_source_name
     );
     ```

1. **Facultatif :** Créez des statistiques sur une table externe.

    Pour des performances de requêtes optimales, nous vous recommandons de créer des statistiques sur les colonnes de table externe, en particulier celles utilisées pour les jointures, les filtres et les agrégats.

     ```sql
      CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
     ```


## <a name="flattening"></a>Aplanissement
 L’aplanissement est activé pour les données imbriquées et répétées, issues de collections de documents MongoDB. L’utilisateur doit activer `create an external table` et spécifier explicitement un schéma relationnel sur des collections de documents MongoDB dont les données peuvent être imbriquées et/ou répétées. Aux prochaines échéances, la détection de schéma automatique sera possible dans les collections de documents mongo.
Les types de données JSON imbriquées/répétées seront aplanis comme suit :

* Objets : collection de clés/valeurs non ordonnées mises entre accolades (imbriquées)

   - Nous créerons une colonne de table pour chaque clé d’objet

     * Nom de colonne : objectname_keyname

* Tableau : valeurs ordonnées, séparées par des virgules, mises entre crochets (répétées)

   - Nous ajouterons une nouvelle ligne de table pour chaque élément de tableau

   - Nous créerons une colonne par tableau pour stocker l’index d’élément de tableau

     * Nom de colonne : arrayname_index

     * Type de données : bigint

Cette technique peut occasionner plusieurs problèmes, notamment les deux suivants :

* un champ répété vide masque de facto les données contenues dans les champs plats du même enregistrement

* la présence de plusieurs champs répétés peut entraîner une explosion du nombre de lignes générées

À titre d’exemple, nous allons évaluer la collection de restaurants de l’exemple de jeu de données MongoDB stockée dans un format JSON non relationnel. Chaque restaurant dispose d’un champ d’adresse imbriqué et d’un tableau de notes (« grades ») attribuées à des jours différents. La figure ci-dessous illustre un restaurant type avec une adresse imbriquée et des notes imbriquées/répétées.

![Aplanissement MongoDB](../../relational-databases/polybase/media/mongo-flattening.png "Aplanissement de restaurant MongoDB")

L’adresse de l’objet sera aplanie comme suit :

* Le champ imbriqué restaurant.address.building devient restaurant.address_building
* Le champ imbriqué restaurant.address.coord devient restaurant.address_coord
* Le champ imbriqué restaurant.address.street devient restaurant.address_street
* Le champ imbriqué restaurant.address.zipcode devient restaurant.address_zipcode

Les notes du tableau seront aplanies comme suit :
| grades_date | grades_grade  | games_score | 
| ------------- | ------------------------- | -------------- |
|1393804800000 |Un |2|
|1378857600000|Un |6|
|135898560000 |Un |10|
|1322006400000|Un |9|
|1299715200000 |B |14|

## <a name="cosmos-db-connection"></a>Connexion Cosmos DB

À l’aide de l’API Mongo Cosmos DB et du connecteur PolyBase MongoDB, vous pouvez créer une table externe pour une **instance Cosmos DB**. Pour cela, vous devez suivre les étapes listées ci-dessus. Vérifiez que les informations d’identification incluses dans l’étendue de la base de données, l’adresse du serveur, le port et la chaîne d’emplacement sont bien ceux du serveur Cosmos DB. 

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur PolyBase, consultez [Vue d’ensemble de SQL Server PolyBase](polybase-guide.md).
