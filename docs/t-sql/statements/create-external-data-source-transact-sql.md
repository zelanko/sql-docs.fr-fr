---
title: "CRÉER la SOURCE de données externe (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL DATA SOURCE
- CREATE_EXTERNAL_DATA_SOURCE
dev_langs: TSQL
helpviewer_keywords:
- External
- External, data source
- PolyBase, create data source
ms.assetid: 75d8a220-0f4d-4d91-8ba4-9d852b945509
caps.latest.revision: "58"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 283971bbd1bfe04b26860f56601c315ac5244717
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="create-external-data-source-transact-sql"></a>CRÉER la SOURCE de données externe (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Crée une source de données externe pour PolyBase, les requêtes de base de données élastique ou le stockage Blob Azure. Selon le scénario, la syntaxe diffère considérablement. Une source de données créée pour PolyBase ne peut pas être utilisée pour les requêtes de base de données élastique.  De même, une source de données créée pour les requêtes de base de données élastique ne peut pas être utilisée pour PolyBase, etc. 
  
> [!NOTE]  
>  PolyBase est pris en charge uniquement sur SQL Server 2016, Azure SQL Data Warehouse et Parallel Data Warehouse. Les requêtes de base de données élastiques sont pris en charge uniquement sur la base de données SQL Azure v12 ou une version ultérieure.  
  
 Pour les scénarios de PolyBase, la source de données externe est un système de fichiers Hadoop (HDFS), un conteneur d’objets blob de stockage Azure ou Azure Data Lake Store. Pour plus d’informations, consultez [Prise en main de PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).  
  
 Pour les scénarios de requête de base de données élastique, la source externe est un gestionnaire de carte de partitions (sur la base de données SQL Azure), ou d’une base de données distant (sur la base de données SQL Azure).  Utilisez [sp_execute_remote &#40; Base de données SQL Azure &#41; ](../../relational-databases/system-stored-procedures/sp-execute-remote-azure-sql-database.md) après la création d’une source de données externe. Pour plus d’informations, consultez [requête de base de données élastique](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  

  Les données externes du stockage Azure Blob source prend en charge `BULK INSERT` et `OPENROWSET` syntaxe et est différente de stockage d’objets Blob Azure pour PolyBase.
    
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- PolyBase only:  Hadoop cluster as data source   
-- (on SQL Server 2016)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = HADOOP,
        LOCATION = 'hdfs://NameNode_URI[:port]'  
        [, RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI[:port]' ]  
        [, CREDENTIAL = credential_name ]
    )
[;]  
  
-- PolyBase only: Azure Storage Blob as data source   
-- (on SQL Server 2016 and Azure SQL Data Warehouse)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = HADOOP,  
        LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'
        [, CREDENTIAL = credential_name ]
    )  
[;]

-- PolyBase only: Azure Data Lake Store
-- (on Azure SQL Data Warehouse)
CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (
    TYPE = HADOOP,
    LOCATION = 'adl://<AzureDataLake account_name>.azuredatalake.net',
    CREDENTIAL = AzureStorageCredential
);

-- PolyBase only: Hadoop cluster as data source
-- (on Parallel Data Warehouse)
CREATE EXTERNAL DATA SOURCE data_source_name
    WITH ( 
        TYPE = HADOOP, 
        LOCATION = 'hdfs://NameNode_URI[:port]'
        [, JOB_TRACKER_LOCATION = 'JobTracker_URI[:port]' ]
    )
[;]

-- PolyBase only: Azure Storage Blob as data source 
-- (on Parallel Data Warehouse)
CREATE EXTERNAL DATA SOURCE data_source_name
    WITH ( 
        TYPE = HADOOP,
        LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'
    )
[;]
  
-- Elastic Database query only: a shard map manager as data source   
-- (only on Azure SQL Database)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = SHARD_MAP_MANAGER,  
        LOCATION = '<server_name>.database.windows.net',  
        DATABASE_NAME = '\<ElasticDatabase_ShardMapManagerDb'>,  
        CREDENTIAL = <ElasticDBQueryCred>,  
        SHARD_MAP_NAME = '<ShardMapName>'  
    )  
[;]  
  
-- Elastic Database query only: a remote database on Azure SQL Database as data source   
-- (only on Azure SQL Database)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = RDBMS,  
        LOCATION = '<server_name>.database.windows.net',  
        DATABASE_NAME = '<Remote_Database_Name>',  
        CREDENTIAL = <SQL_Credential>  
    )  
[;]  

-- Bulk operations only: Azure Storage Blob as data source   
-- (on SQL Server 2017 or later, and Azure SQL Database).
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = BLOB_STORAGE,  
        LOCATION = 'https://storage_account_name.blob.core.windows.net/container_name'
        [, CREDENTIAL = credential_name ]
    )  
```  
  
## <a name="arguments"></a>Arguments  
 *data_source_name* Spécifie le nom défini par l’utilisateur pour la source de données. Le nom doit être unique au sein de la base de données SQL Server, base de données SQL Azure et Azure SQL Data Warehouse. Le nom doit être unique au sein du serveur dans Parallel Data Warehouse.
  
 TYPE = [HADOOP | SHARD_MAP_MANAGER | SGBDR | BLOB_STORAGE]  
 Spécifie le type de source de données. Utiliser HADOOP lorsque la source de données externes est Hadoop ou un objet blob de stockage Azure pour Hadoop. Utilisez SHARD_MAP_MANAGER lors de la création d’une source de données externe pour la requête de base de données élastique pour le partitionnement de base de données SQL Azure. Utilisez SGBDR avec les sources de données externes pour les requêtes entre bases de données avec la requête de base de données élastique de base de données SQL Azure.  Utilisez BLOB_STORAGE lors de l’exécution des opérations en bloc à l’aide de [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) ou [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) avec [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].
  
EMPLACEMENT = \<location_path > **HADOOP**    
Pour HADOOP, spécifie l’URI Uniform Resource Indicator () pour un cluster Hadoop.  
`LOCATION = 'hdfs:\/\/*NameNode\_URI*\[:*port*\]'`  
NameNode_URI : Le nom de l’ordinateur ou l’adresse IP du cluster Hadoop Namenode.  
port : port le Namenode IPC. Cela est indiqué par le paramètre de configuration fs.default.name dans Hadoop. Si la valeur n’est pas spécifiée, 8020 est utilisé par défaut.  
Exemple : `LOCATION = 'hdfs://10.10.10.10:8020'`

Pour le stockage d’objets blob Azure avec Hadoop, spécifie l’URI pour la connexion au stockage d’objets blob Azure.  
`LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'`  
wasb [s] : Spécifie le protocole de stockage d’objets blob Azure. Le [s] est facultatif et spécifie une connexion SSL sécurisée ; données envoyées à partir de SQL Server sont chiffrées en toute sécurité via le protocole SSL. Nous vous recommandons vivement d’à l’aide de 'wasbs' au lieu de 'wasb'. Notez que l’emplacement peut utiliser asv [s] wasb [s] à la place. La syntaxe asv [s] est déconseillée et sera supprimée dans une version ultérieure.  
conteneur : Spécifie le nom du conteneur de stockage d’objets blob Azure. Pour spécifier le conteneur racine d’un domaine compte de stockage, utilisez le nom de domaine au lieu du nom de conteneur. Conteneurs de racine sont en lecture seule, afin de données ne peut pas être réécrites sur le conteneur.  
account_name : le nom de domaine complet (FQDN) du compte de stockage Azure.  
Exemple : `LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'`

Pour Azure Data Lake Store, emplacement spécifie l’URI pour la connexion à votre Azure Data Lake Store.



**SHARD_MAP_MANAGER**   
 Pour SHARD_MAP_MANAGER, spécifie le nom du serveur logique qui héberge le Gestionnaire de carte de partitions dans la base de données SQL Azure ou d’une base de données SQL Server sur une machine virtuelle Azure.
 
 ```
 CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL ElasticDBQueryCred  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc WITH
  (TYPE = SHARD_MAP_MANAGER,
  LOCATION = '<server_name>.database.windows.net',
  DATABASE_NAME = 'ElasticScaleStarterKit_ShardMapManagerDb',
  CREDENTIAL = ElasticDBQueryCred,
  SHARD_MAP_NAME = 'CustomerIDShardMap'
) ;
```

Pour obtenir un didacticiel, consultez [mise en route avec les requêtes élastiques pour le partitionnement (partitionnement horizontal)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/).
  
**SGBDR**   
Pour le SGBDR, spécifie le nom du serveur logique de la base de données distante dans la base de données SQL Azure.  

```  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';  
  
CREATE DATABASE SCOPED CREDENTIAL SQL_Credential    
WITH IDENTITY = '<username>',  
SECRET = '<password>';  
  
CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc WITH   
    (TYPE = RDBMS,   
    LOCATION = '<server_name>.database.windows.net',   
    DATABASE_NAME = 'Customers',   
    CREDENTIAL = SQL_Credential   
) ;   
```  
  
Pour obtenir un didacticiel sur le SGBDR, consultez [mise en route avec les requêtes de bases de données croisées (partitionnement vertical)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/).  

**BLOB_STORAGE**   
Pour les opérations en bloc uniquement, `LOCATION` doit être valide l’URL pour le stockage d’objets Blob Azure et le conteneur. Ne placez pas  **/** , nom de fichier ou partage les paramètres de signature d’accès à la fin de la `LOCATION` URL.   
Les informations d’identification utilisées, doivent être créés à l’aide de `SHARED ACCESS SIGNATURE` comme identité. Pour plus d’informations sur les signatures d’accès partagé, consultez [Utilisation des signatures d’accès partagé (SAP)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1). Pour obtenir un exemple de l’accès de stockage d’objets blob, consultez l’exemple F de [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md). 

  
 RESOURCE_MANAGER_LOCATION = '*ResourceManager_URI*[ :*port*]'  
 Spécifie l’emplacement du Gestionnaire de ressources Hadoop. Si spécifié, l’optimiseur de requête peut prendre une décision de coût pour pré-traiter les données d’une requête PolyBase à l’aide des fonctionnalités de calcul de Hadoop avec MapReduce. Appelé des prédicats, cela peut considérablement réduire le volume de données transférées entre SQL et Hadoop et par conséquent, améliorer les performances des requêtes.  
  
 Lorsque cela n’est pas spécifié, en exécutant un push de calcul à Hadoop est désactivé pour les requêtes PolyBase.  
 
Si le port n’est pas spécifié, la valeur par défaut est déterminée à l’aide de la valeur actuelle pour la configuration de « connexion à hadoop ».

|Connectivité Hadoop|Port du Gestionnaire de ressources par défaut|
|-------------------|-----------------------------|
| 1|50300|
|2|50300|
|3|8021|
|4|8032|
|5|8050|
|6|8032|
|7|8050|

Pour obtenir une liste complète des versions prises en charge par chaque valeur de la connectivité et des distributions Hadoop, consultez [PolyBase Connectivity Configuration (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).
  
> [!IMPORTANT]  
>  La valeur RESOURCE_MANAGER_LOCATION est une chaîne et n’est pas validée lorsque vous créez la source de données externe. Entrez une valeur incorrecte peut entraîner des retards futures lors de l’accès à l’emplacement.  
  
 Exemples de Hadoop :  
  
-   Hortonworks HDP 2.0, 2.1 et 2.2. 2.3 sur Windows :   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
-   Hortonworks HDP 1.3 sur Windows :   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:50300'  
    ```  
  
-   Hortonworks HDP 2.0, 2.1, 2.2 et 2.3 sur Linux :   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8050'  
    ```  
  
-   Hortonworks HDP 1.3 sur Linux :   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:50300'  
    ```  
  
-   Cloudera 4.3 sur Linux :   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8021'  
    ```  
  
-   Cloudera 5.1-5.11 sur Linux :   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
 Informations d’identification = *credential_name*  
 Spécifie les informations d’identification étendue de base de données pour l’authentification auprès de la source de données externe. Pour obtenir un exemple, consultez [C. création d’une source de données externe du stockage blob Azure](../../t-sql/statements/create-external-data-source-transact-sql.md#credential). Pour créer les informations d’identification, consultez [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md). Notez que les informations d’identification ne sont pas requises pour les jeux de données publics qui autorise l’accès anonyme. 
  
 Nom_base_de_données = *'QueryDatabaseName'*  
 Le nom de la base de données qui fonctionne comme le Gestionnaire de carte de partitions (pour SHARD_MAP_MANAGER) ou la base de données à distance (pour le SGBDR).  
  
 SHARD_MAP_NAME = *'ShardMapName'*  
 Pour SHARD_MAP_MANAGER. Le nom de la carte de partitions. Pour plus d’informations sur la création d’une carte de partitions, consultez [mise en route de la requête de base de données élastique](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/)  
  
## <a name="polybase-specific-notes"></a>Notes spécifiques PolyBase  
Pour obtenir une liste complète des sources de données externes prises en charge, consultez [PolyBase Connectivity Configuration (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).

 Pour utiliser PolyBase, vous devez créer ces trois objets :  
  
-   Source de données externe.  
  
-   Un format de fichier externe, et  
  
-   Une table externe qui fait référence à la source de données externe et le format de fichier externe.  
  
## <a name="permissions"></a>Autorisations  
 Requiert l’autorisation CONTROL sur la base de données dans l’entrepôt de données SQL, SQL Server, APS 2016 et base de données SQL.

> [!IMPORTANT]  
>  Dans les versions précédentes de PDW, créer des autorisations ALTER ANY EXTERNAL DATA SOURCE externe de données source requis.
  
  
## <a name="error-handling"></a>Gestion des erreurs  
 Une erreur d’exécution se produira si les sources de données Hadoop externes ne sont pas cohérents sur ayant RESOURCE_MANAGER_LOCATION défini. Autrement dit, vous ne pouvez pas spécifier deux sources de données externes qui référencent le même cluster Hadoop, puis en fournissant emplacement du Gestionnaire de ressources pour un et pas pour les autres.  
  
 Le moteur SQL ne vérifie pas l’existence de la source de données externe lorsqu’il crée l’objet de source de données externe. Si la source de données n’existe pas pendant l’exécution de requête, une erreur se produit.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
Pour PolyBase, la source de données externe est étendue de base de données dans SQL Server et SQL Data Warehouse. Il est à portée de serveur dans Parallel Data Warehouse.
  
Pour PolyBase, lorsque RESOURCE_MANAGER_LOCATION ou JOB_TRACKER_LOCATION est défini, l’optimiseur de requête considère que l’optimisation de chaque requête en lançant une carte réduire le travail sur la source externe de Hadoop et transmettant le calcul. C’est une décision basée sur les coûts.  

Pour garantir des requêtes PolyBase réussies en cas de basculement de Hadoop NameNode, envisagez d’utiliser une adresse IP virtuelle pour le NameNode du cluster Hadoop. Si vous n’utilisez pas une adresse IP virtuelle pour le Hadoop NameNode, en cas de basculement Hadoop NameNode avoir pour objet de modifier la SOURCE de données externe pour pointer vers le nouvel emplacement.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Toutes les sources de données définies sur le même emplacement de cluster Hadoop doivent utiliser le même paramètre pour RESOURCE_MANAGER_LOCATION ou JOB_TRACKER_LOCATION. S’il existe une incohérence, une erreur d’exécution se produit.  
  
 Si le cluster Hadoop est configuré avec un nom et la source de données externe utilise l’adresse IP de l’emplacement du cluster, PolyBase doit toujours être en mesure de résoudre le nom du cluster lorsque la source de données est utilisée. Pour résoudre le nom, vous devez activer un redirecteur DNS.  
  
## <a name="locking"></a>Verrouillage  
 Acquiert un verrou partagé sur l’objet de SOURCE de données externe.  
  
##  <a name="examples"></a>Exemples : SQL Server 2016  
  
### <a name="a-create-external-data-source-to-reference-hadoop"></a>A. Créer la source de données externe en référence Hadoop  
Pour créer une source de données externe pour faire référence à votre cluster Hortonworks ou des Cloudera Hadoop, spécifiez le nom de l’ordinateur ou adresse IP Hadoop Namenode et le port.  
  
```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8050'
);

```  
  
### <a name="b-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>B. Créer de source de données externe en référence Hadoop avec poussée vers le bas activée  
Spécifiez l’option RESOURCE_MANAGER_LOCATION pour activer la transmission des calculs à Hadoop des requêtes PolyBase. Une fois activé, PolyBase utilise une décision basée sur les coûts pour déterminer si le calcul de la requête doit-elle être envoyée à Hadoop ou toutes les données doivent être déplacées pour traiter la requête dans SQL Server.
  
```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
);

```
  
###  <a name="credential"></a> C. Créer la source de données externe pour faire référence à Hadoop sécurisé Kerberos  
Pour vérifier si le cluster Hadoop sécurisé Kerberos, vérifiez la valeur de propriété hadoop.security.authentication dans Hadoop core-site.Xml. Pour faire référence à un cluster Hadoop sécurisé Kerberos, vous devez spécifier les informations d’identification d’une étendue de la base de données qui contient votre nom d’utilisateur Kerberos et le mot de passe. La clé principale de base de données est utilisée pour chiffrer le secret des informations d’identification incluses dans l’étendue de base de données. 
  
```sql  
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';

-- Create a database scoped credential with Kerberos user name and password.
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1 
WITH IDENTITY = '<hadoop_user_name>', 
SECRET = '<hadoop_password>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (
    TYPE = HADOOP, 
    LOCATION = 'hdfs://10.10.10.10:8050', 
    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050', 
    CREDENTIAL = HadoopUser1
);
```

### <a name="d-create-external-data-source-to-reference-azure-blob-storage"></a>D. Créer la source de données externe pour référencer le stockage d’objets blob Azure
Pour créer une source de données externe pour faire référence à votre conteneur de stockage d’objets blob Azure, spécifiez l’URI de stockage d’objets blob Azure et les informations d’identification d’une étendue de la base de données qui contient votre clé de compte de stockage Azure.

Dans cet exemple, la source de données externe est un conteneur de stockage d’objets blob Azure appelé dailylogs sous le compte de stockage Azure nommé mon compte. Le stockage Azure source de données externe pour le transfert de données uniquement. et il ne prend pas en charge la pile de prédicats.

Cet exemple montre comment créer les informations d’identification de base de données d’une étendue pour l’authentification dans le stockage Azure. Le mot de passe des informations d’identification de base de données, spécifiez la clé de compte de stockage Azure. Spécifiez l’identité des informations d’identification d’une étendue n’importe quelle chaîne dans la base de données, il n’est pas utilisé pour l’authentification dans le stockage Azure. Ensuite, les informations d’identification sont utilisée dans l’instruction qui crée une source de données externe.

```
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential 
WITH IDENTITY = 'myaccount', 
SECRET = '<azure_storage_account_key>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
    TYPE = HADOOP, 
    LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/',
    CREDENTIAL = AzureStorageCredential
);
```

## <a name="examples-azure-sql-database"></a>Exemples : Base de données SQL Azure

### <a name="e-create-a-shard-map-manager-external-data-source"></a>E. Créer une source de données externe partition carte manager
Pour créer une source de données externe pour faire référence à un SHARD_MAP_MANAGER, spécifiez le nom du serveur logique qui héberge le Gestionnaire de carte de partitions dans la base de données SQL Azure ou d’une base de données SQL Server sur une machine virtuelle Azure.

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL ElasticDBQueryCred  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc 
WITH (
    TYPE = SHARD_MAP_MANAGER,
    LOCATION = '<server_name>.database.windows.net',
    DATABASE_NAME = 'ElasticScaleStarterKit_ShardMapManagerDb',
    CREDENTIAL = ElasticDBQueryCred,
    SHARD_MAP_NAME = 'CustomerIDShardMap'
);
```

### <a name="f-create-an-rdbms-external-data-source"></a>F. Créer une source de données externe SGBDR
Pour créer une source de données externe pour faire référence à un système SGBDR, spécifie le nom du serveur logique de la base de données distante dans la base de données SQL Azure.

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL SQL_Credential  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc 
WITH (
    TYPE = RDBMS, 
    LOCATION = '<server_name>.database.windows.net', 
    DATABASE_NAME = 'Customers', 
    CREDENTIAL = SQL_Credential 
);
```

## <a name="examples-azure-sql-data-warehouse"></a>Exemples : L’entrepôt de données SQL Azure

### <a name="g-create-external-data-source-to-reference-azure-data-lake-store"></a>G. Créer la source de données externe en référence Azure Data Lake Store
Connectivité d’Azure Data lake Store est basée sur l’URI de votre ADLS et principal du service de votre Application Azure Active directory. Vous trouverez la documentation pour la création de cette application à[lake store l’authentification des données à l’aide d’Active Directory](https://docs.microsoft.com/en-us/azure/data-lake-store/data-lake-store-authenticate-using-active-directory).

```sql
-- If you do not have a Master Key on your DW you will need to create one.
CREATE MASTER KEY

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLUser 
WITH IDENTITY = '<clientID>@<OAuth2.0TokenEndPoint>',
SECRET = '<KEY>' ;


CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (TYPE = HADOOP,
      LOCATION = '<ADLS URI>'
)
```



## <a name="examples-parallel-data-warehouse"></a>Exemples : Parallel Data Warehouse

### <a name="h-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>H. Créer de source de données externe en référence Hadoop avec poussée vers le bas activée
Spécifiez l’option JOB_TRACKER_LOCATION pour activer la transmission des calculs à Hadoop des requêtes PolyBase. Une fois activé, PolyBase utilise une décision basée sur les coûts pour déterminer si le calcul de la requête doit-elle être envoyée à Hadoop ou toutes les données doivent être déplacées pour traiter la requête dans SQL Server. 

```sql
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    JOB_TRACKER_LOCATION = '10.10.10.10:8050'
);
```

### <a name="i-create-external-data-source-to-reference-azure-blob-storage"></a>I. Créer la source de données externe pour référencer le stockage d’objets blob Azure
EMPLACEMENT source source de données pour faire référence à votre conteneur de stockage d’objets blob Azure, spécifiez l’URI de stockage d’objets blob Azure en tant que les données externes pour créer un externe. Ajoutez votre clé de compte de stockage Azure au fichier de base-site.XML PDW pour l’authentification.

Dans cet exemple, la source de données externe est un conteneur de stockage d’objets blob Azure appelé dailylogs sous le compte de stockage Azure nommé mon compte. La source de données externe de stockage Azure est pour le transfert de données uniquement et ne prend pas en charge l’insertion d’un prédicat.

```sql
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
        TYPE = HADOOP, 
        LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'
);
```

## <a name="examples-bulk-operations"></a>Exemples : Les opérations en bloc   
### <a name="j-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage"></a>J. Créer une source de données externe pour les opérations en bloc la récupération des données à partir du stockage d’objets Blob Azure.   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].   
Utiliser la source de données suivants pour les opérations en bloc à l’aide de [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) ou [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md). Les informations d’identification utilisées, doivent être créés à l’aide de `SHARED ACCESS SIGNATURE` comme identité. Pour plus d’informations sur les signatures d’accès partagé, consultez [Utilisation des signatures d’accès partagé (SAP)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).   
```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoices
    WITH  (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net/week3',
        CREDENTIAL = AccessAzureInvoices
    );   
```   
Pour voir cet exemple en cours d’utilisation, consultez [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md).
  
## <a name="see-also"></a>Voir aussi
[MODIFIER la SOURCE de données externe (Transact-SQL)](../../t-sql/statements/alter-external-data-source-transact-sql.md)  
[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
[CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
[CREATE EXTERNAL TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
[CREATE TABLE AS SELECT &#40; Entrepôt de données SQL Azure &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
[Sys.external_data_sources (Transact-SQL)](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)  
  
  

