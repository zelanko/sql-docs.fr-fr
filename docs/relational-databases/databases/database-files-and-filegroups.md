---
title: "Groupes de fichiers et fichiers de base de données | Microsoft Docs"
ms.custom: 
ms.date: 10/11/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases [SQL Server], files
- filegroups [SQL Server]
- transaction logs [SQL Server], about
- transaction logs [SQL Server], files
- .mdf files
- data files [SQL Server]
- default filegroups
- files [SQL Server], about files and filegroups
- secondary files [SQL Server]
- log files [SQL Server]
- .ndf files
- files [SQL Server]
- .ldf files
- database files [SQL Server]
- databases [SQL Server], filegroups
- filegroups [SQL Server], types
- primary filegroups [SQL Server]
- user-defined filegroups [SQL Server]
- filegroups [SQL Server], about filegroups
- primary files [SQL Server]
- file types [SQL Server]
ms.assetid: 9ca11918-480d-4838-9198-cec221ef6ad0
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 73fde10c6cf318e5cd5c7eaa52a55a36f4d82001
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="database-files-and-filegroups"></a>Groupes de fichiers et fichiers de base de données
  Chaque base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possède au moins deux fichiers de système d'exploitation : un fichier de données et un fichier journal. Les fichiers de données contiennent des données et des objets tels que des tables, des index, des procédures stockées et des vues. Les fichiers journaux contiennent les informations nécessaires pour récupérer toutes les transactions de la base de données. Les fichiers de données peuvent être regroupés dans des groupes de fichiers à des fins d'allocation et d'administration.  
  
## <a name="database-files"></a>Fichiers de base de données  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les bases de données possèdent trois types de fichiers, comme indiqué dans le tableau suivant.  
  
|Fichier|Description|  
|----------|-----------------|  
|Principal|Le fichier de données primaire contient les informations de démarrage de la base de données, et il pointe vers les autres fichiers de la base de données. Les objets et les données utilisateur peuvent être stockés dans ce fichier ou dans des fichiers de données secondaires. Chaque base de données comprend un fichier de données primaire. L'extension de fichier recommandée est .mdf.|  
|Secondary|Les fichiers de données secondaires sont facultatifs, définis par l'utilisateur, et ils stockent les données utilisateur. Les fichiers secondaires peuvent être utilisés pour répartir des données sur plusieurs disques en plaçant chaque fichier sur un lecteur de disque distinct. En outre, si la taille d'une base de données excède la taille maximale autorisée pour un fichier Windows, vous pouvez avoir recours aux fichiers secondaires afin que la base de données puisse continuer à croître.<br /><br /> L'extension de fichier recommandée est .ndf.|  
|Journal des transactions|Les fichiers journaux des transactions contiennent les informations du journal qui sont utilisées pour la restauration de la base de données. Chaque base de données doit posséder au moins un fichier journal. L'extension de fichier recommandée pour les journaux des transactions est .ldf.|  
  
 Par exemple, il est possible de créer une base de données simple (appelée **Sales** ) incluant un fichier primaire qui contient toutes les données et tous les objets, et un fichier journal qui contient les informations du journal des transactions. Ou encore, il est possible de créer une base de données plus complexe (appelée **Orders** ) incluant un fichier primaire et cinq fichiers secondaires. Les données et les objets de la base de données sont répartis dans les six fichiers, et les quatre fichiers journaux contiennent les informations du journal des transactions.  
  
 Par défaut, les données et les journaux des transactions sont placés sur le même lecteur et leur chemin est identique, ceci afin de gérer les systèmes comportant un seul disque. Cependant, cette configuration n'est pas forcément optimale pour les environnements de production. Nous vous recommandons de placer les fichiers de données et les fichiers journaux sur des disques distincts.  

### <a name="logical-and-physical-file-names"></a>Noms de fichiers logiques et physiques

Les fichiers SQL Server portent deux noms : 

**logical_file_name**  : nom utilisé pour faire référence au fichier physique dans toutes les instructions Transact-SQL. Le nom de fichier logique doit respecter les règles régissant les identificateurs SQL Server et doit être unique parmi les noms de fichiers logiques de la base de données.

**os_file_name** : nom du fichier physique, comprenant le chemin du répertoire. Il doit respecter les règles en vigueur pour les noms de fichiers du système d'exploitation.

Les données et les fichiers journaux SQL Server peuvent être placés dans les systèmes de fichiers FAT ou NTFS. Nous vous recommandons d'utiliser le système de fichiers NTFS pour des raisons de sécurité. Les fichiers journaux et les groupes de fichiers de données en lecture/écriture ne peuvent pas être implantés dans un système de fichiers compressé NTFS. Seuls les groupes de fichiers secondaires en lecture seule et les bases de données en lecture seule peuvent être implantés dans un système de fichiers compressé NTFS.

Lorsque plusieurs instances de SQL Server sont exécutées sur un ordinateur unique, chaque instance reçoit son propre répertoire par défaut pour contenir les fichiers des bases de données créées dans l’instance. Pour plus d’informations, consultez [Emplacements des fichiers pour les instances par défaut et les instances nommées de SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).

### <a name="data-file-pages"></a>Pages de fichiers de données

Les pages d’un fichier de données SQL Server sont numérotées de manière séquentielle, zéro (0) correspondant à la première page. Chaque fichier d'une base de données possède un numéro d'identification de fichier unique. L'ID de fichier et le numéro de page sont nécessaires pour identifier de manière unique une page d'une base de données. L'exemple ci-dessous montre les numéros de page d'une base de données disposant d'un fichier de données primaire de 4 Mo et d'un fichier de données secondaire de 1 Mo.

![data_file_pages](../../relational-databases/databases/media/data-file-pages.gif)

La première page de chaque fichier est une page d'en-tête qui contient des informations sur les attributs du fichier. D'autres pages situées au début du fichier contiennent également des informations sur le système, comme les tables d'allocation. Une des pages système stockée à la fois dans le fichier de données primaire et dans le premier fichier journal est une page d'amorçage de base de données qui contient des informations sur les attributs de la base de données. Pour plus d’informations sur les pages et les types de pages, consultez « Fonctionnement des pages et étendues ».

### <a name="file-size"></a>Taille du fichier

Les fichiers SQL Server peuvent augmenter automatiquement leur volume et dépasser leur taille d’origine. Lorsque vous définissez un fichier, vous pouvez spécifier un incrément de croissance précis. Chaque fois que le fichier est rempli, sa taille augmente en fonction de l'incrément de croissance. Si un groupe comporte plusieurs fichiers, ces derniers ne s'accroissent pas automatiquement jusqu'à ce que tous les fichiers soient remplis. La croissance se produit dans ce cas selon le principe de chacun son tour.

Chaque fichier peut également avoir une taille maximale. En l'absence de spécification, le fichier continue à s'accroître jusqu'à ce que tout l'espace disque disponible soit utilisé. Cette fonctionnalité s’avère particulièrement utile lorsque SQL Server sert de base de données incorporée dans une application pour laquelle l’utilisateur n’a pas accès à un administrateur système. L'utilisateur peut laisser les fichiers s'accroître automatiquement autant que nécessaire pour réduire la charge administrative liée à la gestion de l'espace disponible dans la base de données et à l'affectation manuelle d'espace supplémentaire. 


## <a name="database-snapshot-files"></a>Fichiers d'instantanés de base de données

Le format de fichier utilisé par un instantané de base de données pour stocker ses données de copie lors de l'écriture varie selon que l'instantané a été créé par un utilisateur ou utilisé en interne :

* Un instantané de base de données créé par un utilisateur stocke ses données dans un ou plusieurs fichiers partiellement alloués. La technologie des fichiers partiellement alloués constitue une fonctionnalité du système de fichiers NTFS. Au départ, un fichier partiellement alloué ne contient pas de données utilisateur et aucun espace disque pour les données utilisateur ne lui a été alloué. Pour des informations générales sur l’utilisation des fichiers partiellement alloués dans un instantané de base de données et sur le schéma de croissance des instantanés de bases de données, consultez [Afficher la taille du fichier partiellement alloué d’un instantané de base de données (Transact-SQL)](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md). 
* Les instantanés de base de données sont utilisés en interne par certaines commandes DBCC. Citons notamment les commandes DBCC CHECKDB, DBCC CHECKTABLE, DBCC CHECKALLOC et DBCC CHECKFILEGROUP. Un instantané interne de base de données utilise les flux de données de remplacement éparses des fichiers de la base de données d'origine. Comme les fichiers partiellement alloués, les flux de données de remplacement sont une fonctionnalité du système de fichiers NTFS. L'utilisation de flux de données de remplacement éparses permet d'associer plusieurs affectations de données avec un seul fichier ou dossier sans influer sur les statistiques de taille de fichier ou de volume. 


  
## <a name="filegroups"></a>Groupes de fichiers  
 Chaque base de données possède un groupe de fichiers primaire. Celui-ci contient le fichier de données primaire et tous les fichiers secondaires qui n'ont pas été placés dans d'autres groupes de fichiers. Il est possible de créer des groupes de fichiers définis par l'utilisateur pour regrouper des fichiers de données à des fins d'administration, d'allocation des données et de placement.  
  
 Par exemple, trois fichiers (Data1.ndf, Data2.ndf, et Data3.ndf) peuvent être créés sur trois lecteurs, respectivement, puis affectés au groupe de fichiers **fgroup1**. Une table peut alors être créée spécialement pour le groupe de fichiers **fgroup1**. Les requêtes portant sur des données de la table seront réparties sur les trois disques, ce qui permettra d'améliorer les performances. Une amélioration similaire des performances pourra être obtenue en créant un fichier unique sur un jeu de bandes RAID (Redundant Array of Independent Disks). Cependant, les fichiers et les groupes de fichiers vous permettent d'ajouter facilement des fichiers sur de nouveaux disques.  
  
 Tous les fichiers de données sont stockés dans les groupes de fichiers répertoriés dans le tableau suivant.  
  
|Groupe de fichiers|Description|  
|---------------|-----------------|  
|Principal|Groupe de fichiers qui contient le fichier primaire. Toutes les tables système sont allouées au groupe de fichiers primaire.|  
|Définie par l'utilisateur|Groupe de fichiers créé par l'utilisateur lorsque celui-ci crée la base de données ou lorsqu'il la modifie ultérieurement.|  
  
### <a name="default-filegroup"></a>Groupe de fichiers par défaut  
 Lorsque des objets sont créés dans la base de données, sans spécifier le groupe de fichiers auquel ils appartiennent, ces objets sont affectés au groupe de fichiers par défaut. À tout moment, un groupe de fichiers précis est désigné comme étant le groupe de fichiers par défaut. Les fichiers du groupe de fichiers par défaut doivent être suffisamment volumineux pour contenir tous les nouveaux objets qui ne sont pas affectés à d'autres groupes de fichiers.  
  
 Le groupe de fichiers PRIMARY est le groupe de fichiers par défaut sauf s'il est modifié par l'instruction ALTER DATABASE. Les objets et tables système restent affectés au groupe de fichiers PRIMARY, et non au nouveau groupe par défaut.  

### <a name="file-and-filegroup-example"></a>Exemple de fichier et de groupe de fichiers

L’exemple ci-dessous crée une base de données sur une instance de SQL Server. La base de données possède un fichier de données primaire, un groupe de fichiers défini par l'utilisateur et un fichier journal. Le fichier de données primaire fait partie du groupe de fichiers primaire et le groupe de fichiers défini par l'utilisateur possède deux fichiers de données secondaires. Une instruction ALTER DATABASE fait du groupe de fichiers défini par l'utilisateur le groupe par défaut. Une table est ensuite créée en spécifiant le groupe de fichiers défini par l'utilisateur. Cet exemple utilise le chemin générique `c:\Program Files\Microsoft SQL Server\MSSQL.1` pour éviter de spécifier une version de SQL Server.

```
USE master;
GO
-- Create the database with the default data
-- filegroup and a log file. Specify the
-- growth increment and the max size for the
-- primary data file.
CREATE DATABASE MyDB
ON PRIMARY
  ( NAME='MyDB_Primary',
    FILENAME=
       'c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\data\MyDB_Prm.mdf',
    SIZE=4MB,
    MAXSIZE=10MB,
    FILEGROWTH=1MB),
FILEGROUP MyDB_FG1
  ( NAME = 'MyDB_FG1_Dat1',
    FILENAME =
       'c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\data\MyDB_FG1_1.ndf',
    SIZE = 1MB,
    MAXSIZE=10MB,
    FILEGROWTH=1MB),
  ( NAME = 'MyDB_FG1_Dat2',
    FILENAME =
       'c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\data\MyDB_FG1_2.ndf',
    SIZE = 1MB,
    MAXSIZE=10MB,
    FILEGROWTH=1MB)
LOG ON
  ( NAME='MyDB_log',
    FILENAME =
       'c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\data\MyDB.ldf',
    SIZE=1MB,
    MAXSIZE=10MB,
    FILEGROWTH=1MB);
GO
ALTER DATABASE MyDB 
  MODIFY FILEGROUP MyDB_FG1 DEFAULT;
GO

-- Create a table in the user-defined filegroup.
USE MyDB;
CREATE TABLE MyTable
  ( cola int PRIMARY KEY,
    colb char(8) )
ON MyDB_FG1;
GO
```

L'illustration ci-dessous récapitule les résultats de l'exemple précédent.

![filegroup_example](../../relational-databases/databases/media/filegroup-example.gif)
  
## <a name="related-content"></a>Contenu connexe  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
 [Options de fichiers et de groupes de fichiers ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)  
  
 [Attacher et détacher une base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
