---
title: CREATE EXTERNAL DATA SOURCE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL DATA SOURCE
- CREATE_EXTERNAL_DATA_SOURCE
dev_langs:
- TSQL
helpviewer_keywords:
- External
- External, data source
- PolyBase, create data source
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 91711ce160dcb653d9e05e8b0a445214a247d337
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "73981884"
---
# <a name="create-external-data-source-transact-sql"></a>CREATE EXTERNAL DATA SOURCE (Transact-SQL)

Crée une source de données externe pour l’interrogation à l’aide de SQL Server, SQL Database, SQL Data Warehouse ou le système de la plateforme d’analyse (Parallel Data Warehouse ou PDW).

Cet article fournit la syntaxe, les arguments, les notes, les autorisations et des exemples associés au produit SQL que vous choisissez.

Pour plus d’informations sur les conventions de la syntaxe, consultez [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="click-a-product"></a>Cliquez sur un produit !

Dans la ligne suivante, cliquez sur le nom du produit qui vous intéresse. Le clic affiche un contenu différent ici dans cette page web, approprié pour le produit sur lequel vous cliquez.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions"

|                               |                                                              |                                                              |                                                              |      |
| ----------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ---- |
| **\* _SQL Server \*_** &nbsp; | [SQL Database](create-external-data-source-transact-sql.md?view=azuresqldb-current) | [SQL Data<br />Warehouse](create-external-data-source-transact-sql.md?view=azure-sqldw-latest) | [Analytics Platform<br />System (PDW)](create-external-data-source-transact-sql.md?view=aps-pdw-2016-au7) |      |
|                               |                                                              |                                                              |                                                              |      |

&nbsp;

## <a name="overview-sql-server"></a>Présentation : SQL Server

Crée une source de données externe pour des requêtes PolyBase. Des sources de données externes sont utilisées pour établir la connectivité et prendre en charge ces principaux cas d’utilisation :

- Virtualisation des données et chargement des données à l’aide de [PolyBase][intro_pb]
- Les opérations de chargement en bloc à l’aide de `BULK INSERT` ou `OPENROWSET`

**S’APPLIQUE À** : SQL Server 2016 (ou ultérieur)

## <a name="syntax"></a>Syntaxe

```sql
CREATE EXTERNAL DATA SOURCE <data_source_name>  
WITH
(    LOCATION                  = '<prefix>://<path>[:<port>]'
[,   CONNECTION_OPTIONS        = '<name_value_pairs>']
[,   CREDENTIAL                = <credential_name> ]
[,   PUSHDOWN                  = ON | OFF]
[,   TYPE                      = HADOOP | BLOB_STORAGE ]
[,   RESOURCE_MANAGER_LOCATION = '<resource_manager>[:<port>]'
)
[;]
```

## <a name="arguments"></a>Arguments

### <a name="data_source_name"></a>data_source_name

Spécifie le nom défini par l’utilisateur de la source de données. Ce nom doit être unique dans la base de données de SQL Server.

### <a name="location--prefixpathport"></a>EMPLACEMENT = *`'<prefix>://<path[:port]>'`*

Fournit le protocole de connectivité et le chemin d’accès à la source de données externe.

| Source de données externe    | Préfixe de l’emplacement | Chemin d’emplacement                                         | Emplacements pris en charge par produit / service |
| ----------------------- | --------------- | ----------------------------------------------------- | ---------------------------------------- |
| Cloudera ou Hortonworks | `hdfs`          | `<Namenode>[:port]`                                   | SQL Server (2016+)                       |
| Stockage Blob Azure      | `wasb[s]`       | `<container>@<storage_account>.blob.core.windows.net` | SQL Server (2016+)                       |
| SQL Server              | `sqlserver`     | `<server_name>[\<instance_name>][:port]`              | SQL Server (2019+)                       |
| Oracle                  | `oracle`        | `<server_name>[:port]`                                | SQL Server (2019+)                       |
| Teradata                | `teradata`      | `<server_name>[:port]`                                | SQL Server (2019+)                       |
| MongoDB ou CosmosDB     | `mongodb`       | `<server_name>[:port]`                                | SQL Server (2019+)                       |
| ODBC                    | `odbc`          | `<server_name>[:port]`                                | SQL Server (2019 +) - Windows uniquement        |
| opérations en bloc         | `https`         | `<storage_account>.blob.core.windows.net/<container>` | SQL Server (2017+)                       |

Chemin d’emplacement :

- `<`NameNode`>` = Nom de la machine, nom de l’URI de service ou adresse IP du `Namenode` du cluster Hadoop. PolyBase doit résoudre tous les noms DNS utilisés par le cluster Hadoop. <!-- For highly available Hadoop configurations, provide the Nameservice ID as the `LOCATION`. -->
- `port` = Le port d’écoute de la source de données externe. Dans Hadoop, le port se trouve à l’aide du paramètre de configuration `fs.defaultFS`. La valeur par défaut est 8020.
- `<container>` = le conteneur du compte de stockage contenant les données. Les conteneurs racines sont en lecture seule, donc les données ne peuvent pas être réécrites sur le conteneur.
- `<storage_account>` = le nom du compte de stockage de la ressource Azure.
- `<server_name>` = le nom d’hôte.
- `<instance_name>` = le nom de l’instance nommée de SQL Server. Utilisé si votre Service SQL Server Browser est en cours d’exécution sur l’instance cible.

Remarques et conseils supplémentaires lors de la définition de l’emplacement :

- Le moteur SQL ne vérifie pas l’existence de la source de données externe lorsque l’objet est créé. Pour valider, créez une table externe à l’aide d’une source de données externe.
- Utilisez la même source de données externe pour toutes les tables lors de l’interrogation de Hadoop afin de garantir la cohérence des paramètres sémantiques de requête.
- Vous pouvez utiliser le préfixe d’emplacement `sqlserver` pour connecter SQL Server 2019 à SQL Server, SQL Database ou SQL Data Warehouse.
- Spécifiez `Driver={<Name of Driver>}` lors de la connexion via `ODBC`.
- `wasb` est le protocole par défaut pour le stockage d’objets blob Azure. `wasbs` est facultatif mais recommandé, car il permet d’envoyer les données au moyen d’une connexion SSL sécurisée.
- Pour garantir la réussite des requêtes PolyBase lors du basculement du `Namenode` Hadoop, envisagez d’utiliser une adresse IP virtuelle pour le `Namenode`du cluster Hadoop. Dans le cas contraire, exécutez une commande [ALTER EXTERNAL DATA SOURCE][alter_eds] pour pointer vers le nouvel emplacement.

### <a name="connection_options--key_value_pair"></a>CONNECTION_OPTIONS = *key_value_pair*

Spécifie des options supplémentaires lors de la connexion via `ODBC` à une source de données externe.

Au minimum, le nom du pilote est requis, mais d’autres options telles que `APP='<your_application_name>'` ou `ApplicationIntent= ReadOnly|ReadWrite` sont également utiles pour paramétrer et aider à la résolution des problèmes.

Reportez-vous à la documentation du produit `ODBC` pour obtenir la liste des options [CONNECTION_OPTIONS][connection_options] autorisées.

### <a name="pushdown--on--off"></a>PUSHDOWN = *ON | OFF*

Indique si le calcul peut être transmis à la source de données externe. Cette option est activée par défaut.

`PUSHDOWN` est pris en charge lors de la connexion à SQL Server, Oracle, Teradata, MongoDB ou ODBC au niveau de la source de données externe.

L’activation ou la désactivation de la transmission au niveau de la requête s’effectue au moyen d’un [indicateur][hint_pb].

### <a name="credential--credential_name"></a>CREDENTIAL = *credential_name*

Spécifie les informations d’identification limitées à la base de données servant à l’authentification auprès de la source de données externe.

Remarques et conseils supplémentaires lors de la création d’informations d’identification :

- `CREDENTIAL` est requis uniquement si le blob a été sécurisé. `CREDENTIAL` n’est pas requis pour les jeux de données qui autorisent l’accès anonyme.
- Lorsque `TYPE` = `BLOB_STORAGE`, les informations d’identification doivent être créées avec l’identité `SHARED ACCESS SIGNATURE`. En outre, le jeton SAS doit être configuré comme suit :
  - Retirez le caractère `?` en tête lorsqu’il est configuré en tant que secret
  - Disposez d’au moins l’autorisation en lecture sur le fichier qui doit être chargé (par exemple `srt=o&sp=r`)
  - Utilisez une période d’expiration valide (toutes les dates sont au format UTC).

Pour un exemple d’utilisation de `CREDENTIAL` avec `SHARED ACCESS SIGNATURE` et `TYPE` = `BLOB_STORAGE`, consultez [Créer une source de données externe pour les opérations en bloc de récupération de données dans le stockage Blob Azure](#f-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage)

Pour créer des informations d’identification délimitées à la base de données, consultez [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)][create_dsc].

### <a name="type---hadoop--blob_storage-"></a>TYPE = *[ HADOOP | BLOB_STORAGE ]*

Spécifie le type de source de données externe en cours de configuration. Ce paramètre n’est pas toujours requis.

- Utilisez HADOOP lorsque la source de données externe est Cloudera, Hortonworks ou Stockage Blob Azure.
- Utilisez BLOB_STORAGE quand vous exécutez des opérations en bloc à l’aide de [BULK INSERT][bulk_insert] ou [OPENROWSET][openrowset] avec [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].

> [!IMPORTANT]
> Ne paramétrez pas `TYPE` si vous utilisez toute autre source de données externe.

Pour un exemple d’utilisation de `TYPE` = `HADOOP` pour charger des données depuis le stockage Blob Azure, consultez [Créer une source de données externes pour référencer le stockage blob Azure](#e-create-external-data-source-to-reference-azure-blob-storage).

### <a name="resource_manager_location--resourcemanager_uriport"></a>RESOURCE_MANAGER_LOCATION = *'ResourceManager_URI[:port]'*

Configurez cette valeur facultative lors de la connexion à Hortonworks ou Cloudera.

Lorsque `RESOURCE_MANAGER_LOCATION` est défini, l’optimiseur de requête prend une décision basée sur le coût pour améliorer les performances. Une tâche MapReduce peut être utilisée pour transmettre le calcul à Hadoop. En spécifiant `RESOURCE_MANAGER_LOCATION`, il est possible de considérablement réduire le volume des données transférées entre Hadoop et SQL, ce qui peut donc améliorer les performances des requêtes.  

Si le Gestionnaire des ressources n’est pas spécifié, le transfert de calcul dans Hadoop est désactivé pour les requêtes PolyBase.

Si le port n’est pas spécifié, la valeur par défaut est déterminée d’après le paramètre actuel de la configuration de la « connexion à hadoop ».

| Connexion Hadoop | Port du Gestionnaire de ressources par défaut |
| ------------------- | ----------------------------- |
| 1                   | 50300                         |
| 2                   | 50300                         |
| 3                   | 8021                          |
| 4                   | 8032                          |
| 5                   | 8050                          |
| 6                   | 8032                          |
| 7                   | 8050                          |

Pour obtenir la liste complète des versions de Hadoop prises en charge, consultez [Configuration de la connectivité PolyBase (Transact-SQL)][connectivity_pb].

> [!IMPORTANT]  
> La valeur RESOURCE_MANAGER_LOCATION n’est pas validée lorsque vous créez la source de données externe. La saisie d’une valeur incorrecte peut entraîner l’échec de la requête au moment de l’exécution chaque fois qu’une transmission est tentée, étant donné que la valeur fournie ne serait pas en mesure d’être résolue.

[Créer une source de données externe pour faire référence à Hadoop avec la transmission activée](#c-create-external-data-source-to-reference-hadoop-with-push-down-enabled) fournit un exemple concret ainsi que des instructions complémentaires.

## <a name="permissions"></a>Autorisations

Nécessite l’autorisation CONTROL sur la base de données dans SQL Server.

## <a name="locking"></a>Verrouillage

Prend un verrou partagé sur l’objet EXTERNAL DATA SOURCE.  

## <a name="security"></a>Sécurité

PolyBase prend en charge l’authentification basée sur le proxy pour la plupart de ces sources de données externes. Créez des informations d’identification au niveau de la base de données pour créer le compte proxy.

Lorsque vous vous connectez au stockage ou au pool de données dans un cluster Big data de SQL Server, les informations d’identification de l’utilisateur sont transmises par le système back-end. Créez des connexions dans le pool de données lui-même pour activer l’authentification en transfert direct.

Actuellement un jeton SAP avec le type `HADOOP` n’est pas pris en charge. Il est uniquement pris en charge avec une clé d’accès de compte de stockage. Toute tentative de créer une source de données externe avec le type `HADOOP` et les informations d’identification SAS échoue avec l’erreur :

`Msg 105019, Level 16, State 1 - EXTERNAL TABLE access failed due to internal error: 'Java exception raised on call to HdfsBridge_Connect. Java exception message: Parameters provided to connect to the Azure storage account are not valid.: Error [Parameters provided to connect to the Azure storage account are not valid.] occurred while accessing external file.'`

## <a name="examples-sql-server-2016"></a>Exemples : SQL Server (2016+)

### <a name="a-create-external-data-source-in-sql-2019-to-reference-oracle"></a>A. Créer une source de données externe dans SQL 2019 pour faire référence à Oracle

Pour créer une source de données externe qui fait référence à Oracle, assurez-vous d’avoir des informations d’identification de niveau base de données. Vous pouvez également, si vous le souhaitez, activer ou désactiver la transmission des calculs par rapport à cette source de données.

```sql
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '!MyC0mpl3xP@ssw0rd!
;

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL OracleProxyAccount
WITH
     IDENTITY   = 'oracle_username'
,    SECRET     = 'oracle_password'
;

CREATE EXTERNAL DATA SOURCE MyOracleServer
WITH
(    LOCATION   = 'oracle://145.145.145.145:1521'
,    CREDENTIAL = OracleProxyAccount
,    PUSHDOWN   = ON
,    TYPE=BLOB_STORAGE
)
;
```

Pour obtenir des exemples supplémentaires pour d’autres sources de données telles que MongoDB, consultez [Configurer PolyBase pour accéder aux données externes dans MongoDB][mongodb_pb].

### <a name="b-create-external-data-source-to-reference-hadoop"></a>B. Créer une source de données externe pour faire référence à Hadoop

Pour créer une source de données externe pour faire référence à votre cluster Hortonworks ou Cloudera Hadoop, spécifiez le nom de l’ordinateur ou l’adresse IP du port et du `Namenode` Hadoop. <!-- Provide the Nameservice ID as the `LOCATION` for highly available configurations. -->

```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH
(    LOCATION = 'hdfs://10.10.10.10:8050'
,    TYPE     = HADOOP
)
;
```

### <a name="c-create-external-data-source-to-reference-hadoop-with-push-down-enabled"></a>C. Créer une source de données externe pour faire référence à Hadoop avec transmission activée

Spécifiez l’option `RESOURCE_MANAGER_LOCATION` pour activer le calcul transmis à Hadoop pour des requêtes PolyBase. Une fois activé, PolyBase prend une décision basée sur les coûts pour déterminer si le calcul de la requête doit être poussé vers Hadoop.

```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH
(    LOCATION                  = 'hdfs://10.10.10.10:8020'
,    TYPE                      = HADOOP
,    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
)
;
```

### <a name="d-create-external-data-source-to-reference-kerberos-secured-hadoop"></a>D. Créer une source de données externe pour faire référence à Hadoop sécurisé par Kerberos

Pour vérifier si le cluster Hadoop est sécurisé par Kerberos, regardez la valeur de la propriété hadoop.security.authentication dans Hadoop core-site.xml. Pour faire référence à un cluster Hadoop sécurisé par Kerberos, vous devez spécifier des informations d’identification limitées à la base de données qui contiennent votre nom d’utilisateur et votre mot de passe Kerberos. La clé principale de la base de données est utilisée pour chiffrer le secret des informations d’identification limitées à la base de données.

```sql  
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo'
;

-- Create a database scoped credential with Kerberos user name and password.
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1
WITH
     IDENTITY   = '<hadoop_user_name>'
,    SECRET     = '<hadoop_password>'
;

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH
(    LOCATION                  = 'hdfs://10.10.10.10:8050'
,    CREDENTIAL                = HadoopUser1
,    TYPE                      = HADOOP
,    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
)
;
```

### <a name="e-create-external-data-source-to-reference-azure-blob-storage"></a>E. Créer une source de données externe pour faire référence au stockage d’objets blob Azure

Dans cet exemple, la source de données externe est un conteneur de stockage d’objets blob Azure appelé `daily` sous le compte de stockage Azure nommé `logs`. La source de données externe de stockage Azure sert au transfert des données uniquement. Elle ne prend pas en charge le pushdown de prédicats.

Cet exemple montre comment créer des informations d’identification limitées à la base de données qui serviront à l’authentification auprès du stockage Azure. Spécifiez la clé du compte de stockage Azure dans le secret des informations d’identification de la base de données. Vous pouvez spécifier toute chaîne de l’identité des informations d’identification limitées à la base de données, étant donné qu’elle n’est pas utilisée lors de l’authentification auprès du stockage Azure.

```sql
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo'
;

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential
WITH
     IDENTITY   = '<my_account>'
,    SECRET     = '<azure_storage_account_key>'
;

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage
WITH
(    LOCATION   = 'wasbs://daily@logs.blob.core.windows.net/'
,    CREDENTIAL = AzureStorageCredential
,    TYPE       = HADOOP
)
;
```

## <a name="examples-bulk-operations"></a>Exemples : opérations en bloc

> [!NOTE]
> Ne placez pas de **/** en fin, nom de fichier, ou paramètres de signature d’accès partagé à la fin de l’URL `LOCATION` lors de la configuration d’une source de données externe pour les opérations en bloc.

### <a name="f-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage"></a>F. Créer une source de données externe pour les opérations en bloc de récupération de données dans le stockage Blob Azure

**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].
Utilisez la source de données suivante pour les opérations en bloc à l’aide de [BULK INSERT][bulk_insert] ou [OPENROWSET][openrowset]. L’identifiant utilisé doit donner à l’identité la valeur `SHARED ACCESS SIGNATURE`, ne doit pas avoir le premier `?` dans le jeton SAS, doit avoir au moins les droits de lecture sur le fichier à charger (par exemple `srt=o&sp=r`), et doit présenter une période d’expiration valide (toutes les dates sont en heure UTC). Pour plus d’informations sur les signatures d’accès partagé, consultez [Utilisation des signatures d’accès partagé (SAP)][sas_token].

```sql
CREATE DATABASE SCOPED CREDENTIAL AccessAzureInvoices
WITH
     IDENTITY = 'SHARED ACCESS SIGNATURE'
--   REMOVE ? FROM THE BEGINNING OF THE SAS TOKEN
,    SECRET = '******srt=sco&sp=rwac&se=2017-02-01T00:55:34Z&st=2016-12-29T16:55:34Z***************'
;

CREATE EXTERNAL DATA SOURCE MyAzureInvoices
WITH
(    LOCATION   = 'https://newinvoices.blob.core.windows.net/week3'
,    CREDENTIAL = AccessAzureInvoices
,    TYPE       = BLOB_STORAGE
)
;
```

Pour voir une utilisation de cet exemple, consultez [BULK INSERT][bulk_insert_example].

## <a name="see-also"></a>Voir aussi

- [ALTER EXTERNAL DATA SOURCE (Transact-SQL)][alter_eds]
- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)][create_dsc]
- [CREATE EXTERNAL FILE FORMAT (Transact-SQL)][create_eff]
- [CREATE EXTERNAL TABLE (Transact-SQL)][create_etb]
- [sys.external_data_sources (Transact-SQL)][cat_eds]
- [Utilisation des signatures d’accès partagé (SAP)][sas_token]

<!-- links to external pages -->
<!-- SQL Docs -->
[bulk_insert]: https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql
[bulk_insert_example]: https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql#f-importing-data-from-a-file-in-azure-blob-storage
[openrowset]: https://docs.microsoft.com/sql/t-sql/functions/openrowset-transact-sql

[create_dsc]: https://docs.microsoft.com/sql/t-sql/statements/create-database-scoped-credential-transact-sql
[create_eff]: https://docs.microsoft.com/sql/t-sql/statements/create-external-file-format-transact-sql
[create_etb]: https://docs.microsoft.com/sql/t-sql/statements/create-external-table-transact-sql
[create_etb_as_sel]: https://docs.microsoft.com/sql/t-sql/statements/create-external-table-as-select-transact-sql?view=azure-sqldw-latest
[create_tbl_as_sel]: https://docs.microsoft.com/sql/t-sql/statements/create-table-as-select-azure-sql-data-warehouse?view=azure-sqldw-latest

[alter_eds]: https://docs.microsoft.com/sql/t-sql/statements/alter-external-data-source-transact-sql

[cat_eds]: https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-external-data-sources-transact-sql
<!-- PolyBase docs -->
[intro_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide
[mongodb_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-configure-mongodb
[connectivity_pb]:https://docs.microsoft.com/sql/database-engine/configure-windows/polybase-connectivity-configuration-transact-sql
[connection_options]: https://docs.microsoft.com/sql/relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client
[hint_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-pushdown-computation#force-pushdown

<!-- Azure Docs -->
[sas_token]: https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1

::: moniker-end
::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"

|                                                              |                                 |                                                              |                                                              |      |
| ------------------------------------------------------------ | ------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---- |
| [SQL Server](create-external-data-source-transact-sql.md?view=sql-server-2017) | **_\* SQL Database \*_** &nbsp; | [SQL Data<br />Warehouse](create-external-data-source-transact-sql.md?view=azure-sqldw-latest) | [Analytics Platform<br />System (PDW)](create-external-data-source-transact-sql.md?view=aps-pdw-2016-au7) |      |
|                                                              |                                 |                                                              |                                                              |      |

&nbsp;

## <a name="overview-azure-sql-database"></a>Présentation : Azure SQL Database

Crée une source de données externe pour des requêtes élastiques. Des sources de données externes sont utilisées pour établir la connectivité et prendre en charge ces principaux cas d’utilisation :

- Les opérations de chargement en bloc à l’aide de `BULK INSERT` ou `OPENROWSET`
- Interrogation d’instances distantes de SQL Database ou de SQL Data Warehouse à l’aide de SQL Database avec des [requêtes élastiques][remote_eq]
- Interrogation d’une base Azure SQL Database partitionnée à l’aide de [requêtes élastiques][sharded_eq]

## <a name="syntax"></a>Syntaxe

```sql
CREATE EXTERNAL DATA SOURCE <data_source_name>  
WITH
(    LOCATION                  = '<prefix>://<path>[:<port>]'
[,   CREDENTIAL                = <credential_name> ]
[,   TYPE                      = BLOB_STORAGE | RDBMS | SHARD_MAP_MANAGER ]
[,   DATABASE_NAME             = '<database_name>' ]
[,   SHARD_MAP_NAME            = '<shard_map_manager>' ]
)
[;]
```

## <a name="arguments"></a>Arguments

### <a name="data_source_name"></a>data_source_name

Spécifie le nom défini par l’utilisateur de la source de données. Ce nom doit être unique dans la base de données de SQL Database (SQL DB).

### <a name="location--prefixpathport"></a>EMPLACEMENT = *`'<prefix>://<path[:port]>'`*

Fournit le protocole de connectivité et le chemin d’accès à la source de données externe.

| Source de données externe   | Préfixe de l’emplacement | Chemin d’emplacement                                         |
| ---------------------- | --------------- | ----------------------------------------------------- |
| opérations en bloc        | `https`         | `<storage_account>.blob.core.windows.net/<container>` |
| Requête élastique (partition)  | Facultatif    | `<shard_map_server_name>.database.windows.net`        |
| Requête élastique (distant) | Facultatif    | `<remote_server_name>.database.windows.net`           |

Chemin d’emplacement :

- `<shard_map_server_name>` = le nom du serveur logique dans Azure qui héberge le Gestionnaire de la carte de partitions. L’argument `DATABASE_NAME` fournit la base de données utilisée pour héberger la carte de partitions et l’argument `SHARD_MAP_NAME` est utilisé pour la carte de partitions proprement dite.
- `<remote_server_name>` = le nom du serveur logique cible pour la requête élastique. Le nom de la base de données est spécifié avec l’argument `DATABASE_NAME`.

Remarques et conseils supplémentaires lors de la définition de l’emplacement :

- Le moteur SQL Database ne vérifie pas l’existence de la source de données externe lorsque l’objet est créé. Pour valider, créez une table externe à l’aide d’une source de données externe.

### <a name="credential--credential_name"></a>CREDENTIAL = *credential_name*

Spécifie les informations d’identification limitées à la base de données servant à l’authentification auprès de la source de données externe.

Remarques et conseils supplémentaires lors de la création d’informations d’identification :

- Pour charger les données à partir du stockage Blob Azure dans SQL Database, utilisez une clé de stockage Azure.
- `CREDENTIAL` est requis uniquement si le blob a été sécurisé. `CREDENTIAL` n’est pas requis pour les jeux de données qui autorisent l’accès anonyme.
- Lorsque `TYPE` = `BLOB_STORAGE`, les informations d’identification doivent être créées avec l’identité `SHARED ACCESS SIGNATURE`. En outre, le jeton SAS doit être configuré comme suit :
  - Retirez le caractère `?` en tête lorsqu’il est configuré en tant que secret
  - Disposez d’au moins l’autorisation en lecture sur le fichier qui doit être chargé (par exemple `srt=o&sp=r`)
  - Utilisez une période d’expiration valide (toutes les dates sont au format UTC).

Pour un exemple d’utilisation de `CREDENTIAL` avec `SHARED ACCESS SIGNATURE` et `TYPE` = `BLOB_STORAGE`, consultez [Créer une source de données externe pour les opérations en bloc de récupération de données dans le stockage Blob Azure](#c-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage)

Pour créer des informations d’identification délimitées à la base de données, consultez [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)][create_dsc].

### <a name="type---blob_storage--rdbms--shard_map_manager"></a>TYPE = *[ BLOB_STORAGE | RDBMS | SHARD_MAP_MANAGER]*

Spécifie le type de source de données externe en cours de configuration. Ce paramètre n’est pas toujours requis.

- Utilisez SGBDR pour les requêtes de bases de données croisées utilisant les requêtes élastiques à partir de SQL Database.  
- Utilisez SHARD_MAP_MANAGER lors de la création d’une source de données externe lorsque vous vous connectez à une base de données SQL partitionnée.
- Utilisez BLOB_STORAGE quand vous exécutez des opérations en bloc à l’aide de [BULK INSERT][bulk_insert] ou [OPENROWSET][openrowset].

> [!IMPORTANT]
> Ne paramétrez pas `TYPE` si vous utilisez toute autre source de données externe.

### <a name="database_name--database_name"></a>DATABASE_NAME = *database_name*

Configurez cet argument lorsque `TYPE` a la valeur `RDBMS` ou `SHARD_MAP_MANAGER`.

| TYPE              | Valeur de DATABASE_NAME                                       |
| ----------------- | ------------------------------------------------------------ |
| SGBDR             | Le nom de la base de données distante sur le serveur fourni à l’aide de `LOCATION` |
| SHARD_MAP_MANAGER | Nom de la base de données faisant office de Gestionnaire de la carte de partitions      |

Pour un exemple montrant comment créer une source de données externe où `TYPE`=`RDBMS`, consultez [Créer une source de données externe SGBDR](#b-create-an-rdbms-external-data-source)

### <a name="shard_map_name--shard_map_name"></a>SHARD_MAP_NAME = *shard_map_name*

Utilisé lorsque l’argument `TYPE` a la valeur `SHARD_MAP_MANAGER` uniquement pour définir le nom de la carte de partitions.

Pour un exemple montrant comment créer une source de données externe où `TYPE` = `SHARD_MAP_MANAGER`, consultez [Créer une source de données externe de Gestionnaire de la carte des partitions](#a-create-a-shard-map-manager-external-data-source)

## <a name="permissions"></a>Autorisations

Nécessite l’autorisation CONTROL sur la base de données dans SQL Database.

## <a name="locking"></a>Verrouillage

Prend un verrou partagé sur l’objet EXTERNAL DATA SOURCE.  

## <a name="examples"></a>Exemples :

### <a name="a-create-a-shard-map-manager-external-data-source"></a>A. Créer une source de données externe de Gestionnaire de cartes de partitions

Pour créer une source de données externe pour faire référence à SHARD_MAP_MANAGER, spécifiez le nom du serveur SQL Database qui héberge le Gestionnaire de cartes de partitions dans SQL Database ou une base de données SQL Server sur une machine virtuelle.

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>'
;

CREATE DATABASE SCOPED CREDENTIAL ElasticDBQueryCred
WITH
     IDENTITY   = '<username>'
,    SECRET     = '<password>'
;

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc
WITH
(    TYPE             = SHARD_MAP_MANAGER
,    LOCATION         = '<server_name>.database.windows.net'
,    DATABASE_NAME    = 'ElasticScaleStarterKit_ShardMapManagerDb'
,    CREDENTIAL       = ElasticDBQueryCred
,    SHARD_MAP_NAME   = 'CustomerIDShardMap'
)
;
```

Pour un tutoriel détaillé, consultez [Bien démarrer avec les requêtes élastiques pour le partitionnement (partitionnement horizontal)][sharded_eq_tutorial].

### <a name="b-create-an-rdbms-external-data-source"></a>B. Créer une source de données externe de SGBDR

Pour créer une source de données externe pour faire référence à un SGBDR, spécifie le nom du serveur SQL Database de la base de données distante dans SQL Database.

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>'
;

CREATE DATABASE SCOPED CREDENTIAL SQL_Credential  
WITH
     IDENTITY  = '<username>'
,    SECRET    = '<password>'
;

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc
WITH
(    TYPE          = RDBMS
,    LOCATION      = '<server_name>.database.windows.net'
,    DATABASE_NAME = 'Customers'
,    CREDENTIAL    = SQL_Credential
)
;
```

Pour un tutoriel détaillé sur le SGBDR, consultez [Prise en main des requêtes de bases de données croisées (partitionnement vertical)][remote_eq_tutorial].

## <a name="examples-bulk-operations"></a>Exemples : opérations en bloc

> [!NOTE]
> Ne placez pas de **/** en fin, nom de fichier, ou paramètres de signature d’accès partagé à la fin de l’URL `LOCATION` lors de la configuration d’une source de données externe pour les opérations en bloc.

### <a name="c-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage"></a>C. Créer une source de données externe pour les opérations en bloc de récupération de données dans le stockage Blob Azure

Utilisez la source de données suivante pour les opérations en bloc à l’aide de [BULK INSERT][bulk_insert] ou [OPENROWSET][openrowset]. L’identifiant utilisé doit donner à l’identité la valeur `SHARED ACCESS SIGNATURE`, ne doit pas avoir le premier `?` dans le jeton SAS, doit avoir au moins les droits de lecture sur le fichier à charger (par exemple `srt=o&sp=r`), et doit présenter une période d’expiration valide (toutes les dates sont en heure UTC). Pour plus d’informations sur les signatures d’accès partagé, consultez [Utilisation des signatures d’accès partagé (SAP)][sas_token].

```sql
CREATE DATABASE SCOPED CREDENTIAL AccessAzureInvoices
WITH
     IDENTITY = 'SHARED ACCESS SIGNATURE'
--   REMOVE ? FROM THE BEGINNING OF THE SAS TOKEN
,    SECRET = '******srt=sco&sp=rwac&se=2017-02-01T00:55:34Z&st=2016-12-29T16:55:34Z***************'
;

CREATE EXTERNAL DATA SOURCE MyAzureInvoices
WITH
(    LOCATION   = 'https://newinvoices.blob.core.windows.net/week3'
,    CREDENTIAL = AccessAzureInvoices
,    TYPE       = BLOB_STORAGE
)
;
```

Pour voir une utilisation de cet exemple, consultez [BULK INSERT][bulk_insert_example].

## <a name="see-also"></a>Voir aussi

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)][create_dsc]
- [CREATE EXTERNAL TABLE (Transact-SQL)][create_etb]
- [sys.external_data_sources (Transact-SQL)][cat_eds]
- [Utilisation des signatures d’accès partagé (SAP)][sas_token]
- [Vue d’ensemble de la requête élastique][intro_eq]

<!-- links to external pages -->
<!-- SQL Docs -->
[bulk_insert]: https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql
[bulk_insert_example]: https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql#f-importing-data-from-a-file-in-azure-blob-storage
[openrowset]: https://docs.microsoft.com/sql/t-sql/functions/openrowset-transact-sql
[create_dsc]: https://docs.microsoft.com/sql/t-sql/statements/create-database-scoped-credential-transact-sql
[create_etb]: https://docs.microsoft.com/sql/t-sql/statements/create-external-data-source
[alter_eds]: https://docs.microsoft.com/sql/t-sql/statements/alter-external-data-source-transact-sql
[cat_eds]: https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-external-data-sources-transact-sql
<!-- PolyBase docs -->
[intro_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide
[mongodb_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-configure-mongodb
[connectivity_pb]:https://docs.microsoft.com/sql/database-engine/configure-windows/polybase-connectivity-configuration-transact-sql
[connection_options]: https://docs.microsoft.com/sql/relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client
[hint_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-pushdown-computation#force-pushdown
<!-- Elastic Query Docs -->
[intro_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/
[remote_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/
[remote_eq_tutorial]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/
[sharded_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/
[sharded_eq_tutorial]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/

<!-- Azure Docs -->
[azure_ad]: https://docs.microsoft.com/azure/data-lake-store/data-lake-store-authenticate-using-active-directory
[sas_token]: https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

|                                                              |                                                              |                                            |                                                              |      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------ | ------------------------------------------------------------ | ---- |
| [SQL Server](create-external-data-source-transact-sql.md?view=sql-server-2017) | [SQL Database](create-external-data-source-transact-sql.md?view=azuresqldb-current) | **_\* SQL Data<br />Warehouse \*_** &nbsp; | [Analytics Platform<br />System (PDW)](create-external-data-source-transact-sql.md?view=aps-pdw-2016-au7) |      |
|                                                              |                                                              |                                            |                                                              |      |

&nbsp;

## <a name="overview-azure-sql-data-warehouse"></a>Présentation : Azure SQL Data Warehouse.

Crée une source de données externe pour PolyBase. Des sources de données externes sont utilisées pour établir la connectivité et prendre en charge le cas d’utilisation principal suivant : Virtualisation des données et chargement des données à l’aide de [PolyBase][intro_pb]

> [!IMPORTANT]  
> Pour créer une source de données externes afin d’interroger des instances SQL Database Warehouse à l’aide de SQL Database avec des [requêtes élastiques][remote_eq], consultez [SQL Database](create-external-data-source-transact-sql.md?view=azuresqldb-current).

## <a name="syntax"></a>Syntaxe

```sql
CREATE EXTERNAL DATA SOURCE <data_source_name>  
WITH
(    LOCATION                  = '<prefix>://<path>[:<port>]'
[,   CREDENTIAL                = <credential_name> ]
[,   TYPE                      =  HADOOP
)
[;]
```

## <a name="arguments"></a>Arguments

### <a name="data_source_name"></a>data_source_name

Spécifie le nom défini par l’utilisateur de la source de données. Ce nom doit être unique dans la base de données de SQL Data Warehouse (SQL DW).

### <a name="location--prefixpathport"></a>EMPLACEMENT = *`'<prefix>://<path[:port]>'`*

Fournit le protocole de connectivité et le chemin d’accès à la source de données externe.

| Source de données externe        | Préfixe de l’emplacement | Chemin d’emplacement                                         |
| --------------------------- | --------------- | ----------------------------------------------------- |
| Stockage Blob Azure          | `wasb[s]`       | `<container>@<storage_account>.blob.core.windows.net` |
| Azure Data Lake Store Gén. 1 | `adl`           | `<storage_account>.azuredatalake.net`                 |
| Azure Data Lake Store Gén. 2 | `abfs[s]`       | `<container>@<storage_account>.dfs.core.windows.net`  |

Chemin d’emplacement :

- `<container>` = le conteneur du compte de stockage contenant les données. Les conteneurs racines sont en lecture seule, donc les données ne peuvent pas être réécrites sur le conteneur.
- `<storage_account>` = le nom du compte de stockage de la ressource Azure.

Remarques et conseils supplémentaires lors de la définition de l’emplacement :

- L’option par défaut consiste à activer les connexions SSL sécurisées lors du provisionnement d’Azure Data Lake Storage Gen 2. Si cette option est activée, vous devez utiliser `abfss` lorsqu’une connexion SSL sécurisée est sélectionnée. Notez que `abfss` fonctionne également pour les connexions SSL non sécurisées. 
- Le moteur SQL Data Warehouse ne vérifie pas l’existence de la source de données externe lorsque l’objet est créé. Pour valider, créez une table externe à l’aide d’une source de données externe.
- Utilisez la même source de données externe pour toutes les tables lors de l’interrogation de Hadoop afin de garantir la cohérence des paramètres sémantiques de requête.
- `wasb` est le protocole par défaut pour le stockage d’objets blob Azure. `wasbs` est facultatif mais recommandé, car il permet d’envoyer les données au moyen d’une connexion SSL sécurisée.

### <a name="credential--credential_name"></a>CREDENTIAL = *credential_name*

Spécifie les informations d’identification limitées à la base de données servant à l’authentification auprès de la source de données externe.

Remarques et conseils supplémentaires lors de la création d’informations d’identification :

- Pour charger des données en provenance du stockage Blob Azure ou d’Azure Data Lake Store (ADLS) Gén. 2 dans SQL DW, utilisez une clé de stockage Azure.
- `CREDENTIAL` est requis uniquement si le blob a été sécurisé. `CREDENTIAL` n’est pas requis pour les jeux de données qui autorisent l’accès anonyme.

Pour créer des informations d’identification délimitées à la base de données, consultez [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)][create_dsc].

### <a name="type--hadoop"></a>TYPE = *HADOOP*

Spécifie le type de source de données externe en cours de configuration. Ce paramètre n’est pas toujours requis.

- Utilisez HADOOP lorsque la source de données externe est Clouderale Stockage Blob Azure, ADLS Gén. 1 ou ADLS Gén. 2.

> [!IMPORTANT]
> Ne paramétrez pas `TYPE` si vous utilisez toute autre source de données externe.

Pour un exemple d’utilisation de `TYPE` = `HADOOP` pour charger des données depuis le stockage Blob Azure, consultez [Créer une source de données externes pour référencer le stockage blob Azure](#a-create-external-data-source-to-reference-azure-blob-storage).

## <a name="permissions"></a>Autorisations

Nécessite l’autorisation CONTROL sur la base de données dans SQL Data Warehouse.

## <a name="locking"></a>Verrouillage

Prend un verrou partagé sur l’objet EXTERNAL DATA SOURCE.  

## <a name="security"></a>Sécurité

PolyBase prend en charge l’authentification basée sur le proxy pour la plupart de ces sources de données externes. Créez des informations d’identification au niveau de la base de données pour créer le compte proxy.

Lorsque vous vous connectez au stockage ou au pool de données dans un cluster Big data de SQL Server, les informations d’identification de l’utilisateur sont transmises par le système back-end. Créez des connexions dans le pool de données lui-même pour activer l’authentification en transfert direct.

Actuellement un jeton SAP avec le type `HADOOP` n’est pas pris en charge. Il est uniquement pris en charge avec une clé d’accès de compte de stockage. Toute tentative de créer une source de données externe avec le type `HADOOP` et les informations d’identification SAS échoue avec l’erreur :

`Msg 105019, Level 16, State 1 - EXTERNAL TABLE access failed due to internal error: 'Java exception raised on call to HdfsBridge_Connect. Java exception message: Parameters provided to connect to the Azure storage account are not valid.: Error [Parameters provided to connect to the Azure storage account are not valid.] occurred while accessing external file.'`

## <a name="examples"></a>Exemples :

### <a name="a-create-external-data-source-to-reference-azure-blob-storage"></a>A. Créer une source de données externe pour faire référence au stockage d’objets blob Azure

Dans cet exemple, la source de données externe est un conteneur de stockage d’objets blob Azure appelé `daily` sous le compte de stockage Azure nommé `logs`. La source de données externe de stockage Azure sert au transfert des données uniquement. Elle ne prend pas en charge le pushdown de prédicats.

Cet exemple montre comment créer des informations d’identification limitées à la base de données qui serviront à l’authentification auprès du stockage Azure. Spécifiez la clé du compte de stockage Azure dans le secret des informations d’identification de la base de données. Vous pouvez spécifier toute chaîne de l’identité des informations d’identification limitées à la base de données, étant donné qu’elle n’est pas utilisée lors de l’authentification auprès du stockage Azure.

```sql
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo'
;

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential
WITH
     IDENTITY   = '<my_account>'
,    SECRET     = '<azure_storage_account_key>'
;

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage
WITH
(    LOCATION   = 'wasbs://daily@logs.blob.core.windows.net/'
,    CREDENTIAL = AzureStorageCredential
,    TYPE       = HADOOP
)
;
```

### <a name="b-create-external-data-source-to-reference-azure-data-lake-store-gen-1-or-2-using-a-service-principal"></a>B. Créer une source de données externe pour référencer Azure Data Lake Store Gen 1 ou 2 à l’aide d’un principal de service

La connectivité Azure Data Lake Store est basée sur votre URI ADLS et sur le principal de service de votre application Azure Active Directory. La documentation sur la création de cette application est disponible ici : [Authentification auprès de Data Lake Store à l’aide d’Azure Active Directory][azure_ad[].

```sql
-- If you do not have a Master Key on your DW you will need to create one.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>'
;

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLS_credential
WITH
--   IDENTITY   = '<clientID>@<OAuth2.0TokenEndPoint>'
     IDENTITY   = '536540b4-4239-45fe-b9a3-629f97591c0c@https://login.microsoftonline.com/42f988bf-85f1-41af-91ab-2d2cd011da47/oauth2/token'
--,  SECRET     = '<KEY>'
,    SECRET     = 'BjdIlmtKp4Fpyh9hIvr8HJlUida/seM5kQ3EpLAmeDI='
;

-- For Gen 1 - Create an external data source
-- TYPE: HADOOP - PolyBase uses Hadoop APIs to access data in Azure Data Lake Storage.
-- LOCATION: Provide Data Lake Storage Gen 1 account name and URI
-- CREDENTIAL: Provide the credential created in the previous step
CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH
(    LOCATION       = 'adl://newyorktaxidataset.azuredatalakestore.net'
,    CREDENTIAL     = ADLS_credential
,    TYPE           = HADOOP
)
;

-- For Gen 2 - Create an external data source
-- TYPE: HADOOP - PolyBase uses Hadoop APIs to access data in Azure Data Lake Storage.
-- LOCATION: Provide Data Lake Storage Gen 2 account name and URI
-- CREDENTIAL: Provide the credential created in the previous step
CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH
(    LOCATION       = 'abfss://newyorktaxidataset.azuredatalakestore.net' -- Please note the abfss endpoint when your account has secure transfer enabled
,    CREDENTIAL     = ADLS_credential
,    TYPE           = HADOOP
)
;
```

### <a name="c-create-external-data-source-to-reference-azure-data-lake-store-gen-2-using-the-storage-account-key"></a>C. Créer une source de données externe pour référencer Azure Data Lake Store Gen 2 à l’aide d’une clé de compte de stockage

```sql
-- If you do not have a Master Key on your DW you will need to create one.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>'
;

CREATE DATABASE SCOPED CREDENTIAL ADLS_credential
WITH
--   IDENTITY   = '<storage_account_name>'
     IDENTITY   = 'newyorktaxidata'
--,  SECRET     = '<storage_account_key>'
,    SECRET     = 'yz5N4+bxSb89McdiysJAzo+9hgEHcJRJuXbF/uC3mhbezES/oe00vXnZEl14U0lN3vxrFKsphKov16C0w6aiTQ=='
;

-- Note this example uses a Gen 2 secured endpoint (abfss)
CREATE EXTERNAL DATA SOURCE <data_source_name>
WITH
(    LOCATION   = 'abfss://2013@newyorktaxidataset.dfs.core.windows.net'
,    CREDENTIAL = ADLS_credential
,    TYPE       = HADOOP
)
[;]
```

### <a name="d-create-external-data-source-to-reference-polybase-connectivity-to-azure-data-lake-store-gen-2"></a>D. Créer une source de données externe pour faire référence à la connectivité PolyBase à Azure Data Lake Store Gen 2

Il n’est pas nécessaire de spécifier SECRET lors de la connexion au compte Azure Data Lake Store Gen2 avec un mécanisme d’[identité managée](/azure/active-directory/managed-identities-azure-resources/overview
).

```sql
-- If you do not have a Master Key on your DW you will need to create one
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>'

--Create database scoped credential with **IDENTITY = 'Managed Service Identity'**

CREATE DATABASE SCOPED CREDENTIAL msi_cred WITH IDENTITY = 'Managed Service Identity';

--Create external data source with abfss:// scheme for connecting to your Azure Data Lake Store Gen2 account

CREATE EXTERNAL DATA SOURCE ext_datasource_with_abfss WITH (TYPE = hadoop, LOCATION = 'abfss://myfile@mystorageaccount.dfs.core.windows.net', CREDENTIAL = msi_cred);
```

## <a name="see-also"></a>Voir aussi

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)][create_dsc]
- [CREATE EXTERNAL FILE FORMAT (Transact-SQL)][create_eff]
- [CREATE EXTERNAL TABLE (Transact-SQL)][create_etb]
- [CREATE EXTERNAL TABLE AS SELECT (Azure SQL Data Warehouse)][create_etb_as_sel]
- [CREATE TABLE AS SELECT (Azure SQL Data Warehouse)][create_tbl_as_sel]
- [sys.external_data_sources (Transact-SQL)][cat_eds]
- [Utilisation des signatures d’accès partagé (SAP)][sas_token]

<!-- links to external pages -->
<!-- SQL Docs -->
[bulk_insert]: https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql
[bulk_insert_example]: https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql#f-importing-data-from-a-file-in-azure-blob-storage
[openrowset]: https://docs.microsoft.com/sql/t-sql/functions/openrowset-transact-sql

[create_dsc]: https://docs.microsoft.com/sql/t-sql/statements/create-database-scoped-credential-transact-sql
[create_eff]: https://docs.microsoft.com/sql/t-sql/statements/create-external-file-format-transact-sql
[create_etb]: https://docs.microsoft.com/sql/t-sql/statements/create-external-data-source
[create_etb_as_sel]: https://docs.microsoft.com/sql/t-sql/statements/create-external-table-as-select-transact-sql?view=azure-sqldw-latest
[create_tbl_as_sel]: https://docs.microsoft.com/sql/t-sql/statements/create-table-as-select-azure-sql-data-warehouse?view=azure-sqldw-latest

[alter_eds]: https://docs.microsoft.com/sql/t-sql/statements/alter-external-data-source-transact-sql

[cat_eds]: https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-external-data-sources-transact-sql
<!-- PolyBase docs -->
[intro_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide
[mongodb_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-configure-mongodb
[connectivity_pb]:https://docs.microsoft.com/sql/database-engine/configure-windows/polybase-connectivity-configuration-transact-sql
[connection_options]: https://docs.microsoft.com/sql/relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client
[hint_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-pushdown-computation#force-pushdown
<!-- Elastic Query Docs -->
[intro_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/
[remote_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/
[remote_eq_tutorial]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/
[sharded_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/
[sharded_eq_tutorial]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/

<!-- Azure Docs -->
[azure_ad]: https://docs.microsoft.com/azure/data-lake-store/data-lake-store-authenticate-using-active-directory
[sas_token]: https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1

::: moniker-end
::: moniker range=">=aps-pdw-2016||=sqlallproducts-allversions"

|                                                              |                                                              |                                                              |                                                         |      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------- | ---- |
| [SQL Server](create-external-data-source-transact-sql.md?view=sql-server-2017) | [SQL Database](create-external-data-source-transact-sql.md?view=azuresqldb-current) | [SQL Data<br />Warehouse](create-external-data-source-transact-sql.md?view=azure-sqldw-latest) | **_\* Analytics<br />Platform System (PDW) \*_** &nbsp; |      |
|                                                              |                                                              |                                                              |                                                         |      |

&nbsp;

## <a name="overview-analytics-platform-system"></a>Présentation : Système de la plateforme d'analyse

Crée une source de données externe pour des requêtes PolyBase. Des sources de données externes sont utilisées pour établir la connectivité et prendre en charge le cas d’utilisation suivant : Virtualisation des données et chargement des données à l’aide de [PolyBase][intro_pb]

## <a name="syntax"></a>Syntaxe

```sql
CREATE EXTERNAL DATA SOURCE <data_source_name>  
WITH
(    LOCATION                  = '<prefix>://<path>[:<port>]'
[,   CREDENTIAL                = <credential_name> ]
[,   TYPE                      = HADOOP ]
[,   RESOURCE_MANAGER_LOCATION = '<resource_manager>[:<port>]'
)
[;]
```

## <a name="arguments"></a>Arguments

### <a name="data_source_name"></a>data_source_name

Spécifie le nom défini par l’utilisateur de la source de données. Le nom doit être unique au sein du serveur dans le système de la plateforme d’analyse (Parallel Data Warehouse ou PDW).

### <a name="location--prefixpathport"></a>EMPLACEMENT = *`'<prefix>://<path[:port]>'`*

Fournit le protocole de connectivité et le chemin d’accès à la source de données externe.

| Source de données externe    | Préfixe de l’emplacement | Chemin d’emplacement                                         |
| ----------------------- | --------------- | ----------------------------------------------------- |
| Cloudera ou Hortonworks | `hdfs`          | `<Namenode>[:port]`                                   |
| Stockage Blob Azure      | `wasb[s]`       | `<container>@<storage_account>.blob.core.windows.net` |

Chemin d’emplacement :

- `<`NameNode`>` = Nom de la machine, nom de l’URI de service ou adresse IP du `Namenode` du cluster Hadoop. PolyBase doit résoudre tous les noms DNS utilisés par le cluster Hadoop. <!-- For highly available Hadoop configurations, provide the Nameservice ID as the `LOCATION`. -->
- `port` = Le port d’écoute de la source de données externe. Dans Hadoop, le port se trouve à l’aide du paramètre de configuration `fs.defaultFS`. La valeur par défaut est 8020.
- `<container>` = le conteneur du compte de stockage contenant les données. Les conteneurs racines sont en lecture seule, donc les données ne peuvent pas être réécrites sur le conteneur.
- `<storage_account>` = le nom du compte de stockage de la ressource Azure.

Remarques et conseils supplémentaires lors de la définition de l’emplacement :

- Le moteur PDW ne vérifie pas l’existence de la source de données externe lorsque l’objet est créé. Pour valider, créez une table externe à l’aide d’une source de données externe.
- Utilisez la même source de données externe pour toutes les tables lors de l’interrogation de Hadoop afin de garantir la cohérence des paramètres sémantiques de requête.
- `wasb` est le protocole par défaut pour le stockage d’objets blob Azure. `wasbs` est facultatif mais recommandé, car il permet d’envoyer les données au moyen d’une connexion SSL sécurisée.
- Pour garantir la réussite des requêtes PolyBase lors du basculement du `Namenode` Hadoop, envisagez d’utiliser une adresse IP virtuelle pour le `Namenode`du cluster Hadoop. Dans le cas contraire, exécutez une commande [ALTER EXTERNAL DATA SOURCE][alter_eds] pour pointer vers le nouvel emplacement.

### <a name="credential--credential_name"></a>CREDENTIAL = *credential_name*

Spécifie les informations d’identification limitées à la base de données servant à l’authentification auprès de la source de données externe.

Remarques et conseils supplémentaires lors de la création d’informations d’identification :

- Pour charger des données en provenance du stockage Blob Azure ou d’Azure Data Lake Store (ADLS) Gén. 2 dans SQL DW ou PDW, utilisez une clé de stockage Azure.
- `CREDENTIAL` est requis uniquement si le blob a été sécurisé. `CREDENTIAL` n’est pas requis pour les jeux de données qui autorisent l’accès anonyme.

### <a name="type---hadoop-"></a>TYPE = *[ HADOOP ]*

Spécifie le type de source de données externe en cours de configuration. Ce paramètre n’est pas toujours requis.

- Utilisez HADOOP lorsque la source de données externe est Cloudera, Hortonworks ou Stockage Blob Azure.

> [!IMPORTANT]
> Ne paramétrez pas `TYPE` si vous utilisez toute autre source de données externe.

Pour un exemple d’utilisation de `TYPE` = `HADOOP` pour charger des données depuis le stockage Blob Azure, consultez [Créer une source de données externes pour référencer le stockage blob Azure](#d-create-external-data-source-to-reference-azure-blob-storage).

### <a name="resource_manager_location--resourcemanager_uriport"></a>RESOURCE_MANAGER_LOCATION = *'ResourceManager_URI[:port]'*

Configurez cette valeur facultative lors de la connexion à Hortonworks ou Cloudera.

Lorsque `RESOURCE_MANAGER_LOCATION` est défini, l’optimiseur de requête prend une décision basée sur le coût pour améliorer les performances. Une tâche MapReduce peut être utilisée pour transmettre le calcul à Hadoop. En spécifiant `RESOURCE_MANAGER_LOCATION`, il est possible de considérablement réduire le volume des données transférées entre Hadoop et SQL, ce qui peut donc améliorer les performances des requêtes.  

Si le Gestionnaire des ressources n’est pas spécifié, le transfert de calcul dans Hadoop est désactivé pour les requêtes PolyBase.

Si le port n’est pas spécifié, la valeur par défaut est déterminée d’après le paramètre actuel de la configuration de la « connexion à hadoop ».

| Connexion Hadoop | Port du Gestionnaire de ressources par défaut |
| ------------------- | ----------------------------- |
| 1                   | 50300                         |
| 2                   | 50300                         |
| 3                   | 8021                          |
| 4                   | 8032                          |
| 5                   | 8050                          |
| 6                   | 8032                          |
| 7                   | 8050                          |

Pour obtenir la liste complète des versions de Hadoop prises en charge, consultez [Configuration de la connectivité PolyBase (Transact-SQL)][connectivity_pb].

> [!IMPORTANT]  
> La valeur RESOURCE_MANAGER_LOCATION n’est pas validée lorsque vous créez la source de données externe. La saisie d’une valeur incorrecte peut entraîner l’échec de la requête au moment de l’exécution chaque fois qu’une transmission est tentée, étant donné que la valeur fournie ne serait pas en mesure d’être résolue.

[Créer une source de données externe pour faire référence à Hadoop avec la transmission activée](#b-create-external-data-source-to-reference-hadoop-with-push-down-enabled) fournit un exemple concret ainsi que des instructions complémentaires.

## <a name="permissions"></a>Autorisations

Nécessite l’autorisation CONTROL sur la base de données dans le système de la plateforme d’analyse (Parallel Data Warehouse ou PDW).

> [!NOTE]
> Dans les versions précédentes de PDW, la création d’une source de données externe nécessitait des autorisations ALTER ANY EXTERNAL DATA SOURCE.

## <a name="locking"></a>Verrouillage

Prend un verrou partagé sur l’objet EXTERNAL DATA SOURCE.  

## <a name="security"></a>Sécurité

PolyBase prend en charge l’authentification basée sur le proxy pour la plupart de ces sources de données externes. Créez des informations d’identification au niveau de la base de données pour créer le compte proxy.

Actuellement un jeton SAP avec le type `HADOOP` n’est pas pris en charge. Il est uniquement pris en charge avec une clé d’accès de compte de stockage. Toute tentative de créer une source de données externe avec le type `HADOOP` et les informations d’identification SAS échoue avec l’erreur :

`Msg 105019, Level 16, State 1 - EXTERNAL TABLE access failed due to internal error: 'Java exception raised on call to HdfsBridge_Connect. Java exception message: Parameters provided to connect to the Azure storage account are not valid.: Error [Parameters provided to connect to the Azure storage account are not valid.] occurred while accessing external file.'`

## <a name="examples"></a>Exemples :

### <a name="a-create-external-data-source-to-reference-hadoop"></a>A. Créer une source de données externe pour faire référence à Hadoop

Pour créer une source de données externe pour faire référence à votre cluster Hortonworks ou Cloudera Hadoop, spécifiez le nom de l’ordinateur ou l’adresse IP du port et du `Namenode` Hadoop. <!-- Provide the Nameservice ID as the `LOCATION` for highly available configurations. -->

```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH
(    LOCATION = 'hdfs://10.10.10.10:8050'
,    TYPE     = HADOOP
)
;
```

### <a name="b-create-external-data-source-to-reference-hadoop-with-push-down-enabled"></a>B. Créer une source de données externe pour faire référence à Hadoop avec transmission activée

Spécifiez l’option `RESOURCE_MANAGER_LOCATION` pour activer le calcul transmis à Hadoop pour des requêtes PolyBase. Une fois activé, PolyBase prend une décision basée sur les coûts pour déterminer si le calcul de la requête doit être poussé vers Hadoop.

```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH
(    LOCATION                  = 'hdfs://10.10.10.10:8020'
,    TYPE                      = HADOOP
,    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
)
;
```

### <a name="c-create-external-data-source-to-reference-kerberos-secured-hadoop"></a>C. Créer une source de données externe pour faire référence à Hadoop sécurisé par Kerberos

Pour vérifier si le cluster Hadoop est sécurisé par Kerberos, regardez la valeur de la propriété hadoop.security.authentication dans Hadoop core-site.xml. Pour faire référence à un cluster Hadoop sécurisé par Kerberos, vous devez spécifier des informations d’identification limitées à la base de données qui contiennent votre nom d’utilisateur et votre mot de passe Kerberos. La clé principale de la base de données est utilisée pour chiffrer le secret des informations d’identification limitées à la base de données.

```sql  
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo'
;

-- Create a database scoped credential with Kerberos user name and password.
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1
WITH
     IDENTITY   = '<hadoop_user_name>'
,    SECRET     = '<hadoop_password>'
;

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH
(    LOCATION                  = 'hdfs://10.10.10.10:8050'
,    CREDENTIAL                = HadoopUser1
,    TYPE                      = HADOOP
,    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
)
;
```

### <a name="d-create-external-data-source-to-reference-azure-blob-storage"></a>D. Créer une source de données externe pour faire référence au stockage d’objets blob Azure

Dans cet exemple, la source de données externe est un conteneur de stockage d’objets blob Azure appelé `daily` sous le compte de stockage Azure nommé `logs`. La source de données externe de stockage Azure sert au transfert des données uniquement. Elle ne prend pas en charge le pushdown de prédicats.

Cet exemple montre comment créer des informations d’identification limitées à la base de données qui serviront à l’authentification auprès du stockage Azure. Spécifiez la clé du compte de stockage Azure dans le secret des informations d’identification de la base de données. Vous pouvez spécifier toute chaîne de l’identité des informations d’identification limitées à la base de données, étant donné qu’elle n’est pas utilisée lors de l’authentification auprès du stockage Azure.

```sql
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo'
;

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential
WITH
     IDENTITY   = '<my_account>'
,    SECRET     = '<azure_storage_account_key>'
;

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage
WITH
(    LOCATION   = 'wasbs://daily@logs.blob.core.windows.net/'
,    CREDENTIAL = AzureStorageCredential
,    TYPE       = HADOOP
)
;
```

## <a name="see-also"></a>Voir aussi

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)][create_dsc]
- [CREATE EXTERNAL FILE FORMAT (Transact-SQL)][create_eff]
- [CREATE EXTERNAL TABLE (Transact-SQL)][create_etb]
- [sys.external_data_sources (Transact-SQL)][cat_eds]
- [Utilisation des signatures d’accès partagé (SAP)][sas_token]

<!-- links to external pages -->
<!-- SQL Docs -->
[bulk_insert]: https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql
[bulk_insert_example]: https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql#f-importing-data-from-a-file-in-azure-blob-storage
[openrowset]: https://docs.microsoft.com/sql/t-sql/functions/openrowset-transact-sql

[create_dsc]: https://docs.microsoft.com/sql/t-sql/statements/create-database-scoped-credential-transact-sql
[create_eff]: https://docs.microsoft.com/sql/t-sql/statements/create-external-file-format-transact-sql
[create_etb]: https://docs.microsoft.com/sql/t-sql/statements/create-external-data-source
[create_etb_as_sel]: https://docs.microsoft.com/sql/t-sql/statements/create-external-table-as-select-transact-sql?view=azure-sqldw-latest
[create_tbl_as_sel]: https://docs.microsoft.com/sql/t-sql/statements/create-table-as-select-azure-sql-data-warehouse?view=azure-sqldw-latest

[alter_eds]: https://docs.microsoft.com/sql/t-sql/statements/alter-external-data-source-transact-sql

[cat_eds]: https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-external-data-sources-transact-sql
<!-- PolyBase docs -->
[intro_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide
[mongodb_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-configure-mongodb
[connectivity_pb]:https://docs.microsoft.com/sql/database-engine/configure-windows/polybase-connectivity-configuration-transact-sql
[connection_options]: https://docs.microsoft.com/sql/relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client
[hint_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-pushdown-computation#force-pushdown
<!-- Elastic Query Docs -->
[intro_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/
[remote_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/
[remote_eq_tutorial]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/
[sharded_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/
[sharded_eq_tutorial]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/

<!-- Azure Docs -->
[azure_ad]: https://docs.microsoft.com/azure/data-lake-store/data-lake-store-authenticate-using-active-directory
[sas_token]: https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1

::: moniker-end
