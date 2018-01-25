---
title: "CRÉER une TABLE externe (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 11/27/2017
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
- CREATE_EXTERNAL_TABLE
- CREATE EXTERNAL TABLE
- PolyBase, T-SQL
dev_langs: TSQL
helpviewer_keywords:
- External
- External, table create
- PolyBase, external table
ms.assetid: 6a6fd8fe-73f5-4639-9908-2279031abdec
caps.latest.revision: "30"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 97381b5381491b98c81a6863b3cfcdc6a340c79e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="create-external-table-transact-sql"></a>CRÉER une TABLE externe (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Crée une table externe PolyBase qui fait référence à des données stockées dans un cluster Hadoop ou le stockage d’objets blob Azure. Peut également être utilisé pour créer une table externe pour [requête de base de données élastique](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  
  
 Utilisez une table externe à :  
  
-   Interroger des données de stockage d’objets blob Hadoop ou Azure avec [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions.  
  
-   Importer et stocker les données d’Hadoop ou Azure stockage d’objets blob dans votre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.  
  
-   Créer une table externe pour une utilisation avec une base de données élastique  
     requête.  
     
- Importer et de stocker des données à partir d’Azure Data Lake Store dans Azure SQL Data Warehouse
  
 Voir aussi [créer une SOURCE de données externe &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) et [DROP TABLE externe &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-external-table-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  

```  
-- Syntax for SQL Server 
  
-- Create a new external table  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH (   
        LOCATION = 'folder_or_filepath',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
  
}  
  
-- Create a table for use with Elastic Database query  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH ( <sharded_external_table_options> )  
[;]  
  
<sharded_external_table_options> ::=  
        DATA_SOURCE = external_data_source_name,   
        SCHEMA_NAME = N'nonescaped_schema_name',  
        OBJECT_NAME = N'nonescaped_object_name',  
        [DISTRIBUTION  = SHARDED(sharding_column_name) | REPLICATED | ROUND_ROBIN]]  
    )  
[;]  
```  

```  
-- Syntax for Azure SQL Database
  
-- Create a table for use with Elastic Database query  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH ( <sharded_external_table_options> )  
[;]  
  
<sharded_external_table_options> ::=  
        DATA_SOURCE = external_data_source_name,   
        SCHEMA_NAME = N'nonescaped_schema_name',  
        OBJECT_NAME = N'nonescaped_object_name',  
        [DISTRIBUTION  = SHARDED(sharding_column_name) | REPLICATED | ROUND_ROBIN]]  
    )  
[;]  
```  


```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Create a new external table in SQL Server PDW  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH (   
        LOCATION = 'hdfs_folder_or_filepath',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
  
}  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name* . [nom_schéma]. | schema_name. ] *table_name*  
 Un à trois - nom de partie de la table à créer. Pour une table externe, seules les métadonnées de la table sont stockée dans SQL, ainsi que des statistiques de base sur le fichier et ou le dossier référencé dans Hadoop ou Azure blob storage. Aucune donnée réelle est déplacée ou est stockée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 \<column_definition > [,...  *n*  ] CREATE EXTERNAL TABLE autorise une ou plusieurs définitions de colonne. CREATE EXTERNAL TABLE et CREATE TABLE utilisent la même syntaxe de définition d’une colonne. Une exception à cela, vous ne pouvez pas utiliser la contrainte par défaut sur des tables externes. Pour plus d’informations sur les définitions de colonne et leurs types de données, consultez [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md) et [créer la TABLE de base de données SQL Azure](http://msdn.microsoft.com/library/d53c529a-1d5f-417f-9a77-64ccc6eddca1).  
  
 Les définitions de colonne, y compris les types de données et le nombre de colonnes doit correspondre les données dans les fichiers externes. S’il existe une incompatibilité, les lignes du fichier sont rejetées lors de l’interrogation des données réelles.  
  
 Pour les tables externes qui référencent des fichiers sources de données externes, les définitions de colonne et le type doivent mapper le schéma exact du fichier externe. Lors de la définition des types de données qui font référence aux données stockées dans Hadoop/Hive, utiliser les mappages suivants entre les types de données SQL et de la ruche et un cast du type en un type de données SQL lors de la sélection à partir de celui-ci. Les types incluent toutes les versions de la ruche, sauf indication contraire.

> [!NOTE]  
>  SQL Server ne prend pas en charge la ruche _infini_ valeur de données dans toute conversion. PolyBase échoue avec une erreur de conversion de type de données.


|Type de données SQL|Type de données .NET|Type de données Hive|Type de données Hadoop/Java|Commentaires|  
|-------------------|--------------------|--------------------|----------------------------|--------------|  
|tinyint|Byte|tinyint|ByteWritable|Pour les nombres non signés.|  
|smallint|Int16|smallint|ShortWritable||  
|int|Int32|int|IntWritable||  
|bigint|Int64|bigint|LongWritable||  
|bit|Booléen|boolean|BooleanWritable||  
|float|Double|double|DoubleWritable||  
|real|Unique|float|FloatWritable||  
|money|Décimal|double|DoubleWritable||  
|smallmoney|Décimal|double|DoubleWritable||  
|NCHAR|Chaîne<br /><br /> Char[]|chaîne|texte||  
|nvarchar|Chaîne<br /><br /> Char[]|chaîne|Texte||  
|char|Chaîne<br /><br /> Char[]|chaîne|Texte||  
|varchar|Chaîne<br /><br /> Char[]|chaîne|Texte||  
|binary|Byte[]|binary|BytesWritable|S’applique à la ruche 0,8 et versions ultérieur.|  
|varbinary|Byte[]|binary|BytesWritable|S’applique à la ruche 0,8 et versions ultérieur.|  
|date|DateTime|TIMESTAMP|TimestampWritable||  
|smalldatetime|DateTime|TIMESTAMP|TimestampWritable||  
|datetime2|DateTime|TIMESTAMP|TimestampWritable||  
|datetime|DateTime|TIMESTAMP|TimestampWritable||  
|time|TimeSpan|TIMESTAMP|TimestampWritable||  
|Décimal|Décimal|Décimal|BigDecimalWritable|S’applique à Hive0.11 et versions ultérieures.|  
  
 LOCATION =  '*folder_or_filepath*'  
 Spécifie le dossier ou le chemin d’accès et le nom de fichier pour les données réelles dans Hadoop ou Azure blob storage. L’emplacement démarre à partir du dossier racine ; le dossier racine est l’emplacement de données spécifié dans la source de données externe.  
  
 Si vous spécifiez l’emplacement à un dossier, une requête de PolyBase qui sélectionne à partir de la table externe récupérera les fichiers dans le dossier et tous ses sous-dossiers. Tout comme Hadoop, PolyBase ne retourne pas de dossiers cachés. Il ne retourne pas les fichiers dont le nom de fichier commence par un trait de soulignement (_) ou un point (.).  
  
 Dans cet exemple, si emplacement = '/ webdata /', une requête PolyBase retournera des lignes de mydata.txt et mydata2.txt.  Il ne retourne pas mydata3.txt, car il s’agit d’un sous-dossier d’un dossier masqué. Il ne retourne pas _hidden.txt, car il s’agit d’un fichier masqué.  
  
 ![Données récursives pour les tables externes](../../t-sql/statements/media/aps-polybase-folder-traversal.png "données récursives pour les tables externes")  
  
 Pour modifier la valeur par défaut et en lecture seule à partir du dossier racine, définissez l’attribut \<polybase.recursive.traversal > 'false' dans le fichier de configuration core-site.Xml. Ce fichier se trouve sous `<SqlBinRoot>\Polybase\Hadoop\Conf with SqlBinRoot the bin root of SQl Server`. Par exemple, `C:\\Program Files\\Microsoft SQL Server\\MSSQL13.XD14\\MSSQL\\Binn`.  
  
 DATA_SOURCE = *external_data_source_name*  
 Spécifie le nom de la source de données externe qui contient l’emplacement des données externes. Cet emplacement est soit un Hadoop ou Azure blob storage. Pour créer une source de données externe, utilisez [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 FILE_FORMAT = *external_file_format_name*  
 Spécifie le nom de l’objet de format de fichier externe qui stocke la méthode de compression et le type de fichier pour les données externes. Pour créer un format de fichier externe, utilisez [CREATE EXTERNAL FILE FORMAT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
 Refuser des Options  
 Vous pouvez spécifier les paramètres de refus qui déterminent la façon dont PolyBase traite *dirty* enregistre les récupère à partir de la source de données externe. Un enregistrement de données est considérée comme « dirty » si elle les types de données réelles ou le nombre de colonnes ne correspondent pas les définitions de colonne de la table externe.  
  
 Quand ne pas spécifier ou de modifier les valeurs de rejet, PolyBase utilise les valeurs par défaut. Ces informations sur les paramètres de rejet sont stockées en tant que métadonnées supplémentaires lorsque vous créez une table externe avec l’instruction CREATE EXTERNAL TABLE.   Lorsqu’une instruction SELECT ultérieure ou sélectionnez INTO SELECT sélectionne des données à partir de la table externe, PolyBase utilise les options de rejet pour déterminer le nombre ou le pourcentage de lignes peut être rejetée avant l’échec de la requête réelle. . La requête retournera les résultats (partielles) jusqu'à ce que le seuil de rejet est dépassé ; Ensuite, elle échoue avec le message d’erreur approprié.  
  
 REJECT_TYPE = **valeur** | pourcentage  
 Précise si l’option REJECT_VALUE est spécifiée comme une valeur littérale ou pourcentage.  
  
 valeur  
 REJECT_VALUE est une valeur littérale, pas un pourcentage. La requête de PolyBase échoue lorsque le nombre de lignes rejetées dépasse *reject_value*.  
  
 Par exemple, si REJECT_VALUE = 5 et REJECT_TYPE = valeur, la requête SELECT échoue après 5 lignes ont été rejetées de PolyBase.  
  
 Pourcentage  
 REJECT_VALUE est un pourcentage, pas une valeur littérale. Une requête PolyBase échoue lorsque le *pourcentage* de lignes ayant échoué dépasse *reject_value*. Le pourcentage de lignes ayant échoué est calculé à intervalles.  
  
 REJECT_VALUE = *reject_value*  
 Spécifie la valeur ou le pourcentage de lignes peut être rejetée avant l’échec de la requête.  
  
 Pour REJECT_TYPE = valeur, *reject_value* doit être un entier compris entre 0 et 2 147 483 647.  
  
 Pour REJECT_TYPE = percentage, *reject_value* doit être une valeur float comprise entre 0 et 100.  
  
 REJECT_SAMPLE_VALUE = *reject_sample_value*  
 Cet attribut est requis lorsque vous spécifiez REJECT_TYPE = pourcentage. Il détermine le nombre de lignes à la tentative de récupération avant que le PolyBase recalcule le pourcentage de lignes rejetées.  
  
 Le *reject_sample_value* paramètre doit être un entier compris entre 0 et 2 147 483 647.  
  
 Par exemple, si REJECT_SAMPLE_VALUE = 1000, PolyBase calcule le pourcentage de lignes qui ont échoué après qu’il a tenté d’importer les 1000 lignes du fichier de données externe. Si le pourcentage de lignes ayant échoué est inférieure à *reject_value*, PolyBase va tenter de récupérer un autre 1000 lignes. Il continue à recalculer le pourcentage de lignes qui ont échoué après avoir tenté d’importer chaque 1000 lignes supplémentaires.  
  
> [!NOTE]  
>  Étant donné que PolyBase calcule le pourcentage de lignes ayant échoué à intervalles, le pourcentage réel de lignes ayant échoué peut dépasser *reject_value*.  
  
 Exemple :  
  
 Cet exemple montre comment les trois options de rejet interagissent entre eux. Par exemple, si REJECT_TYPE = percentage, REJECT_VALUE = 30 et REJECT_SAMPLE_VALUE = 100, le scénario suivant peut se produire :  
  
-   PolyBase tente de récupérer les 100 premières lignes ; 25 échouent et 75 réussisse.  
  
-   Pourcentage de lignes ayant échoué est calculée comme 25 %, ce qui est inférieur à la valeur de rejet de 30 %. Par conséquent, PolyBase va continuer la récupération des données à partir de la source de données externe.  
  
-   PolyBase tente de charger les 100 lignes ; Cette fois-ci 25 réussissent et échouent 75.  
  
-   Pourcentage de lignes ayant échoué est recalculé à 50 %. Le pourcentage de lignes ayant échoué a dépassé la valeur de rejet de 30 %.  
  
-   La requête PolyBase échoue avec 50 % rejeté lignes après une tentative de retour les 200 premières lignes. Notez que les lignes correspondantes ont été retournées avant la requête PolyBase détecte que le seuil de rejet a été dépassé.  
  
 Options de table externe partitionnée  
 Spécifie la source de données externe (une source de données non SQL Server) et une méthode de distribution pour le [requête de base de données élastique](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  
  
 DATA_SOURCE  
 Une source de données externes telles que les données stockées dans un système de fichiers Hadoop, stockage d’objets blob Azure, ou un [Gestionnaire de carte de partitions](https://azure.microsoft.com/documentation/articles/sql-database-elastic-scale-shard-map-management/).  
  
 SCHEMA_NAME  
 La clause SCHEMA_NAME offre la possibilité de mapper la définition de table externe à une table dans un schéma différent sur la base de données distante. Cela permet de lever l’ambiguïté entre les schémas qui existent sur les bases de données locales et distantes.  
  
 OBJECT_NAME  
 La clause OBJECT_NAME offre la possibilité de mapper la définition de table externe à une table avec un nom différent sur la base de données distante. Cela permet de distinguer les noms des objets qui existent sur les bases de données locales et distantes.  
  
 DISTRIBUTION  
 Ce paramètre est facultatif. Cette option n’est obligatoire uniquement pour les bases de données de type SHARD_MAP_MANAGER. Ce paramètre contrôle si une table est traitée comme une table partitionnée ou d’une table répliquée. Avec **SHARDED** (*nom de la colonne*) des tables, les données de différentes tables ne se chevauchent pas. **RÉPLIQUÉES** Spécifie que les tables ont les mêmes données sur chaque partition. **ROUND_ROBIN** indique qu’une méthode spécifique à l’application est utilisée pour distribuer les données.  
  
## <a name="permissions"></a>Autorisations  
 Requiert les autorisations de l’utilisateur :  
  
-   **CREATE TABLE**  
  
-   **MODIFIER UN SCHÉMA**  
  
-   **MODIFIER N’IMPORTE QUELLE SOURCE DE DONNÉES EXTERNES**  
  
-   **MODIFIER N’IMPORTE QUEL FORMAT DE FICHIER EXTERNE**  

-   **BASE DE DONNÉES DE CONTRÔLE**
  
 Notez que la connexion qui crée la source de données externe doit être autorisé à les lire et écrire dans la source de données externe, située dans Hadoop ou Azure blob storage.  


 > [!IMPORTANT]  

>  L’autorisation ALTER ANY EXTERNAL DATA SOURCE accorde à n’importe quel principal de la possibilité de créer et modifier n’importe quel objet de source de données externe, et par conséquent, elle autorise également la possibilité d’accéder à toutes les informations d’identification de base de données d’une étendue sur la base de données. Cette autorisation doit être considérée comme des privilèges très élevés et doit donc être accordé uniquement aux entités de confiance dans le système.

## <a name="error-handling"></a>Gestion des erreurs  
 Lors de l’exécution de l’instruction CREATE EXTERNAL TABLE, PolyBase tente de se connecter à la source de données externe. Si la tentative de connexion échoue, l’instruction échoue et la table externe ne sera pas créée. Il peut prendre une minute ou plus pour la commande échoue, car PolyBase nouvelle tentative de connexion avant l’échec par la suite de la requête.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Dans les scénarios de requête ad hoc, par exemple, sélectionnez à partir de TABLE externe, PolyBase stocke les lignes extraites de la source de données externes dans une table temporaire. Une fois la requête terminée, PolyBase supprime et la table temporaire. Aucune données permanentes ne sont stockées dans des tables SQL.  
  
 En revanche, dans le scénario d’importation, par exemple, sélectionnez dans à partir de TABLE externe, PolyBase stocke les lignes extraites de la source de données externe en tant que données permanentes dans la table SQL. La nouvelle table est créée lors de l’exécution de requête lorsque Polybase récupère les données externes.  
  
 PolyBase peut transmettre des parmi le calcul de la requête à Hadoop pour améliorer les performances des requêtes. Il s’agit de la pile de prédicats. Pour ce faire, spécifiez l’option d’emplacement Hadoop resource manager dans [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 Vous pouvez créer de nombreuses tables externes qui référencent les sources de données externes identiques ou différents.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Dans la version CTP2, la fonctionnalité d’exportation n'est pas pris en charge, c'est-à-dire définitivement le stockage de données SQL dans la source de données externe. Cette fonctionnalité sera disponible dans CTP3.  
  
 Étant donné que les données pour une table externe se trouvent hors de l’application, il n’est pas sous le contrôle de PolyBase, modifié ou supprimé à tout moment par un processus externe. Pour cette raison, les résultats de requête par rapport à une table externe ne sont pas garantis pour être déterministes. La même requête peut retourner des résultats différents chaque fois qu’il s’exécute sur une table externe. De même, une requête peut échouer si les données externes sont supprimées ou déplacées.  
  
 Vous pouvez créer plusieurs tables externes que chaque référence à différentes sources externes. Toutefois, si vous exécutez simultanément des requêtes par rapport à différentes sources de données Hadoop, chaque source de Hadoop doit utiliser le même paramètre de configuration de serveur 'connectivité hadoop'. Par exemple, vous ne peut pas simultanément exécuter une requête par rapport à un cluster Hadoop des Cloudera et un cluster Hadoop de Hortonworks depuis ces utiliser différents paramètres de configuration. Pour les paramètres de configuration et les combinaisons prises en charge, consultez [Configuration de la connectivité PolyBase &#40; Transact-SQL &#41; ](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
  
 Uniquement ces instructions de langage de définition de données (DDL) sont autorisées sur des tables externes :  
  
-   CREATE TABLE et DROP TABLE  
  
-   CREATE STATISTICS et DROP STATISTICS  
Remarque : Créer et supprimer des statistiques sur les tables externes ne sont pas pris en charge dans la base de données SQL Azure. 
  
-   CREATE VIEW et DROP VIEW  
  
 Constructions et opérations non prises en charge :  
  
-   La contrainte par défaut sur les colonnes de table externe  
  
-   Opérations de Manipulation Language (DML) de données de delete, insert et update  
  
 Les limitations de requête :  
  
 PolyBase peut consommer un maximum de fichiers de k 33 par dossier lors de l’exécution des requêtes PolyBase simultanées 32. Ce nombre maximal inclut les fichiers et sous-dossiers dans chaque dossier HDFS. Si le degré de concurrence est inférieure à 32, un utilisateur peut exécuter des requêtes PolyBase à des dossiers dans HDFS qui contiennent des fichiers de plus de 33 Ko. Nous recommandons que vous conservez les chemins d’accès de fichier externe courts et pas plus de 30 fichiers Ko par dossier HDFS. Lorsque trop de fichiers sont référencés, une exception d’insuffisance de mémoire de Machine virtuelle Java (JVM) peut se produire.  

Limitations de la largeur de la table : PolyBase dans SQL Server 2016 a une limite de largeur de ligne de 32 Ko, basé sur la taille maximale d’une seule ligne valide à la définition de la table. Si la somme du schéma de la colonne est supérieure à 32 Ko, PolyBase ne sera pas en mesure d’interroger les données. 

Dans l’entrepôt de données SQL, cette limitation a été déclenchée à 1 Mo.


## <a name="locking"></a>Verrouillage  
 Partagé de verrou sur l’objet SCHEMARESOLUTION.  
  
## <a name="security"></a>Sécurité  
 Les fichiers de données pour une table externe est stocké dans Hadoop ou Azure blob storage. Ces fichiers de données sont créés et gérés par votre propre processus. Il vous incombe de gérer la sécurité des données externes.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-create-an-external-table-with-data-in-text-delimited-format"></a>A. Créer une table externe avec des données au format de texte délimité.  
 Cet exemple montre toutes les étapes requises pour créer une table externe qui a des données mises en forme dans les fichiers de texte délimité. Il définit la source de données externe *mydatasource* et un format de fichier externe *myfileformat*. Ces objets de niveau de base de données sont ensuite référencés dans l’instruction CREATE EXTERNAL TABLE. Pour plus d’informations, consultez [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) et [le FORMAT de fichier externe Créer &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT,   
    FORMAT_OPTIONS (FIELD_TERMINATOR ='|')  
);  
  
CREATE EXTERNAL TABLE ClickStream (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
        LOCATION='/webdata/employee.tbl',  
        DATA_SOURCE = mydatasource,  
        FILE_FORMAT = myfileformat  
    )  
;  
  
```  
  
### <a name="b-create-an-external-table-with-data-in-rcfile-format"></a>B. Créer une table externe des données au format de RCFile.  
 Cet exemple montre toutes les étapes requises pour créer une table externe qui comporte des données sous la forme RCFiles. Il définit la source de données externe *mydatasource_rc* et un format de fichier externe *myfileformat_rc*. Ces objets de niveau de base de données sont ensuite référencés dans l’instruction CREATE EXTERNAL TABLE. Pour plus d’informations, consultez [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) et [le FORMAT de fichier externe Créer &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource_rc  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat_rc  
WITH (  
    FORMAT = RCFILE,  
    SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
)  
;  
  
CREATE EXTERNAL TABLE ClickStream_rc (   
    url varchar(50),  
    event_date date,  
    user_ip varchar(50)  
)  
WITH (  
        LOCATION='/webdata/employee_rc.tbl',  
        DATA_SOURCE = mydatasource_rc,  
        FILE_FORMAT = myfileformat_rc  
    )  
;  
  
```  
  
### <a name="c-create-an-external-table-with-data-in-orc-format"></a>C. Créer une table externe des données au format ORC.  
 Cet exemple montre toutes les étapes requises pour créer une table externe qui a des données mises en forme en tant que fichiers ORC. Il définit un mydatasource_orc de source de données externe et un myfileformat_orc de format de fichier externe. Ces objets de niveau de base de données sont ensuite référencés dans l’instruction CREATE EXTERNAL TABLE. Pour plus d’informations, consultez [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md) et [le FORMAT de fichier externe Créer &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource_orc  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat_orc  
WITH (  
    FORMAT = ORC,  
    COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
)  
;  
  
CREATE EXTERNAL TABLE ClickStream_orc (   
    url varchar(50),  
    event_date date,  
    user_ip varchar(50)  
)  
WITH (  
        LOCATION='/webdata/',  
        DATA_SOURCE = mydatasource_orc,  
        FILE_FORMAT = myfileformat_orc  
    )  
;  
  
```  
  
### <a name="d-querying-hadoop-data"></a>D. Interrogation des données Hadoop  
 Parcours est une table externe qui se connecte au fichier texte délimité employee.tbl sur un cluster Hadoop. La requête suivante ressemble à une requête sur une table standard. Toutefois, cette requête extrait les données Hadoop et puis calcule le produit.  
  
```  
SELECT TOP 10 (url) FROM ClickStream WHERE user_ip = 'xxx.xxx.xxx.xxx'  
;  
```  
  
### <a name="e-join-hadoop-data-with-sql-data"></a>E. Joindre des données Hadoop avec les données SQL  
 Cette requête ressemble à une jointure standard sur deux tables SQL. La différence est que PolyBase extrait les données de parcours de Hadoop et puis le joint à la table UrlDescription. Une table est une table externe et l’autre est une table SQL standard.  
  
```  
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="f-import-data-from-hadoop-into-a-sql-table"></a>F. Importer des données depuis Hadoop dans une table SQL  
 Cet exemple crée une nouvelle table ms_user SQL qui stocke le résultat d’une jointure entre la table SQL standard de façon permanente *utilisateur* et la table externe *parcours*.  
  
```  
SELECT DISTINCT user.FirstName, user.LastName  
INTO ms_user  
FROM user INNER JOIN (  
    SELECT * FROM ClickStream WHERE cs.url = 'www.microsoft.com'  
    ) AS ms_user  
ON user.user_ip = ms.user_ip  
;  
  
```  
  
### <a name="g-create-an-external-table-for-a-sharded-data-source"></a>G. Créer une table externe pour une source de données partitionnée  
 Cet exemple Remappe une DMV à distance pour une table externe en utilisant les clauses nom_schéma et nom_objet.  
  
```  
CREATE EXTERNAL TABLE [dbo].[all_dm_exec_requests]([session_id] smallint NOT NULL,  
  [request_id] int NOT NULL,  
  [start_time] datetime NOT NULL,   
  [status] nvarchar(30) NOT NULL,  
  [command] nvarchar(32) NOT NULL,  
  [sql_handle] varbinary(64),  
  [statement_start_offset] int,  
  [statement_end_offset] int,  
  [cpu_time] int NOT NULL)  
WITH  
(  
  DATA_SOURCE = MyExtSrc,  
  SCHEMA_NAME = 'sys',  
  OBJECT_NAME = 'dm_exec_requests',  
  DISTRIBUTION=ROUND_ROBIN  
);   
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="h-importing-data-from-adls-into-azure-includessdwincludesssdw-mdmd"></a>H. Importation de données à partir de ADLS dans Azure[!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
 
  
```  

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLUser 
WITH IDENTITY = '<clientID>@\<OAuth2.0TokenEndPoint>',
SECRET = '<KEY>' ;


CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (TYPE = HADOOP,
      LOCATION = 'adl://pbasetr.azuredatalakestore.net'
)



CREATE EXTERNAL FILE FORMAT TextFileFormat 
WITH ( FORMATTYPE = DELIMITEDTEXT 
     , FORMATOPTIONS ( FIELDTERMINATOR = '|' 
                     , STRINGDELIMITER = '' 
                     , DATEFORMAT = 'yyyy-MM-dd HH:mm:ss.fff' 
                     , USETYPE_DEFAULT = FALSE 
                     ) 
    )


CREATE EXTERNAL TABLE [dbo].[DimProductexternal] 
( [ProductKey] [int] NOT NULL, 
  [ProductLabel] nvarchar NULL, 
  [ProductName] nvarchar NULL ) 
WITH ( LOCATION='/DimProduct/' , 
       DATA_SOURCE = AzureDataLakeStore , 
       FILE_FORMAT = TextFileFormat , 
       REJECT_TYPE = VALUE ,
       REJECT_VALUE = 0 ) ;


CREATE TABLE [dbo].[DimProduct] 
WITH (DISTRIBUTION = HASH([ProductKey] ) ) 
AS SELECT * FROM 
[dbo].[DimProduct_external] ; 
     
```  
  
### <a name="i-join-external-tables"></a>I. Joindre des tables externes  
  
```  
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="j-join-hdfs-data-with-pdw-data"></a>J. Joindre des données HDFS avec des données PDW  
  
```  
SELECT cs.user_ip FROM ClickStream cs  
JOIN User u ON cs.user_ip = u.user_ip  
WHERE cs.url = 'www.microsoft.com'  
;  
  
```  
  
### <a name="k-import-row-data-from-hdfs-into-a-distributed-pdw-table"></a>K. Importer des données de ligne à partir de HDFS dans une Table de PDW distribuée  
  
```  
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = HASH (url) )  
AS SELECT url, event_date, user_ip FROM ClickStream  
;  
```  
  
### <a name="l-import-row-data-from-hdfs-into-a-replicated-pdw-table"></a>L. Importer des données de ligne à partir de HDFS dans une Table répliquée de PDW  
  
```  
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = REPLICATE )  
AS SELECT url, event_date, user_ip   
FROM ClickStream  
;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requête de métadonnées courants (SQL Server PDW)](http://msdn.microsoft.com/en-us/733fc99b-b9f6-4a29-b085-a1bd4f09f2ed)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CREATE TABLE AS SELECT &#40; Entrepôt de données SQL Azure &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
  
  



