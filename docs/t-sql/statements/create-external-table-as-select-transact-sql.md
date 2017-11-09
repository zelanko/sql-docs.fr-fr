---
title: CREATE EXTERNAL TABLE AS SELECT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: 
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CREATE EXTERNAL TABLE AS SELECT
- CREATE_EXTERNAL_TABLE_AS_SELECT
- CREATE EXTERNAL TABLE AS SELECT_TSQL
helpviewer_keywords:
- External, table
- PolyBase, external table
- External, table create as select
- PolyBase, create table as select
ms.assetid: 32dfe254-6df7-4437-bfd6-ca7d37557b0a
caps.latest.revision: 16
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 716c0fdaa701865e8d35154cd19068051e0ab017
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-external-table-as-select-transact-sql"></a>CREATE EXTERNAL TABLE AS SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Crée une table externe, puis exporte vers, en parallèle, les résultats d’une [!INCLUDE[tsql](../../includes/tsql-md.md)] une instruction SELECT à Hadoop ou un objet Blob de stockage Azure.  
  
 Utilisez l’instruction CREATE externe TABLE AS sélectionnez (CETAS) :  
  
-   Exporter une table de base de données vers Hadoop ou Azure blob storage.  
  
-   Importer des données depuis Hadoop ou Azure blob storage et stockez-le dans la base de données.  
  
-   Interroger des données à partir de Hadoop ou Azure blob storage, joindre des tables relationnelles de base de données et réécrire les résultats dans Hadoop ou Azure blob storage.  
  
-   Interroger des données à partir de Hadoop ou Azure blob storage, transformer à l’aide des fonctions de traitement rapide de la base de données et écrire dans Hadoop ou Azure blob storage.  
  
 Pour plus d’informations, consultez [Prise en main de PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE EXTERNAL TABLE [ [database_name  . [ schema_name ] . ] | schema_name . ] table_name   
    WITH (   
        LOCATION = 'hdfs_folder',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
    AS <select_statement>  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
}  
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT <select_criteria>  
```  
  
## <a name="arguments"></a>Arguments  
 [[ *nom_base_de_données* . [ *schema_name* ]. ] | *nom_schéma* . ] *nom_table*  
 Un à trois - nom de partie de la table à créer dans la base de données. Pour une table externe, seules les métadonnées de la table sont stockée dans la base de données relationnelle.  
  
 EMPLACEMENT = '*hdfs_folder*'  
 Spécifie l’emplacement où écrire les résultats de l’instruction SELECT sur la source de données externe. L’emplacement est un nom de dossier et peut éventuellement inclure un chemin d’accès est relatif au dossier racine du Hadoop Cluster ou de l’objet Blob de stockage Azure.  PolyBase créera le chemin d’accès et le dossier s’il n’existe pas.  
  
 Les fichiers externes sont écrits dans *hdfs_folder* et nommée *QueryID_date_time_ID.format*, où *ID* est un identificateur incrémentiel et *format* est le format des données exportées. Par exemple, QID776_20160130_182739_0.orc.  
  
 DATA_SOURCE = *external_data_source_name*  
 Spécifie le nom de l’objet de source de données externe qui contient l’emplacement où les données externes sont stockées ou seront stockées. L’emplacement est un Hadoop Cluster ou un objet Blob de stockage Azure. Pour créer une source de données externe, utilisez [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 FILE_FORMAT = *external_file_format_name*  
 Spécifie le nom de l’objet de format de fichier externe qui contient le format du fichier de données externe. Pour créer un format de fichier externe, utilisez [CREATE EXTERNAL FILE FORMAT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
 Refuser des Options  
 Les options de rejet ne s’appliquent pas au moment de que l’exécution de cette instruction CREATE EXTERNAL TABLE AS SELECT. Au lieu de cela, elles sont spécifiées ici afin que la base de données peut les utiliser ultérieurement lorsqu’il importe des données à partir de la table externe. Plus tard, lorsque l’instruction CREATE TABLE AS SELECT sélectionne des données à partir de la table externe, la base de données utilisera les options de rejet pour déterminer le nombre ou le pourcentage de lignes importation avant d’arrêter l’importation peut échouer.  
  
 REJECT_VALUE = *reject_value*  
 Spécifie la valeur ou le pourcentage de lignes que l’importation avant de la base de données s’arrête à l’importation peut échouer.  
  
 REJECT_TYPE = **valeur** | pourcentage  
 Précise si l’option REJECT_VALUE est spécifiée comme une valeur littérale ou pourcentage.  
  
 valeur  
 REJECT_VALUE est une valeur littérale, pas un pourcentage.  La base de données s’arrête à l’importation des lignes à partir du fichier de données externe lorsque le nombre de lignes ayant échoué dépasse *reject_value*.  
  
 Par exemple, si REJECT_VALUE = 5 et REJECT_TYPE = valeur, la base de données s’arrête à l’importation de lignes après échec de 5 lignes à importer.  
  
 Pourcentage  
 REJECT_VALUE est un pourcentage, pas une valeur littérale. La base de données s’arrête à l’importation de lignes à partir d’externes du fichier de données lorsque la *pourcentage* de lignes ayant échoué dépasse *reject_value*. Le pourcentage de lignes ayant échoué est calculé à intervalles.  
  
 REJECT_SAMPLE_VALUE = *reject_sample_value*  
 Obligatoire lorsque REJECT_TYPE = percentage, spécifie le nombre de lignes à la tentative d’importation avant que la base de données recalcule le pourcentage de lignes qui ont échoué.  
  
 Par exemple, si REJECT_SAMPLE_VALUE = 1000, la base de données calcule le pourcentage de lignes qui ont échoué après qu’il a tenté d’importer les 1000 lignes du fichier de données externe. Si le pourcentage de lignes ayant échoué est inférieure à *reject_value*, la base de données tente de charger une autre 1000 lignes. La base de données se poursuit recalculer le pourcentage de lignes qui ont échoué après avoir tenté d’importer chaque 1000 lignes supplémentaires.  
  
> [!NOTE]  
>  Étant donné que la base de données calcule le pourcentage de lignes ayant échoué à intervalles, le pourcentage réel de lignes ayant échoué peut dépasser *reject_value*.  
  
 Exemple :  
  
 Cet exemple montre comment les trois options de rejet interagissent entre eux. Par exemple, si REJECT_TYPE = percentage, REJECT_VALUE = 30 et REJECT_SAMPLE_VALUE = 100, le scénario suivant peut se produire :  
  
-   La base de données tente de charger les 100 premières lignes ; 25 échouent et 75 réussisse.  
  
-   Pourcentage de lignes ayant échoué est calculée comme 25 %, ce qui est inférieur à la valeur de rejet de 30 %. Par conséquent, pas nécessaire d’arrêter la charge.  
  
-   La base de données tente de charger les 100 lignes ; Cette fois-ci 25 réussissent et échouent 75.  
  
-   Pourcentage de lignes ayant échoué est recalculé à 50 %. Le pourcentage de lignes ayant échoué a dépassé la valeur de rejet de 30 %.  
  
-   Le chargement échoue avec des lignes de 50 % a échoué après avoir essayé de charger les 200 lignes, qui est supérieur à la limite de 30 % spécifiée.  
  
 AVEC *common_table_expression*  
 Spécifie un jeu de résultats nommé temporaire, désigné par le terme d'expression de table commune (CTE, Common Table Expression). Pour plus d’informations, consultez [avec common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 Sélectionnez \<select_criteria > remplit la nouvelle table avec les résultats d’une instruction SELECT. *select_criteria* est le corps de l’instruction SELECT qui détermine les données à copier vers la nouvelle table. Pour plus d’informations sur les instructions SELECT, consultez [SELECT &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Pour exécuter cette commande le **utilisateur de base de données** a besoin de ces autorisations ou les appartenances tous :  
  
-   **ALTER SCHEMA** autorisation sur le schéma local qui contiendra la nouvelle table ou l’appartenance à la **db_ddladmin** rôle de base de données fixe.  
  
-   **CREATE TABLE** autorisation ou l’appartenance dans le **db_ddladmin** rôle de base de données fixe.  
  
-   **Sélectionnez** autorisation sur les objets référencés dans les *select_criteria*.  
  
 La connexion a besoin de toutes ces autorisations :  
  
-   **ADMINISTRER les opérations en bloc** autorisation  
  
-   **ALTER ANY EXTERNAL DATA SOURCE** autorisation  
  
-   **ALTER ANY EXTERNAL FILE FORMAT** autorisation  
  
-   La connexion doit avoir l’autorisation d’écriture pour lire et écrire dans le dossier externe sur le Hadoop Cluster ou d’un objet Blob de stockage Azure.  
 
 > [!IMPORTANT]  
 >  L’autorisation ALTER ANY EXTERNAL DATA SOURCE accorde à n’importe quel principal de la possibilité de créer et modifier n’importe quel objet de source de données externe, et par conséquent, elle autorise également la possibilité d’accéder à toutes les informations d’identification de base de données d’une étendue sur la base de données. Cette autorisation doit être considérée comme des privilèges très élevés et doit donc être accordé uniquement aux entités de confiance dans le système.
  
## <a name="error-handling"></a>Gestion des erreurs  
 Lorsque CREATE EXTERNAL TABLE AS SELECT exporte des données vers un fichier texte délimité, il n’existe aucun fichier de rejet pour les lignes qui ne parviennent pas à exporter.  
  
 Lorsque vous créez la table externe, la base de données tente de se connecter au cluster Hadoop externe ou de l’objet Blob de stockage Azure. Si la connexion échoue, la commande échoue et la table externe ne sera pas créée. Il peut prendre une minute ou plus pour la commande échoue, car les tentatives de la base de données la connexion au moins 3 fois.  
  
 Si CREATE EXTERNAL TABLE AS SELECT est annulée ou échoue, la base de données effectue une tentative de supprimer les nouveaux fichiers et des dossiers déjà créés sur la source de données externe à usage unique.  
  
 La base de données signale les erreurs de Java qui se produisent sur la source de données externes lors de l’exportation de données.  
  
##  <a name="GeneralRemarks"></a>Remarques d’ordre général  
 Une fois l’instruction CETAS terminée, vous pouvez exécuter [!INCLUDE[tsql](../../includes/tsql-md.md)] requêtes sur la table externe. Ces opérations seront importer des données dans la base de données pour la durée de la requête sauf si vous importez à l’aide de l’instruction CREATE TABLE AS SELECT.  
  
 Le nom de la table externe et de la définition sont stockés dans les métadonnées de la base de données. Les données sont stockées dans la source de données externe.  
  
 Les fichiers externes sont nommés *QueryID_date_time_ID.format*, où *ID* est un identificateur incrémentiel et *format* est le format des données exportées. Par exemple, QID776_20160130_182739_0.orc.  
  
 L’instruction CETAS toujours crée une table non partitionnée, même si la table source est partitionnée.  
  
 Pour les plans de requête, créé à expliquer, le databaseuses ces opérations de plan de requête pour les tables externes :  
  
-   Déplacement de lecture aléatoire externe  
  
-   Déplacement de diffusion externe  
  
-   Déplacement de la partition externe  
  
 **S’applique à :**[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]comme condition préalable pour la création d’une table externe, l’administrateur de l’application a besoin configurer la connectivité hadoop. Pour plus d’informations, consultez Configurer la connectivité à des données externes (système de plateforme Analytique) dans la documentation de points d’accès que vous pouvez télécharger à partir de [ici](http://www.microsoft.com/download/details.aspx?id=48241).  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Étant donné que les données de la table externe se trouvent en dehors de la base de données, sauvegarde et les opérations de restauration ne fonctionnent que sur les données stockées dans la base de données. Cela signifie que seules les métadonnées sont sauvegardées et restaurées.  
  
 La base de données ne vérifie pas la connexion à la source de données externe lorsque vous restaurez une sauvegarde de base de données qui contient une table externe. Si la source d’origine n’est pas accessible, la restauration de métadonnées de la table externe réussissent toujours, mais les opérations SELECT sur la table externe échoue.  
  
 La base de données ne garantit pas la cohérence des données entre la déterminées par les données externes. Vous, le client, êtes seul responsable pour maintenir la cohérence entre les données externes et la base de données.  
  
 Opérations Data manipulation language (DML) ne sont pas pris en charge sur les tables externes. Par exemple, vous ne pouvez pas utiliser le [!INCLUDE[tsql](../../includes/tsql-md.md)] mettre à jour, insérer ou supprimer [!INCLUDE[tsql](../../includes/tsql-md.md)]instructions pour modifier les données externes.  
  
 CREATE TABLE, DROP TABLE, CREATE STATISTICS, DROP STATISTICS, CREATE VIEW et DROP VIEW sont les opérations uniquement data definition language (DDL), autorisées sur des tables externes.  
  
 PolyBase peut consommer un maximum de fichiers de k 33 par dossier lors de l’exécution des requêtes PolyBase simultanées 32. Ce nombre maximal inclut les fichiers et sous-dossiers dans chaque dossier HDFS. Si le degré de concurrence est inférieure à 32, un utilisateur peut exécuter des requêtes PolyBase à des dossiers dans HDFS qui contiennent des fichiers de plus de 33 Ko. [!INCLUDE[msCoName](../../includes/msconame-md.md)]recommande aux utilisateurs de Hadoop et PolyBase conserver les chemins d’accès de fichier courts et utilisez pas plus de 30 fichiers Ko par dossier HDFS. Lorsque de trop de fichiers sont référencés, une exception d’insuffisance de mémoire JVM se produit.  
  
 [SET ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/statements/set-rowcount-transact-sql.md) n’a aucun effet sur ce CREATE EXTERNAL TABLE AS SELECT. Pour obtenir un comportement similaire, utilisez [TOP &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 Lorsque CREATE EXTERNAL TABLE AS SELECT sélectionne à partir d’un RCFile, les valeurs de colonne dans le RCFile ne doivent pas contenir le canal ' |' caractères.  
  
## <a name="locking"></a>Verrouillage  
 Acquiert un verrou partagé sur l’objet SCHEMARESOLUTION.  
  
##  <a name="Examples"></a> Exemples  
  
### <a name="a-create-a-hadoop-table-using-create-external-table-as-select-cetas"></a>A. Créer une table Hadoop à l’aide de CREATE externe TABLE AS sélectionnez (CETAS)  
 L’exemple suivant crée une nouvelle table externe nommée `hdfsCustomer`, à l’aide des définitions de colonne et les données de la table source `dimCustomer`.  
  
 La définition de table est stockée dans la base de données, et les résultats de l’instruction SELECT sont exportés vers le ' / pdwdata/customer.tbl' fichier sur la source de données externe Hadoop *customer_ds*. Le fichier est mis en forme selon le format de fichier externe *customer_ff*.  
  
 Le nom de fichier est généré par la base de données et contient l’ID de requête pour faciliter l’alignement de la requête qui a généré le fichier.  
  
 Le chemin d’accès `hdfs://xxx.xxx.xxx.xxx:5000/files/` précédant l’annuaire des clients doit déjà exister. Toutefois, si le répertoire client n’existe pas, la base de données créera le répertoire.  
  
> [!NOTE]  
>  Cet exemple spécifie de 5000. Si le port n’est pas spécifié, la base de données utilise 8020 en tant que le port par défaut.  
  
 Le Hadoop résultant emplacement et nom de fichier sera `hdfs:// xxx.xxx.xxx.xxx:5000/files/Customer/ QueryID_YearMonthDay_HourMinutesSeconds_FileIndex.txt.`.  
  
```  
  
      -- Example is based on AdventureWorks   
CREATE EXTERNAL TABLE hdfsCustomer  
WITH (  
        LOCATION='/pdwdata/customer.tbl',  
        DATA_SOURCE = customer_ds,  
        FILE_FORMAT = customer_ff  
) AS SELECT * FROM dimCustomer;  
```  
  
### <a name="b-use-a-query-hint-with-create-external-table-as-select-cetas"></a>B. Utilisez un indicateur de requête avec CREATE EXTERNAL TABLE AS sélectionnez (CETAS)  
 Cette requête affiche la syntaxe de base pour l’utilisation d’un indicateur de jointure de requête avec l’instruction CETAS. Une fois que la requête est soumise à que la base de données utilise la stratégie de jointure de hachage pour générer le plan de requête. Pour plus d’informations sur les indicateurs de jointure et l’utilisation de la clause OPTION, consultez [Clause OPTION &#40; Transact-SQL &#41; ](../../t-sql/queries/option-clause-transact-sql.md).  
  
> [!NOTE]  
>  Cet exemple spécifie de 5000. Si le port n’est pas spécifié, la base de données utilise 8020 en tant que le port par défaut.  
  
```  
  
      -- Example is based on AdventureWorks  
CREATE EXTERNAL TABLE dbo.FactInternetSalesNew  
WITH   
    (   
        LOCATION = '/files/Customer',  
        DATA_SOURCE = customer_ds,  
        FILE_FORMAT = customer_ff  
    )  
AS SELECT T1.* FROM dbo.FactInternetSales T1 JOIN dbo.DimCustomer T2  
ON ( T1.CustomerKey = T2.CustomerKey )  
OPTION ( HASH JOIN );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
 [CRÉER une TABLE &#40; Entrepôt de données SQL Azure, Parallel Data Warehouse &#41;](~/t-sql/statements/create-table-azure-sql-data-warehouse.md)   
 [CREATE TABLE AS SELECT &#40; Entrepôt de données SQL Azure &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  



