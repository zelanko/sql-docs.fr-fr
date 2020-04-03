---
title: 'Accéder aux données externes : Types génériques ODBC - PolyBase'
description: PolyBase dans SQL Server vous permet de vous connecter à des sources de données compatibles par le biais du connecteur ODBC. Installez le pilote ODBC et créez des tables externes.
ms.date: 02/19/2020
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: de3d0489acfca3363824b45ce87ba7ac4b63bf7a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80215834"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Configurer PolyBase pour accéder à des données externes dans SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

PolyBase dans SQL Server 2019 vous permet de vous connecter à des sources de données compatibles avec ODBC par le biais du connecteur ODBC.

Cet article fournit des exemples d’utilisation d’un pilote ODBC. Contactez votre fournisseur ODBC pour obtenir des exemples spécifiques. Pour déterminer les options de chaîne de connexion appropriées, référez-vous à la documentation du pilote ODBC relative à la source de données. Les exemples présentés dans cet article peuvent ne s’appliquer à aucun pilote ODBC spécifique.

## <a name="prerequisites"></a>Prérequis

>[!NOTE]
>Cette fonctionnalité nécessite SQL Server sur Windows.

* [Installation de PolyBase](polybase-installation.md).

* La [clé principale](../../t-sql/statements/create-master-key-transact-sql.md) doit être créée avant les informations d’identification incluses dans l’étendue de la base de données.

## <a name="install-the-odbc-driver"></a>Installer le pilote ODBC

Commencez par télécharger et installer le pilote ODBC de la source de données à laquelle vous souhaitez vous connecter sur chacun des nœuds PolyBase. Une fois que le pilote est correctement installé, vous pouvez voir et tester le pilote à partir de l’**Administrateur de sources de données ODBC**.

![Groupes de scale-out PolyBase](../../relational-databases/polybase/media/polybase-odbc-admin.png) 

Dans l’exemple ci-dessus, le nom du pilote est entouré en rouge. Utilisez ce nom quand vous créez la source de données externe.

> [!IMPORTANT]
> Afin d’améliorer les performances des requêtes, activez le regroupement de connexions. Cette opération peut être effectuée à partir de l’**Administrateur de sources de données ODBC**.

## <a name="create-an-external-table"></a>Créer une table externe

Pour interroger les données d’une source de données ODBC, vous devez créer des tables externes afin de référencer les données externes. Cette section fournit un exemple de code pour créer des tables externes.

Les commandes Transact-SQL suivantes sont utilisées dans cette section :

* [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
* [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
* [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Créez des informations d’identification incluses dans l’étendue de la base de données pour accéder à la source ODBC.

    ```sql
    CREATE DATABASE SCOPED CREDENTIAL <credential_name> WITH IDENTITY = '<username>', Secret = '<password>';
    ```

    Par exemple, l’exemple suivant crée des informations d’identification nommées `credential_name`, avec l’identité `username` et un mot de passe complexe.

    ```sql
    CREATE DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'username', Secret = 'BycA4ZjrE#*2W%!';
    ```

1. Créez une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

    ```sql
    CREATE EXTERNAL DATA SOURCE <external_data_source_name>
    WITH ( LOCATION = odbc://<ODBC server address>[:<port>],
    CONNECTION_OPTIONS = 'Driver={<Name of Installed Driver>};
    ServerNode = <name of server  address>:<Port>',
    -- PUSHDOWN = [ON] | OFF,
    CREDENTIAL = <credential_name> );
    ```

    L’exemple suivant crée une source de données externe :
    * `external_data_source_name` nommée
    * Situé sur le serveur ODBC `SERVERNAME` et sur le port `4444`
    * Connexion avec `CData ODBC Driver For SAP 2015` : il s’agit du pilote créé dans [Installer le pilote ODBC](#install-the-odbc-driver)
    * Sur `ServerNode` `sap_server_node`, port `5555`
    * Configuré pour un traitement transmis au serveur (`PUSHDOWN = ON`)
    * Utilisation des informations d’identification `credential_name`

    ```sql
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( LOCATION = odbc://SERVERNAME:4444,
    CONNECTION_OPTIONS = 'Driver={CData ODBC Driver For SAP 2015};
    ServerNode = sap_server_node:5555',
    PUSHDOWN = ON,
    CREDENTIAL = credential_name );
    ```

1. **Facultatif :** Créez des statistiques sur une table externe.

    Pour des performances de requêtes optimales, nous vous recommandons de créer des statistiques sur les colonnes de table externe, en particulier celles utilisées pour les jointures, les filtres et les agrégats.

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
    ```

>[!IMPORTANT]
>Une fois que vous avez créé une source de données externes, utilisez la commande [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) afin de créer une table requêtable sur cette source.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur PolyBase, consultez [Vue d’ensemble de SQL Server PolyBase](polybase-guide.md).
