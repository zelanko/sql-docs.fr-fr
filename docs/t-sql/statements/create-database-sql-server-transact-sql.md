---
title: "CRÉER la base de données (SQL Server Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_TSQL
- DATABASE
- CONTAINMENT_TSQL
- CREATE DATABASE
- CREATE_DATABASE_TSQL
- CONTAINS_FILESTREAM_TSQL
- CONTAINS FILESTREAM
- CONTAINMENT
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server database snapshots], creating
- databases [SQL Server], creating
- model database [SQL Server], database creation
- mounted drives [SQL Server]
- CREATE DATABASE
- CREATE DATABASE statement
- file creation [SQL Server]
- creating databases
- containment
- filegroups [SQL Server], database creation
- database creation [SQL Server], CREATE DATABASE statement
- moving databases
- attaching databases [SQL Server], CREATE DATABASE...FOR ATTACH
ms.assetid: 29ddac46-7a0f-4151-bd94-75c1908c89f8
caps.latest.revision: 212
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: de8574d6d4f2322c63743828b7b8a03d4e6fa576
ms.contentlocale: fr-fr
ms.lasthandoff: 10/24/2017

---
# <a name="create-database-sql-server-transact-sql"></a>CREATE DATABASE (SQL Server Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée une nouvelle base de données ainsi que les fichiers utilisés pour stocker la base de données, un instantané de base de données, ou attache une base de données à partir des fichiers détachés d'une base de données créée antérieurement.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      Create a database  
CREATE DATABASE database_name   
[ CONTAINMENT = { NONE | PARTIAL } ]  
[ ON   
      [ PRIMARY ] <filespec> [ ,...n ]   
      [ , <filegroup> [ ,...n ] ]   
      [ LOG ON <filespec> [ ,...n ] ]   
]   
[ COLLATE collation_name ]  
[ WITH  <option> [,...n ] ]  
[;]  
  
<option> ::=  
{  
      FILESTREAM ( <filestream_option> [,...n ] )  
    | DEFAULT_FULLTEXT_LANGUAGE = { lcid | language_name | language_alias }  
    | DEFAULT_LANGUAGE = { lcid | language_name | language_alias }  
    | NESTED_TRIGGERS = { OFF | ON }  
    | TRANSFORM_NOISE_WORDS = { OFF | ON}  
    | TWO_DIGIT_YEAR_CUTOFF = <two_digit_year_cutoff>   
    | DB_CHAINING { OFF | ON }  
    | TRUSTWORTHY { OFF | ON }  
}  
  
<filestream_option> ::=  
{  
      NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL }  
    | DIRECTORY_NAME = 'directory_name'   
}  
  
<filespec> ::=   
{  
(  
    NAME = logical_file_name ,  
    FILENAME = { 'os_file_name' | 'filestream_path' }   
    [ , SIZE = size [ KB | MB | GB | TB ] ]   
    [ , MAXSIZE = { max_size [ KB | MB | GB | TB ] | UNLIMITED } ]   
    [ , FILEGROWTH = growth_increment [ KB | MB | GB | TB | % ] ]  
)  
}  
  
<filegroup> ::=   
{  
FILEGROUP filegroup name [ [ CONTAINS FILESTREAM ] [ DEFAULT ] | CONTAINS MEMORY_OPTIMIZED_DATA ]  
    <filespec> [ ,...n ]  
}  
  
<service_broker_option> ::=  
{  
    ENABLE_BROKER  
  | NEW_BROKER  
  | ERROR_BROKER_CONVERSATIONS  
}  
  
```  
  
```  
  
      Attach a database  
CREATE DATABASE database_name   
    ON <filespec> [ ,...n ]   
    FOR { { ATTACH [ WITH <attach_database_option> [ , ...n ] ] }  
        | ATTACH_REBUILD_LOG }  
[;]  
  
<attach_database_option> ::=  
{  
      <service_broker_option>  
    | RESTRICTED_USER  
    | FILESTREAM ( DIRECTORY_NAME = { 'directory_name' | NULL } )  
}  
  
```  
  
```  
  
      Create a database snapshot  
CREATE DATABASE database_snapshot_name   
    ON   
    (  
        NAME = logical_file_name,  
        FILENAME = 'os_file_name'   
    ) [ ,...n ]   
    AS SNAPSHOT OF source_database_name  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Est le nom de la base de données. Les noms de base de données doivent être uniques au sein d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et respecter les règles pour [identificateurs](../../relational-databases/databases/database-identifiers.md).  
  
 *database_name* peut être un maximum de 128 caractères, sauf si un nom logique n’est pas spécifié pour le fichier journal. Si un nom de fichier journal logique n’est pas spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère le *nom_fichier_logique* et *nom_fichier_se* pour le journal en ajoutant un suffixe à *nom_base_de_données*. Cela limite *nom_base_de_données* à 123 caractères de sorte que le nom de fichier logique généré n’est pas plus de 128 caractères.  
  
 Si le nom de fichier de données n’est pas spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise *nom_base_de_données* à la fois comme le *nom_fichier_logique* et en tant que le *nom_fichier_se*. Le chemin d'accès par défaut est obtenu à partir du Registre. Le chemin d’accès par défaut peut être modifié à l’aide de la **propriétés du serveur (Page Paramètres de base de données)** dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. La modification du chemin d'accès par défaut requiert le redémarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 CONTAINMENT = { NONE | PARTIAL }  

**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Spécifie l'état de la relation contenant-contenu de la base de données. NONE = base de données sans relation contenant-contenu. PARTIAL = Base de données à relation contenant-contenu partielle.  
  
 ON  
 Spécifie que les fichiers disque servant à stocker les parties données de la base de données (fichiers des données) sont définis de manière explicite. ON est requis lorsque le suivi d’une liste séparée par des virgules de \<filespec > des éléments qui définissent les fichiers de données pour le groupe de fichiers principal. La liste des fichiers dans le groupe de fichiers primaire peut être suivie d’une liste séparée par des virgules facultatif de \<groupe de fichiers > des éléments qui définissent des groupes de fichiers utilisateur et leurs fichiers.  
  
 PRIMARY  
 Spécifie que le texte associé \<filespec > liste définit le fichier primaire. Le premier fichier spécifié dans le \<filespec > entrée dans le groupe de fichiers primaire devient le fichier primaire. Une base de données peut avoir qu’un seul fichier primaire. Pour plus d'informations, consultez [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md).  
  
 Si vous ne précisez pas PRIMARY, le premier fichier spécifié dans l'instruction CREATE DATABASE devient le fichier primaire.  
  
 LOG ON  
 Spécifie que les fichiers disque servant à stocker le journal de la base de données (fichiers journaux) sont définis de manière explicite. LOG ON est suivi d’une liste séparée par des virgules de \<filespec > des éléments qui définissent les fichiers journaux. Si LOG ON n’est pas spécifié, un fichier journal est automatiquement créé, qui a une taille de 25 pour cent de la somme des tailles de tous les fichiers de données pour la base de données, ou 512 Ko, selon la plus grande. Ce fichier est placé à l'emplacement de fichier journal par défaut. Pour plus d’informations sur cet emplacement, consultez [afficher ou modifier les emplacements par défaut pour les données et fichiers journaux &#40; SQL Server Management Studio &#41; ](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md).  
  
 LOG ON ne peut pas être spécifié sur un instantané de base de données.  
  
 COLLATE *collation_name*  
 Indique le classement par défaut de la base de données. Le nom du classement peut être un nom de classement Windows ou SQL. S'il n'est pas spécifié, la base de données est affectée au classement par défaut de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un nom de classement ne peut pas être spécifié sur un instantané de base de données.  
  
 Un nom de classement ne peut pas être spécifié pour les clauses FOR ATTACH ou FOR ATTACH_REBUILD_LOG. Pour plus d’informations sur la façon de modifier le classement d’une base de données attachée, visitez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?linkid=16419&kbid=325335).  
  
 Pour plus d’informations sur les noms de classements Windows et SQL, consultez [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
> [!NOTE]  
>  Les bases de données à relation contenant-contenu sont classées différemment des bases de données sans relation contenant-contenu. Consultez [Contained Database Collations](../../relational-databases/databases/contained-database-collations.md) pour plus d’informations.  
  
 AVEC \<option >  
 -   **\<filestream_options >** 
  
     NON_TRANSACTED_ACCESS = { **OFF** | READ_ONLY | COMPLÈTE}  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
     Spécifie le niveau d'accès FILESTREAM non transactionnel à la base de données.  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |OFF|L'accès non transactionnel est désactivé.|  
    |READONLY|Les données FILESTREAM de cette base de données peuvent être lues par des processus non transactionnels.|  
    |FULL|L'accès non transactionnel complet aux FileTables FILESTREAM est activé.|  
  
     DIRECTORY_NAME = \<nom_répertoire > **s’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     Nom de répertoire compatible avec Windows. Ce nom doit être unique parmi tous les noms Database_Directory dans l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La comparaison d'unicité n'est pas sensible à la casse, indépendamment des paramètres de classement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette option doit être définie avant de créer un FileTable dans cette base de données.  
  
 Les options suivantes sont autorisées uniquement lorsque CONTAINMENT a été défini sur PARTIAL. Si CONTAINMENT est défini sur NONE, des erreurs se produiront.  
  
-   **DEFAULT_FULLTEXT_LANGUAGE = \<lcid > | \<nom de la langue > | \<alias de langue >**  
  
**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the default full-text language Server Configuration Option](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md) for a full description of this option.  
  
-   **DEFAULT_LANGUAGE = \<lcid > | \<nom de la langue > | \<alias de langue >**  
  
**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the default language Server Configuration Option](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) for a full description of this option.  
  
-   **NESTED_TRIGGERS = {OFF | ON}**  
  
**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the nested triggers Server Configuration Option](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md) for a full description of this option.  
  
-   **TRANSFORM_NOISE_WORDS = {OFF | ON}**  
  
**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)for a full description of this option.  
  
-   **TWO_DIGIT_YEAR_CUTOFF = {2049 | \<toute année comprise entre 1753 et 9999 >}**  
  
     Quatre chiffres qui représente une année. 2049 est la valeur par défaut. Consultez [configurer l’année à deux chiffres cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md) pour obtenir une description complète de cette option.  
  
-   **DB_CHAINING {OFF | ON}**  
  
     Si ON est spécifié, la base de données peut être la source ou la cible d'un chaînage des propriétés des bases de données croisées.  
  
     Lorsque OFF est spécifié, la base de données ne peut pas participer au chaînage des propriétés des bases de données croisées. La valeur par défaut est OFF.  
  
    > [!IMPORTANT]  
    >  L'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reconnaît ce paramètre lorsque l'option de serveur cross db ownership chaining a la valeur 0 (OFF). Lorsque cross db ownership chaining a la valeur 1 (ON), toutes les bases de données utilisateur peuvent participer aux chaînages des propriétés des bases de données croisées, quelle que soit la valeur de cette option. Cette option est définie à l’aide de [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
     Pour définir cette option, l'appartenance au rôle serveur fixe sysadmin est nécessaire. L’option DB_CHAINING ne peut pas être définie sur ces bases de données système : master, model et tempdb.  
  
-   **DIGNE DE CONFIANCE {OFF | ON}**  
  
     Si ON est spécifié, les modules de base de données (par exemple les vues, les fonctions définies par l'utilisateur ou les procédures stockées) utilisant le contexte d'emprunt d'identité peuvent accéder à des ressources en dehors de la base de données.  
  
     Lorsque OFF est spécifié, les modules de base de données dans le contexte d'emprunt d'identité ne peuvent pas accéder à des ressources en dehors de la base de données. La valeur par défaut est OFF.  
  
     TRUSTWORTHY prend la valeur OFF chaque fois que la base de données est attachée.  
  
     Par défaut, pour toutes les bases de données système, sauf pour la base msdb, l'option TRUSTWORTHY est définie à OFF (désactivé). La valeur ne peut pas être modifiée pour les bases de données model et tempdb. Nous vous recommandons de ne jamais définir l'option TRUSTWORTHY à ON (activé) pour la base de données master.  
  
     Pour définir cette option, l'appartenance au rôle serveur fixe sysadmin est nécessaire.  
  
 FOR ATTACH [WITH \< attach_database_option >] indique que la base de données est créé par [attachement](../../relational-databases/databases/database-detach-and-attach-sql-server.md) un ensemble existant de fichiers du système d’exploitation. Il doit y avoir un \<filespec > entrée qui spécifie le fichier primaire. Le seul autre \<filespec > entrées requises sont celles pour tous les fichiers qui ont un autre chemin d’accès à partir de la base de données lors de la première création ou dernière attachement. A \<filespec > entrée doit être spécifiée pour ces fichiers.  
  
 FOR ATTACH exige les conditions suivantes :  
  
-   Tous les fichiers de données (MDF et NDF) doivent être disponibles.  
  
-   Si plusieurs fichiers journaux existent, tous doivent être disponibles.  
  
 Si une base de données en lecture-écriture possède un seul fichier journal qui n'est pas disponible actuellement, et si la base de données a été fermée sans aucun utilisateur ou transaction ouverte avant l'opération d'attachement, FOR ATTACH reconstruit automatiquement le fichier journal et met à jour le fichier primaire. Par opposition, pour une base de données en lecture seule, le fichier journal ne peut pas être reconstruit car le fichier primaire ne peut pas être mis à jour. Par conséquent, lorsque vous attachez une base de données en lecture seule dont le fichier journal n'est pas disponible, vous devez fournir les fichiers journaux ou les fichiers pour la cause FOR ATTACH.  
  
> [!NOTE]  
>  Une base de données créée dans une version plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas être attachée à des versions antérieures.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tous les fichiers de texte intégral appartenant à la base de données qui est attachée seront attachés avec la base de données. Pour spécifier un nouveau chemin d'accès pour le catalogue de texte intégral, spécifiez le nouvel emplacement sans le nom de fichier du système d'exploitation en texte intégral. Pour plus d’informations, consultez la section Exemples.  
  
 Attachement d’une base de données qui contient une option FILESTREAM de « Nom de répertoire », dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance invitera [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vérifier que le nom Database_Directory est unique. Si elle n’est pas le cas, l’opération d’attachement échoue avec l’erreur, « FILESTREAM Database_Directory name \<nom > n’est pas unique dans cette instance SQL Server ». Pour éviter cette erreur, le paramètre facultatif, *directory_name*, doit être passé à cette opération.  
  
 FOR ATTACH ne peut pas être spécifié sur un instantané de base de données.  
  
 FOR ATTACH peut spécifier l'option RESTRICTED_USER. RESTRICTED_USER permet uniquement aux membres du rôle de base de données fixe db_owner et aux rôles serveurs fixes dbcreator et sysadmin de se connecter à la base de données, mais il n'en limite pas le nombre. Les tentatives par des utilisateurs non qualifiés sont refusées.  
  
 Si la base de données utilise [!INCLUDE[ssSB](../../includes/sssb-md.md)], utilisez WITH \<service_broker_option > dans votre clause FOR ATTACH : 
  
 \<service_broker_option > contrôles [!INCLUDE[ssSB](../../includes/sssb-md.md)] remise de messages et le [!INCLUDE[ssSB](../../includes/sssb-md.md)] identificateur de la base de données. Les options [!INCLUDE[ssSB](../../includes/sssb-md.md)] peuvent être spécifiées uniquement quand la clause FOR ATTACH est utilisée.  
  
 ENABLE_BROKER  
 Spécifie que [!INCLUDE[ssSB](../../includes/sssb-md.md)] est activé pour la base de données spécifiée. Autrement dit, la remise de message est démarrée et is_broker_enabled a la valeur true dans l’affichage catalogue sys.databases. La base de données conserve l'identificateur [!INCLUDE[ssSB](../../includes/sssb-md.md)] existant.  
  
 NEW_BROKER  
 Crée une nouvelle valeur service_broker_guid dans sys.databases et les bases restaurées, et termine tous les points de terminaison de conversation avec un nettoyage. Service Broker est activé, mais aucun message n'est envoyé aux points de terminaison de conversation distants. Tout itinéraire qui fait référence à l'ancien identificateur [!INCLUDE[ssSB](../../includes/sssb-md.md)] doit être recréé avec le nouvel identificateur.  
  
 ERROR_BROKER_CONVERSATIONS  
 Termine toutes les conversations avec une erreur indiquant que la base de données est attachée ou restaurée. Service Broker est désactivé jusqu'à la fin de l'opération, puis il est activé. La base de données conserve l'identificateur [!INCLUDE[ssSB](../../includes/sssb-md.md)] existant.  
  
 Lorsque vous attachez une base de données répliquée qui a été copiée au lieu d'être détachée, tenez compte des conditions suivantes :  
  
-   Si vous attachez la base de données à la même version et à la même instance de serveur que celles de la base de données d'origine, aucune opération supplémentaire n'est nécessaire.  
  
-   Si vous attachez la base de données à la même instance de serveur, mais avec une version mise à niveau, vous devez exécuter [sp_vupgrade_replication](../../relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql.md) pour mettre à niveau de la réplication après l’opération d’attachement est terminée.  
  
-   Si vous attachez la base de données à une autre instance de serveur, quelle que soit la version, vous devez exécuter [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) pour supprimer la réplication une fois l’opération d’attachement terminée.  
  
> [!NOTE]  
>  Attachement fonctionne avec la **vardecimal** le format de stockage, mais la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] doit être mis à niveau au moins [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2. Vous ne pouvez pas attacher une base de données à l'aide du format de stockage vardecimal à une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la **vardecimal** le format de stockage, consultez [la Compression des données](../../relational-databases/data-compression/data-compression.md).  
  
 Lorsqu'une base de données est attachée ou restaurée pour la première fois à une nouvelle instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une copie de la clé principale de la base de données (chiffrée par la clé principale du service) n'est pas encore stockée sur le serveur. Vous devez utiliser l’instruction **OPEN MASTER KEY** pour déchiffrer la clé principale de la base de données. Une fois la clé principale de la base de données déchiffrée, vous avez la possibilité d’activer le déchiffrement automatique dans le futur en exécutant l’instruction **ALTER MASTER KEY REGENERATE** pour fournir au serveur une copie de la clé principale de la base de données chiffrée avec la clé principale du service. Lorsqu'une base de données a été mise à niveau à partir d'une version antérieure, la clé DMK doit être régénérée de façon à utiliser le nouvel algorithme AES. Pour plus d’informations sur la régénération de la clé DMK, consultez [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md). La durée nécessaire pour régénérer la clé DMK à mettre à niveau vers AES dépend du nombre d'objets protégés par la clé DMK. La régénération de la clé DMK à mettre à niveau vers AES est nécessaire une seule fois et n'a aucune incidence sur les régénérations ultérieures effectuées dans le cadre d'une stratégie de rotation de clés. Pour plus d’informations sur la mise à niveau une base de données à l’aide de liaison, consultez [mettre à niveau une base de données à l’aide d’attacher et détacher &#40; Transact-SQL &#41; ](../../relational-databases/databases/upgrade-a-database-using-detach-and-attach-transact-sql.md).  
  
 **Note de sécurité** nous vous recommandons de ne pas joindre les bases de données à partir de sources inconnues ou non approuvées. Ces bases de données peuvent contenir du code malveillant susceptible d'exécuter du code [!INCLUDE[tsql](../../includes/tsql-md.md)] indésirable ou de provoquer des erreurs en modifiant le schéma ou la structure physique des bases de données. Avant d’utiliser une base de données à partir d’une source inconnue ou non approuvée, exécutez [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) sur la base de données sur un serveur de production et examinez également le code, notamment les procédures stockées ou autre code défini par l’utilisateur, dans la base de données.  
  
> [!NOTE]  
>  Le **TRUSTWORTHY** et **DB_CHAINING** options n’ont aucun effet lors de l’attachement d’une base de données.  
  
 FOR ATTACH_REBUILD_LOG  
 Spécifie que la base de données est créée en joignant un ensemble existant de fichiers du système d'exploitation. Cette option est limitée aux bases de données en lecture/écriture. Il doit y avoir un  *\<filespec >* entrée spécifiant le fichier primaire. S'il manque un ou plusieurs fichiers du journal des transactions, le fichier journal est reconstruit. ATTACH_REBUILD_LOG crée automatiquement un fichier journal 1 Mo. Ce fichier est placé à l'emplacement de fichier journal par défaut. Pour plus d’informations sur cet emplacement, consultez [afficher ou modifier les emplacements par défaut pour les données et fichiers journaux &#40; SQL Server Management Studio &#41; ](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md).  
  
> [!NOTE]  
>  Si les fichiers journaux sont disponibles, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilise ces fichiers au lieu de reconstruire les fichiers journaux.  
  
 FOR ATTACH_REBUILD_LOG requiert ce qui suit :  
  
-   Un arrêt propre de la base de données.  
  
-   Tous les fichiers de données (MDF et NDF) doivent être disponibles.  
  
> [!IMPORTANT]  
>  Cette opération brise la chaîne de sauvegarde du journal. Nous recommandons d'effectuer une sauvegarde complète avant de réaliser cette opération. Pour plus d’informations, consultez [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).  
  
 Généralement, FOR ATTACH_REBUILD_LOG est utilisé lorsque vous copiez une base de données en lecture/écriture avec un grand journal vers un autre serveur où la copie sera principalement, ou uniquement, utilisée pour des opérations de lecture, et nécessite donc moins d'espace de journal que la base de données d'origine.  
  
 FOR ATTACH_REBUILD_LOG ne peut pas être spécifié sur un instantané de base de données.  
  
 Pour plus d’informations sur l’attachement et détachement des bases de données, consultez [de base de données attacher et détacher &#40; SQL Server &#41; ](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
 \<filespec >  
 Contrôle les propriétés des fichiers.  
  
 NOM *nom_fichier_logique*  
 Spécifie le nom logique du fichier. NAME est requis lorsque FILENAME est spécifié, sauf lors de la spécification d'une des clauses FOR ATTACH. Un groupe de fichiers FILESTREAM ne peut pas être nommé PRIMARY.  
  
 *nom_fichier_logique*  
 Nom logique utilisé pour référencer le fichier dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Nom_fichier_logique* doit être unique dans la base de données et respecter les règles pour [identificateurs](../../relational-databases/databases/database-identifiers.md). Le nom peut être une constante de type caractère ou Unicode, un identificateur régulier ou un identificateur délimité.  
  
 Nom de fichier { **'***nom_fichier_se***'** | **'***filestream_path***'** }  
 Spécifie un nom de fichier du système d'exploitation (physique).  
  
 **'** *nom_fichier_se* **'**  
 Chemin d'accès et nom de fichier utilisé par le système d'exploitation lorsque vous créez le fichier. Le fichier doit résider sur l'un des périphériques suivants : le serveur local sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé, un réseau de zone de stockage [réseau SAN] ou un réseau basé sur iSCSI. Le chemin d'accès spécifié doit exister avant l'exécution de l'instruction CREATE DATABASE. Pour plus d'informations, consultez le paragraphe « Groupes de fichiers et fichiers de base de données » dans la section Notes.  
  
 Les paramètres SIZE, MAXSIZE et FILEGROWTH peuvent être définis lorsqu'un chemin d'accès UNC est spécifié pour le fichier.  
  
 Si le fichier se trouve sur une partition brute, *nom_fichier_se* doit spécifier uniquement la lettre de lecteur d’une partition brute existante. Un seul fichier de données peut être créé sur chaque partition brute.  
  
 Les fichiers de données ne doivent pas être placés sur des systèmes de fichiers compressés, sauf si les fichiers sont des fichiers secondaires en lecture seule ou si la base de données est en en lecture seule. Les fichiers journaux ne doivent jamais être placés sur des systèmes de fichiers compressés.  
  
 **'** *filestream_path* **'**  
 Pour un groupe de fichiers FILESTREAM, FILENAME fait référence à un chemin d'accès où les données FILESTREAM seront stockées. Le chemin d'accès jusqu'au dernier dossier doit exister, et le dernier dossier ne doit pas exister. Par exemple, si vous spécifiez le chemin d'accès C:\MyFiles\MyFilestreamData, C:\MyFiles doit exister avant l'exécution d'ALTER DATABASE, mais le dossier MyFilestreamData ne doit pas exister.  
  
 Le groupe de fichiers et le fichier (`<filespec>`) doivent être créés dans la même instruction.  
  
 Les propriétés SIZE et FILEGROWTH ne s'appliquent pas à un groupe de fichiers FILESTREAM.  
  
 TAILLE *taille*  
 Précise la taille du fichier.  
  
 TAILLE ne peut pas être spécifié quand le *nom_fichier_se* est spécifié comme un chemin d’accès UNC. SIZE ne s'applique pas à un groupe de fichiers FILESTREAM.  
  
 *taille*  
 Taille initiale du fichier.  
  
 Lorsque *taille* n’est pas fourni pour le fichier primaire, la [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilise la taille du fichier primaire de la base de données model. La taille par défaut du modèle est de 8 Mo (commençant par [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) ou 1 Mo (pour les versions antérieures). Lorsqu’un fichier journal ou un fichier de données secondaire est spécifié, mais *taille* n’est pas spécifié pour le fichier, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] rend le fichier de 8 Mo (commençant par [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) ou 1 Mo (pour les versions antérieures). La taille spécifiée pour le fichier primaire doit être au moins égale à la taille du fichier primaire de la base de données model.  
  
 Les suffixes kilo-octet (Ko), mégaoctet (Mo), gigaoctet (Go) ou téraoctet (To) peuvent être utilisés. La valeur par défaut est Mo. Indiquez un nombre entier sans aucune décimale. *Taille* est une valeur entière. Pour les valeurs supérieures à 2147483647, utilisez des unités plus grandes.  
  
 MAXSIZE *max_size*  
 Spécifie la taille maximale que peut atteindre le fichier. MAXSIZE ne peut pas être spécifié quand le *nom_fichier_se* est spécifié comme un chemin d’accès UNC.  
  
 *max_size*  
 Est la taille de fichier maximale. Les indications Ko, Mo, Go et To peuvent être utilisées. La valeur par défaut est Mo. Indiquez un nombre entier sans aucune décimale. Si *max_size* n’est pas spécifié, le fichier augmente jusqu'à ce que le disque est plein. *Max_size* est une valeur entière. Pour les valeurs supérieures à 2147483647, utilisez des unités plus grandes.  
  
 UNLIMITED  
 Précise que la taille du fichier peut croître jusqu'à ce que le disque soit saturé. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un fichier journal spécifié avec une croissance illimitée a une taille maximale de 2 To et un fichier de données une taille maximale de 16 To.  
  
> [!NOTE]  
>  Aucune taille maximale n'est définie lorsque cette option est spécifiée pour un conteneur FILESTREAM. Il continue à grandir jusqu'à ce que le disque soit saturé.  
  
 FILEGROWTH *growth_increment*  
 Spécifie l'incrément de croissance automatique du fichier. Le paramètre FILEGROWTH d'un fichier ne peut dépasser le paramètre MAXSIZE. FILEGROWTH ne peut pas être spécifié quand le *nom_fichier_se* est spécifié comme un chemin d’accès UNC. FILEGROWTH ne s'applique pas à un groupe de fichiers FILESTREAM.  
  
 *growth_increment*  
 Représente la quantité d’espace ajoutée au fichier chaque fois qu’un espace supplémentaire est requis.  
  
 La valeur peut être exprimée en Mo, Ko, Go, To ou pourcentage (%). Si un nombre est mentionné sans spécifier Mo, Ko ou %, la valeur par défaut est Mo. Lorsque % est spécifié, la taille de l'incrément de croissance est le pourcentage choisi de la taille du fichier au moment où l'incrémentation a lieu. La taille spécifiée est arrondie aux 64 Ko plus proche, et la valeur minimale est de 64 Ko.  
  
 La valeur 0 indique que la croissance automatique est désactivée et qu'aucun espace supplémentaire n'est autorisé.  
  
 Si la croissance du fichier n’est pas spécifié, les valeurs par défaut sont :  
  
|Version|Valeurs par défaut|  
|-------------|--------------------|  
|Début[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|Données de 64 Mo. Les fichiers journaux 64 Mo.|  
|Début[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Données de 1 Mo. Fichiers journaux de 10 %.|  
|Versions antérieures à[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Données de 10 %. Fichiers journaux de 10 %.|  
  
 \<groupe de fichiers >  
 Contrôle les propriétés des groupes de fichiers. Filegroup ne peut pas être spécifié sur un instantané de base de données.  
  
 Groupe de fichiers *filegroup_name*  
 Nom logique du groupe de fichiers.  
  
 *FILEGROUP_NAME*  
 *FILEGROUP_NAME* doit être unique dans la base de données et ne peut pas être les fournie par le système noms PRIMARY et PRIMARY_LOG. Le nom peut être une constante de type caractère ou Unicode, un identificateur régulier ou un identificateur délimité. Le nom doit respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md).  
  
 CONTAINS FILESTREAM  
 Spécifie que le groupe de fichiers stocke des objets BLOB (binary large objects) FILESTREAM dans le système de fichiers.  
  
 CONTAINS MEMORY_OPTIMIZED_DATA  

**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Spécifie que le groupe de fichiers stocke des données optimisées en mémoire dans le système de fichiers. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md). Un seul groupe de fichiers MEMORY_OPTIMIZED_DATA est autorisé par base de données. Pour obtenir des exemples de code que vous créez un groupe de fichiers pour stocker les données mémoire optimisé, consultez [création d’une Table optimisée en mémoire et une en mode natif procédure stockée compilée](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).  
  
 DEFAULT  
 Spécifie le groupe de fichiers nommé qui est le groupe de fichiers par défaut de la base de données.  
  
 *nom_instantané_base_de_données*  
 Nom du nouvel instantané de base de données. Les noms des instantanés de bases de données doivent être uniques au sein d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et respecter les règles applicables aux identificateurs. *nom_instantané_base_de_données* peut comporter un maximum de 128 caractères.  
  
 ON **(** nom  **=**  *nom_fichier_logique***,** nom de fichier **='***nom_fichier_se***')** [ **,**... *n* ]  
 Pour créer un instantané de base de données, spécifie une liste de fichiers dans la base de données source. Pour que l'instantané fonctionne, tous les fichiers de données doivent être spécifiés individuellement. Cependant, les fichiers journaux ne sont pas autorisés pour les instantanés de base de données. Les groupes de fichiers FILESTREAM ne sont pas pris en charge par les instantanés de base de données. Si un fichier de données FILESTREAM est inclus dans une clause CREATE DATABASE ON, l'instruction échoue et une erreur est levée.  
  
 Pour obtenir une description des NAME et FILENAME et leurs valeurs, consultez les descriptions de l’équivalent \<filespec > valeurs.  
  
> [!NOTE]  
>  Lorsque vous créez un instantané de base de données, l’autre \<filespec > options et le mot clé PRIMARY ne sont pas autorisées.  
  
 AS SNAPSHOT OF *nom_base_de_données_source*  
 Spécifie que la base de données en cours de création est un instantané de base de données de la base de données source spécifiée par *nom_base_de_données_source*. Les bases de données d'instantané et source doivent se trouver sur la même instance.  
  
 Pour plus d'informations, consultez le paragraphe « Instantanés de base de données » dans la section Remarques.  
  
## <a name="remarks"></a>Notes  
 Le [base de données master](../../relational-databases/databases/master-database.md) doit être sauvegardée chaque fois qu’une base de données utilisateur est créé, modifié ou supprimé.  
  
 L'instruction CREATE DATABASE doit être exécutée en mode de validation automatique (mode de gestion des transactions par défaut) et n'est pas autorisée dans une transaction explicite ou implicite.  
  
 Vous pouvez utiliser une instruction CREATE DATABASE pour créer une base de données et les fichiers qui stockent la base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implémente l'instruction CREATE DATABASE à l'aide des étapes suivantes :  
  
1.  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise une copie de la [base de données model](../../relational-databases/databases/model-database.md) pour initialiser la base de données et ses métadonnées.  
  
2.  Un GUID Service Broker est affecté à la base de données.  
  
3.  Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] complète ensuite le reste de la base de données avec des pages vides, à l'exception des pages qui contiennent des données internes enregistrant la manière dont est utilisé l'espace dans la base de données.  
  
 Vous pouvez spécifier un maximum de 32 767 bases de données sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Chaque base de données appartient à un propriétaire qui peut réaliser des activités spéciales dans la base de données. Le propriétaire est l'utilisateur qui crée la base de données. Le propriétaire de la base de données peut être modifié à l’aide de [sp_changedbowner](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md).  

Certaines fonctionnalités de base de données dépendent de fonctionnalités ou les fonctionnalités présentent dans le système de fichiers pour les fonctionnalités complètes de base de données. Voici quelques exemples des fonctionnalités qui dépendent de jeu de fonctionnalités de système de fichiers :
- DBCC CHECKDB
- FileStream
- Sauvegardes en ligne à l’aide d’instantanés VSS et le fichier
- Création d’instantanés de base de données
- Le groupe de fichiers mémoire optimisé de données
   
## <a name="database-files-and-filegroups"></a>Groupes de fichiers et fichiers de base de données  
 Chaque base de données comporte au moins deux fichiers, un *fichier primaire* et un *fichier journal des transactions*et au moins un groupe de fichiers. Un maximum de 32 767 fichiers et 32 767 groupes de fichiers peut être spécifié pour chaque base de données.  
  
 Lorsque vous créez une base de données, vérifiez les fichiers de données aussi grand que possible en fonction de la quantité maximale de données attendues dans la base de données  
  
 Nous vous recommandons d'utiliser un réseau de zone de stockage (SAN, Storage Area Network), un réseau basé sur iSCSI ou un disque attaché localement pour le stockage de vos fichiers de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], car cette configuration optimise les performances et la fiabilité de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="database-snapshots"></a>Instantanés de base de données  
 Vous pouvez utiliser l’instruction CREATE DATABASE pour créer une vue en lecture seule, statique, un *instantané de base de données* de la *base de données source*. Chaque instantané de base de données est transactionnellement cohérent avec la base de données source existante au moment de la création de l'instantané. Une base de données source peut posséder plusieurs instantanés.  
  
> [!NOTE]  
>  Lorsque vous créez un instantané de base de données, l'instruction CREATE DATABASE ne peut pas faire référence à des fichiers journaux, hors connexion, de restauration ou anciens.  
  
 Si la création d'un instantané de base de données échoue, l'instantané devient suspect et doit être supprimé. Pour plus d’informations, consultez [DROP DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-database-transact-sql.md).  
  
 Chaque instantané est conservé jusqu'à ce qu'il soit supprimé par DROP DATABASE.  
  
 Pour plus d’informations, consultez [Instantanés de base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
## <a name="database-options"></a>Options de base de données  
 Plusieurs options de base de données sont définies automatiquement chaque fois que vous créez une base de données. Pour obtenir la liste de ces options, consultez [Options ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="the-model-database-and-creating-new-databases"></a>Base de données model et création de nouvelles bases de données  
 Tous les objets définis par l’utilisateur dans le [base de données model](../../relational-databases/databases/model-database.md) sont copiés dans toutes les bases de données nouvellement créés. Vous pouvez ajouter dans la base de données model tous les objets, tels que tables, vues, procédures stockées ou types de données, à inclure dans toutes les bases de données nouvellement créées.  
  
 Lorsqu’une base de données créer *nom_base_de_données* instruction est spécifié sans paramètre de taille supplémentaire, le fichier de données principal est la même taille que le fichier primaire dans la base de données model.  
  
 Sauf si FOR ATTACH est spécifié, chaque nouvelle base de données hérite des paramètres d'option de base de données de la base de données model. Par exemple, l’option de réduction automatique de base de données a la valeur **true** dans le modèle et dans toutes les nouvelles bases de données que vous créez. Si vous modifiez les options de la base de données model, ces nouveaux paramètres d'options sont valables pour toutes les nouvelles bases de données que vous créez. Les opérations de modification dans la base de données model n'affectent pas les bases de données existantes. Si vous avez précisé FOR ATTACH dans l'instruction CREATE DATABASE, la nouvelle base de données héritera des paramètres d'option de la base de données originale.  
  
## <a name="viewing-database-information"></a>Affichage des informations de bases de données  
 Vous pouvez utiliser les affichages catalogue, les fonctions système et les procédures stockées du système pour retourner des informations sur les bases de données, les fichiers et les groupes de fichiers. Pour plus d’informations, consultez [Vues système &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90).  
  
## <a name="permissions"></a>Permissions  
 L'autorisation CREATE DATABASE, CREATE ANY DATABASE ou ALTER ANY DATABASE est obligatoire.  
  
 Pour garder le contrôle de l'utilisation du disque sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'autorisation de création de bases de données est généralement limitée à quelques comptes de connexion.  
  
 L'exemple suivant fournit l'autorisation de créer une base de données à l'utilisateur de base de données Fay.  
  
```  
USE master;  
GO  
GRANT CREATE DATABASE TO [Fay];  
GO  
```  
  
### <a name="permissions-on-data-and-log-files"></a>Autorisations sur les données et les journaux  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], certaines autorisations sont définies sur les données et les journaux de chaque base de données. Les autorisations suivantes sont définies chaque fois que les opérations suivantes sont appliquées à une base de données :  
  
|||  
|-|-|  
|Créé le|Modifiée pour ajouter un nouveau fichier|  
|Attachée|Sauvegardée|  
|Détachée|Restaurée|  
  
 Les autorisations empêchent les fichiers d'être accidentellement falsifiés s'ils résident dans un répertoire doté d'autorisations d'ouverture.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] ne définit pas d'autorisations sur les fichiers de données et les journaux.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-database-without-specifying-files"></a>A. Création d'une base de données sans spécifier de fichiers  
 Cet exemple crée une base de données appelée `mytest` et crée un fichier primaire et un fichier de journal des transactions correspondants. Étant donné que l’instruction n’a aucun \<filespec >, le fichier de base de données primaire est la taille du fichier primaire de base de données de modèle. Le journal des transactions est défini à la plus grande de ces valeurs : 512 Ko ou 25 % de la taille du fichier de données primaire. Puisque MAXSIZE n'est pas spécifié, la taille des fichiers peut s'accroître jusqu'à occuper tout l'espace disque disponible. Cet exemple montre également comment supprimer la base de données nommée `mytest`, si elle existe, avant de créer la base de données `mytest`.  
  
```  
USE master;  
GO  
IF DB_ID (N'mytest') IS NOT NULL
DROP DATABASE mytest;
GO
CREATE DATABASE mytest;  
GO  
-- Verify the database files and sizes  
SELECT name, size, size*1.0/128 AS [Size in MBs]   
FROM sys.master_files  
WHERE name = N'mytest';  
GO  
  
```  
  
### <a name="b-creating-a-database-that-specifies-the-data-and-transaction-log-files"></a>B. Création d'une base de données qui spécifie les fichiers de données et les fichiers journaux de transactions  
 L'exemple suivant crée la base de données `Sales`. Étant donné que le mot clé primaire n’est pas utilisé, le premier fichier (`Sales_dat`) devient le fichier primaire. Le paramètre SIZE n'étant spécifié ni en Mo ni en Ko pour le fichier `Sales_dat` , la valeur par défaut est Mo et il est alloué en mégaoctets. La base de données `Sales_log` est alloué en mégaoctets car le suffixe `MB` est défini explicitement dans le paramètre `SIZE` .  
  
```tsql  
USE master;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
### <a name="c-creating-a-database-by-specifying-multiple-data-and-transaction-log-files"></a>C. Création d'une base de données en spécifiant plusieurs fichiers de données et plusieurs fichiers journaux de transactions  
 Cet exemple crée une base de données appelée `Archive` qui comprend trois fichiers de données de `100-MB` et deux fichiers du journal des transactions de `100-MB`. Le fichier primaire est le premier fichier dans la liste et il est spécifié de manière explicite à l'aide du mot clé `PRIMARY`. Les fichiers du journal des transactions sont spécifiés à la suite des mots clés `LOG ON`. Notez les extensions utilisées pour les fichiers dans l'option `FILENAME` : `.mdf` pour les fichiers de données primaires, `.ndf` pour les fichiers de données secondaires et `.ldf` pour les fichiers journaux de transactions. Cet exemple place la base de données sur le lecteur `D:` plutôt qu'avec la base de données `master`.  
  
```tsql  
USE master;  
GO  
CREATE DATABASE Archive   
ON  
PRIMARY    
    (NAME = Arch1,  
    FILENAME = 'D:\SalesData\archdat1.mdf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
    ( NAME = Arch2,  
    FILENAME = 'D:\SalesData\archdat2.ndf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
    ( NAME = Arch3,  
    FILENAME = 'D:\SalesData\archdat3.ndf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20)  
LOG ON   
   (NAME = Archlog1,  
    FILENAME = 'D:\SalesData\archlog1.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
   (NAME = Archlog2,  
    FILENAME = 'D:\SalesData\archlog2.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20) ;  
GO  
```  
  
### <a name="d-creating-a-database-that-has-filegroups"></a>D. Création d'une base de données possédant des groupes de fichiers  
 L'exemple suivant crée la base de données `Sales` qui possède les groupes de fichiers suivants :  
  
-   Le groupe de fichiers primaire avec les fichiers `Spri1_dat` et `Spri2_dat`. Les incréments FILEGROWTH de ces fichiers sont spécifiés à `15%`.  
  
-   Un groupe de fichiers nommé `SalesGroup1` avec les fichiers `SGrp1Fi1` et `SGrp1Fi2`.  
  
-   Un groupe de fichiers nommé `SalesGroup2` avec les fichiers `SGrp2Fi1` et `SGrp2Fi2`.  
  
 Cet exemple place les fichiers de données et les fichiers journaux sur des disques différents afin d'améliorer les performances.  
  
```tsql  
USE master;  
GO  
CREATE DATABASE Sales  
ON PRIMARY  
( NAME = SPri1_dat,  
    FILENAME = 'D:\SalesData\SPri1dat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 15% ),  
( NAME = SPri2_dat,  
    FILENAME = 'D:\SalesData\SPri2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 15% ),  
FILEGROUP SalesGroup1  
( NAME = SGrp1Fi1_dat,  
    FILENAME = 'D:\SalesData\SG1Fi1dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
( NAME = SGrp1Fi2_dat,  
    FILENAME = 'D:\SalesData\SG1Fi2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
FILEGROUP SalesGroup2  
( NAME = SGrp2Fi1_dat,  
    FILENAME = 'D:\SalesData\SG2Fi1dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
( NAME = SGrp2Fi2_dat,  
    FILENAME = 'D:\SalesData\SG2Fi2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'E:\SalesLog\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
### <a name="e-attaching-a-database"></a>E. Attachement d'une base de données  
 L'exemple ci-dessous détache la base de données `Archive` créée dans l'exemple D, puis l'attache à l'aide de la clause `FOR ATTACH`. `Archive` a été défini de manière à posséder plusieurs fichiers de données et fichiers journaux. Cependant, l'emplacement des fichiers n'ayant pas été modifié depuis leur création, seuls les fichiers primaires doivent être spécifiés dans la clause `FOR ATTACH`. À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], tout fichier de texte intégral appartenant à la base de données qui est attachée est attaché avec la base de données.  
  
```tsql  
USE master;  
GO  
sp_detach_db Archive;  
GO  
CREATE DATABASE Archive  
      ON (FILENAME = 'D:\SalesData\archdat1.mdf')   
      FOR ATTACH ;  
GO  
```  
  
### <a name="f-creating-a-database-snapshot"></a>F. Création d'un instantané de base de données  
 L’exemple suivant crée l’instantané de base de données `sales_snapshot0600`. Un instantané de base de données étant en lecture seule, un fichier journal ne peut pas être spécifié. Conformément à la syntaxe, chaque fichier de la base de données source est spécifié et les groupes de fichiers ne sont pas spécifiés.  
  
 La base de données source dans cet exemple est la base de données `Sales` créée dans l'exemple D.  
  
```tsql  
USE master;  
GO  
CREATE DATABASE sales_snapshot0600 ON  
    ( NAME = SPri1_dat, FILENAME = 'D:\SalesData\SPri1dat_0600.ss'),  
    ( NAME = SPri2_dat, FILENAME = 'D:\SalesData\SPri2dt_0600.ss'),  
    ( NAME = SGrp1Fi1_dat, FILENAME = 'D:\SalesData\SG1Fi1dt_0600.ss'),  
    ( NAME = SGrp1Fi2_dat, FILENAME = 'D:\SalesData\SG1Fi2dt_0600.ss'),  
    ( NAME = SGrp2Fi1_dat, FILENAME = 'D:\SalesData\SG2Fi1dt_0600.ss'),  
    ( NAME = SGrp2Fi2_dat, FILENAME = 'D:\SalesData\SG2Fi2dt_0600.ss')  
AS SNAPSHOT OF Sales ;  
GO  
```  
  
### <a name="g-creating-a-database-and-specifying-a-collation-name-and-options"></a>G. Création d'une base de données et spécification d'un nom de classement et d'options  
 L'exemple suivant crée la base de données `MyOptionsTest`. Un nom de classement est spécifié et les options `TRUSTYWORTHY` et `DB_CHAINING` ont la valeur `ON`.  
  
```tsql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE French_CI_AI  
WITH TRUSTWORTHY ON, DB_CHAINING ON;  
GO  
--Verifying collation and option settings.  
SELECT name, collation_name, is_trustworthy_on, is_db_chaining_on  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
### <a name="h-attaching-a-full-text-catalog-that-has-been-moved"></a>H. Attachement d'un catalogue de texte intégral qui a été déplacé  
 L'exemple suivant attache le catalogue de texte intégral `AdvWksFtCat` ainsi que les fichiers de données et fichiers journaux de `AdventureWorks2012`. Dans cet exemple, le catalogue de texte intégral est déplacé de son emplacement par défaut vers un nouvel emplacement `c:\myFTCatalogs`. Les fichiers de données et les fichiers journaux restent dans leurs emplacements par défaut.  
  
```tsql  
USE master;  
GO  
--Detach the AdventureWorks2012 database  
sp_detach_db AdventureWorks2012;  
GO  
-- Physically move the full text catalog to the new location.  
--Attach the AdventureWorks2012 database and specify the new location of the full-text catalog.  
CREATE DATABASE AdventureWorks2012 ON   
    (FILENAME = 'c:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_data.mdf'),   
    (FILENAME = 'c:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_log.ldf'),  
    (FILENAME = 'c:\myFTCatalogs\AdvWksFtCat')  
FOR ATTACH;  
GO  
```  
  
### <a name="i-creating-a-database-that-specifies-a-row-filegroup-and-two-filestream-filegroups"></a>I. Création d'une base de données qui spécifie un groupe de fichiers de ligne et deux groupes de fichiers FILESTREAM  
 L'exemple ci-dessous crée la base de données `FileStreamDB`. La base de données est créée avec un groupe de fichiers de ligne et deux groupes de fichiers FILESTREAM. Chaque groupe de fichiers contient un fichier :  
  
-   `FileStreamDB_data` contient des données de ligne. Il contient un seul fichier, `FileStreamDB_data.mdf` avec le chemin d'accès par défaut.  
  
-   `FileStreamPhotos` contient des données FILESTREAM. Il contient deux conteneurs de données FILESTREAM : `FSPhotos` (dans `C:\MyFSfolder\Photos`) et `FSPhotos2` (dans `D:\MyFSfolder\Photos`). Il est marqué comme groupe de fichiers FILESTREAM par défaut.  
  
-   `FileStreamResumes` contient des données FILESTREAM. Il contient un seul conteneur de données FILESTREAM, `FSResumes`, qui se trouve dans `C:\MyFSfolder\Resumes`.  
  
```tsql  
USE master;  
GO  
-- Get the SQL Server data path.  
DECLARE @data_path nvarchar(256);  
SET @data_path = (SELECT SUBSTRING(physical_name, 1, CHARINDEX(N'master.mdf', LOWER(physical_name)) - 1)  
                  FROM master.sys.master_files  
                  WHERE database_id = 1 AND file_id = 1);  
  
 -- Execute the CREATE DATABASE statement.   
EXECUTE ('CREATE DATABASE FileStreamDB  
ON PRIMARY   
    (  
    NAME = FileStreamDB_data   
    ,FILENAME = ''' + @data_path + 'FileStreamDB_data.mdf''  
    ,SIZE = 10MB  
    ,MAXSIZE = 50MB  
    ,FILEGROWTH = 15%  
    ),  
FILEGROUP FileStreamPhotos CONTAINS FILESTREAM DEFAULT  
    (  
    NAME = FSPhotos  
    ,FILENAME = ''C:\MyFSfolder\Photos''  
-- SIZE and FILEGROWTH should not be specified here.  
-- If they are specified an error will be raised.  
, MAXSIZE = 5000 MB  
    ),  
    (  
      NAME = FSPhotos2  
      , FILENAME = ''D:\MyFSfolder\Photos''  
      , MAXSIZE = 10000 MB  
     ),  
FILEGROUP FileStreamResumes CONTAINS FILESTREAM  
    (  
    NAME = FileStreamResumes  
    ,FILENAME = ''C:\MyFSfolder\Resumes''  
    )   
LOG ON  
    (  
    NAME = FileStream_log  
    ,FILENAME = ''' + @data_path + 'FileStreamDB_log.ldf''  
    ,SIZE = 5MB  
    ,MAXSIZE = 25MB  
    ,FILEGROWTH = 5MB  
    )'  
);  
GO  
```  
  
### <a name="j-creating-a-database-that-has-a-filestream-filegroup-with-multiple-files"></a>J. Création d'une base de données disposant d'un groupe de fichiers FILESTREAM avec de nombreux fichiers  
 L'exemple ci-dessous crée la base de données `BlobStore1`. La base de données est créée avec un groupe de fichiers de ligne et un groupe de fichiers FILESTREAM, `FS`. Le groupe de fichiers FILESTREAM contient deux fichiers, `FS1` et `FS2`. Puis la base de données est modifiée par l'ajout d'un troisième fichier, `FS3`, au groupe de fichiers FILESTREAM.  
  
```tsql  
USE master;  
GO  
  
CREATE DATABASE [BlobStore1]  
CONTAINMENT = NONE  
ON PRIMARY   
(   
    NAME = N'BlobStore1',   
    FILENAME = N'C:\BlobStore\BlobStore1.mdf',  
    SIZE = 100MB,  
    MAXSIZE = UNLIMITED,  
    FILEGROWTH = 1MB  
),   
FILEGROUP [FS] CONTAINS FILESTREAM DEFAULT   
(  
    NAME = N'FS1',  
    FILENAME = N'C:\BlobStore\FS1',  
    MAXSIZE = UNLIMITED  
),   
(  
    NAME = N'FS2',  
    FILENAME = N'C:\BlobStore\FS2',  
    MAXSIZE = 100MB  
)  
LOG ON   
(  
    NAME = N'BlobStore1_log',  
    FILENAME = N'C:\BlobStore\BlobStore1_log.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 1GB,  
    FILEGROWTH = 1MB  
);  
GO  
  
ALTER DATABASE [BlobStore1]  
ADD FILE  
(  
    NAME = N'FS3',  
    FILENAME = N'C:\BlobStore\FS3',  
    MAXSIZE = 100MB  
)  
TO FILEGROUP [FS];  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Attacher et détacher une base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_detach_db &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_removedbreplication &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)   
 [Instantanés de base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)   
 [Déplacer des fichiers de bases de données](../../relational-databases/databases/move-database-files.md)   
 [Bases de données](../../relational-databases/databases/databases.md)   
 [Objets binaires volumineux &#40;Objet BLOB&#41; Données &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)  


