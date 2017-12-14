---
title: "tempdb, base de données | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary tables [SQL Server], tempdb database
- tempdb database [SQL Server], about tempdb
- temporary stored procedures [SQL Server]
- tempdb database [SQL Server]
ms.assetid: ce4053fb-e37a-4851-b711-8e504059a780
caps.latest.revision: "66"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.openlocfilehash: 6d71dcbda413d604c2c6ac2e4d85a815a4aa3719
ms.sourcegitcommit: ef1fa818beea435f58986af3379853dc28f5efd8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="tempdb-database"></a>Base de données tempdb
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] La base de données système **tempdb** est une ressource globale disponible pour tous les utilisateurs connectés à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sert de conteneur aux éléments suivants :  
  
- Les **objets utilisateurs** temporaires créés explicitement, tels que les tables et index temporaires locaux ou globaux, les procédures stockées temporaires, les variables de table, les tables retournées dans des fonctions table, ou les curseurs.  
- Les **objets internes** créés par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Notamment :
  - Les tables de travail afin de stocker les résultats intermédiaires pour les mises en spools, les curseurs, les tris et le stockage temporaire des des objets volumineux (LOB).
  - Les fichiers de travail correspondant aux opérations de jointures ou d'agrégations hachées
  - Les résultats de tris intermédiaires pour les opérations de création ou de reconstruction d'index (si SORT_IN_TEMPDB est spécifié) ou pour certaines requêtes GROUP BY, ORDER BY ou UNION.

  > [!NOTE]
  > Chaque objet interne utilise un minimum de neuf pages, une page IAM et une extension composée de huit pages. Pour plus d’informations sur les pages et les extensions, consultez [Pages et étendues](../../relational-databases/pages-and-extents-architecture-guide.md#pages-and-extents).

- Des **banques de versions**, qui sont un ensemble de pages de données contenant les lignes de données requises pour prendre en charge les fonctionnalités qui utilisent le contrôle de version de ligne. Il existe deux banques de versions : une banque de versions commune et une banque de versions de construction d'index en ligne. Les banques de versions contiennent les éléments suivants :
  - Les versions de ligne générées par les transactions de modification de données dans une base de données qui utilise l'isolement basé sur le contrôle de version de ligne read committed ou les transactions d'isolement d'instantané.  
  - Versions de ligne qui sont générées par les transactions de modification de données pour les fonctionnalités telles que : opérations d'index en ligne, MARS (Multiple Active Result Sets) et déclencheurs AFTER.  
  
Les opérations effectuées dans **tempdb** sont soumises à un enregistrement minimal dans le journal. Cela permet de restaurer des transactions. La base de données**tempdb** étant recréée chaque fois que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est démarré, le système démarre toujours avec une copie propre de la base de données. Les tables et les procédures stockées temporaires sont automatiquement supprimées à la déconnexion et aucune connexion n'est active lorsque le système est arrêté. Par conséquent, aucune donnée de la base de données **tempdb** ne doit être enregistrée d'une session de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'autre. La sauvegarde et la restauration ne sont pas autorisées sur la base de données **tempdb**.  
  
## <a name="physical-properties-of-tempdb"></a>Propriétés physiques de tempdb  
 Le tableau suivant répertorie les valeurs de configuration initiales des fichiers de données et des journaux de **tempdb**, qui sont basés sur les valeurs par défaut pour la base de données Model. La taille de ces fichiers peut varier légèrement en fonction des éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Fichier|Nom logique|Nom physique|Taille initiale|Croissance du fichier|  
|----------|------------------|-------------------|------------------|-----------------|  
|Données primaires|tempdev|tempdb.mdf|8 mégaoctets|Croissance automatique de 64 Mo jusqu’à saturation du disque.|  
|Fichiers de données secondaires*|temp#|tempdb_mssql_#.ndf|8 mégaoctets|Croissance automatique de 64 Mo jusqu’à saturation du disque.|  
|Journal|templog|templog.ldf|8 mégaoctets|Croissance automatique de 64 mégaoctets jusqu’à un maximum de 2 téraoctets.|  
  
 \* Le nombre de fichiers dépend du nombre de processeurs (logiques) sur l’ordinateur. En règle générale, si le nombre de processeurs logiques est inférieur ou égal à 8, utilisez le même nombre de fichiers de données que de processeurs logiques. Si le nombre de processeurs logiques est supérieur à huit, utilisez huit fichiers de données et si le conflit persiste, augmentez le nombre de fichiers de données par multiples de quatre jusqu’à ce que le conflit atteigne un niveau acceptable ou modifiez la charge de travail/le code.

> [!NOTE]
> La valeur par défaut du nombre de fichiers de données est basée sur les directives générales de l’article [KB 2154845](http://support.microsoft.com/kb/2154845/).  
  
### <a name="moving-the-tempdb-data-and-log-files"></a>Déplacement des fichiers de données et des journaux de tempdb  
 Pour déplacer les données **tempdb** et les fichiers journaux, consultez [Déplacer des bases de données système](../../relational-databases/databases/move-system-databases.md).  
  
### <a name="database-options"></a>Options de base de données  
 Le tableau suivant répertorie les valeurs par défaut de chaque option de la base de données **tempdb** et précise si elles sont modifiables. Pour afficher les valeurs actuelles de ces options, utilisez l'affichage catalogue [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) .  
  
|Option de base de données|Valeur par défaut|Peut être modifiée|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Oui|  
|ANSI_NULL_DEFAULT|OFF|Oui|  
|ANSI_NULLS|OFF|Oui|  
|ANSI_PADDING|OFF|Oui|  
|ANSI_WARNINGS|OFF|Oui|  
|ARITHABORT|OFF|Oui|  
|AUTO_CLOSE|OFF|Non|  
|AUTO_CREATE_STATISTICS|ON|Oui|  
|AUTO_SHRINK|OFF|Non|  
|AUTO_UPDATE_STATISTICS|ON|Oui|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Oui|  
|CHANGE_TRACKING|OFF|Non|  
|CONCAT_NULL_YIELDS_NULL|OFF|Oui|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Oui|  
|CURSOR_DEFAULT|GLOBAL|Oui|  
|Options de disponibilité de base de données|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|Non<br /><br /> Non<br /><br /> Non|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Oui|  
|DB_CHAINING|ON|Non|  
|ENCRYPTION|OFF|Non|  
|MIXED_PAGE_ALLOCATION|OFF|Non|  
|NUMERIC_ROUNDABORT|OFF|Oui|  
|PAGE_VERIFY|CHECKSUM pour les nouvelles installations de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NONE pour les mises à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Oui|  
|PARAMETERIZATION|SIMPLE|Oui|  
|QUOTED_IDENTIFIER|OFF|Oui|  
|READ_COMMITTED_SNAPSHOT|OFF|Non|  
|RECOVERY|SIMPLE|Non|  
|RECURSIVE_TRIGGERS|OFF|Oui|  
|Options de Service Broker|ENABLE_BROKER|Oui|  
|TRUSTWORTHY|OFF|Non|  
  
 Pour obtenir une description de ces options de base de données, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="restrictions"></a>Restrictions  
 Les opérations suivantes ne peuvent pas être effectuées sur la base de données **tempdb** :  
  
- Ajout de groupes de fichiers  
- Sauvegarde ou restauration de la base de données  
- Modification du classement. Le classement par défaut est le classement du serveur.  
- Modification du propriétaire de la base de données. La base de données**tempdb** appartient à **sa**.  
- Création d'un instantané de base de données  
- Suppression de la base de données  
- Suppression de l'utilisateur **Invité** de la base de données  
- Activation de la capture des données modifiées.  
- Participation à la mise en miroir de bases de données  
- Suppression du groupe de fichiers primaire, du fichier de données primaire ou du fichier journal  
- Changement du nom de la base de données ou du groupe de fichiers primaire  
- Exécution de DBCC CHECKALLOC  
- Exécution de DBCC CHECKCATALOG  
- Affectation de la valeur OFFLINE à la base de données.  
- Affectation de la valeur READ_ONLY à la base de données ou au groupe de fichiers primaire  
  
## <a name="permissions"></a>Autorisations  
 Tous les utilisateurs peuvent créer des objets temporaires dans tempdb. Les utilisateurs n'ont accès qu'aux objets qu'ils possèdent, sauf s'ils ont reçu des autorisations supplémentaires. Il est possible de révoquer l’autorisation de connexion à tempdb pour empêcher un utilisateur d’utiliser tempdb. Cependant, cela n’est pas recommandé, car certaines opérations courantes nécessitent l’utilisation de tempdb.  

## <a name="optimizing-tempdb-performance"></a>Optimisation des performances de la base de données tempdb
 La taille et l’emplacement physique de la base de données tempdb peuvent influer sur les performances d’un système. Par exemple, si la taille définie pour tempdb est trop petite, il se peut qu'à chaque redémarrage de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une partie de la charge de traitement du système soit absorbée par l'ajustement automatique de tempdb à la taille nécessaire à la gestion de la charge de travail.

 Si possible, utilisez [l’initialisation instantanée de fichiers de base de données](../../relational-databases/databases/database-instant-file-initialization.md) pour améliorer les performances des opérations de croissance de fichiers de données.
 
 Pré-allouez l'espace de tous les fichiers de tempdb en définissant leur taille avec une valeur suffisamment élevée pour assumer la charge de travail habituelle de l'environnement. Cela évite que tempdb ne se développe trop fréquemment et que les performances n'en soient affectées. La base de données tempdb doit être définie de façon à autoriser la croissance automatique, mais celle-ci doit être utilisée pour augmenter l'espace disque en cas d'exceptions non prévues. 

 Les fichiers de données doivent être de taille égale dans chaque [groupe de fichiers](../../relational-databases/databases/database-files-and-filegroups.md#filegroups), car [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise un algorithme de remplissage proportionnel qui privilégie les allocations dans les fichiers ayant davantage d’espace libre. Le fait de diviser tempdb en plusieurs fichiers de données de taille égale procure un niveau élevé d’efficacité parallèle dans les opérations qui utilisent tempdb. 
 
 Définissez l'incrément de croissance de la taille du fichier avec une taille suffisante afin d'éviter que la valeur de croissance des fichiers de la base de données tempdb ne soit trop faible. Si, au vu de la quantité de données à écrire dans la base de données tempdb, l'incrément de croissance est trop faible, la base de données tempdb risque d'avoir à se développer en permanence, affectant ainsi les performances.
 
 Pour vérifier les paramètres actuels de croissance et de taille de tempdb, utilisez la requête suivante :
 ```t-sql
 SELECT name AS FileName, 
    size*1.0/128 AS FileSizeinMB,
    CASE max_size 
        WHEN 0 THEN 'Autogrowth is off.'
        WHEN -1 THEN 'Autogrowth is on.'
        ELSE 'Log file will grow to a maximum size of 2 TB.'
    END,
    growth AS 'GrowthValue',
    'GrowthIncrement' = 
        CASE
            WHEN growth = 0 THEN 'Size is fixed and will not grow.'
            WHEN growth > 0 AND is_percent_growth = 0 
                THEN 'Growth value is in 8-KB pages.'
            ELSE 'Growth value is a percentage.'
        END
FROM tempdb.sys.database_files;
GO
```
 
 Placez la base de données tempdb sur un sous-système d'E/S rapide. Si plusieurs disques sont directement attachés, utilisez l'agrégation de disques. Il n’est pas obligatoire que les fichiers ou les groupes de fichiers de données tempdb soient sur des disques ou des piles de disques différents, sauf si vous observez également des goulots d’étranglement d’E/S.
 
 Placez la base de données tempdb sur des disques différents de ceux employés par les bases de données utilisateur.

## <a name="performance-improvements-in-tempdb"></a>Amélioration des performances dans tempdb  
 À compter de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], les performances de **tempdb** sont optimisées comme suit :  
  
- Les tables temporaires et les variables de table sont mises en cache. La mise en cache permet aux opérations de création et de suppression des objets temporaires de s'exécuter très rapidement et réduit la contention d'allocation des pages.  
- Le protocole d'accès aux pages d'allocation est amélioré. Cela réduit le nombre de verrous de mise à jour utilisés.  
- La surcharge d'enregistrement pour **tempdb** est réduite. Cela réduit la consommation de bande passante au niveau des E/S de disque sur le fichier journal **tempdb** .  
- Le programme d’installation ajoute plusieurs fichiers de données tempdb lors de l’installation d’une nouvelle instance. Cette tâche peut être réalisée par le biais du nouveau contrôle d’entrée de l’interface utilisateur dans la rubrique **Configuration du moteur de base de données** et d’un paramètre de ligne de commande /SQLTEMPDBFILECOUNT. Par défaut, le programme d’installation ajoute huit fichiers de données tempdb ou autant de fichiers de données tempdb que de processeurs logiques, la valeur la plus petite étant retenue.  
- S’il existe plusieurs fichiers de base de données **tempdb** , ces fichiers continuent tous de croître de la même manière en même temps en fonction des paramètres de croissance. L’indicateur de trace 1117 n’est plus nécessaire.  
- Toutes les allocations dans **tempdb** utilisent des extensions uniformes. [L’indicateur de trace 1118](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) n’est plus nécessaire.  
- Pour le groupe de fichiers primaire, la propriété AUTOGROW_ALL_FILES est activée et la propriété ne peut pas être modifiée. 

## <a name="capacity-planning-for-tempdb"></a>Planification des capacités de tempdb
 La détermination de la taille appropriée pour tempdb dans un environnement de production dépend de nombreux facteurs. Comme décrit plus haut dans cette rubrique, ces facteurs incluent la charge de travail existante et les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisées. Nous vous recommandons d’analyser la charge de travail existante en effectuant les tâches suivantes dans un environnement de test SQL Server :
- Activez la croissance automatique de tempdb.
- Exécutez les requêtes individuelles ou les fichiers de trace de la charge de travail, et surveillez l’utilisation de l’espace dans tempdb.
- Exécutez les opérations de maintenance des index, comme leur reconstruction et la surveillance de l’espace dans tempdb. 
- Retenez les valeurs d’utilisation de l’espace des étapes précédentes pour prédire l’utilisation de la charge de travail totale, ajustez cette valeur en fonction de l’activité simultanée prévue, et définissez la taille de tempdb en conséquence.

## <a name="how-to-monitor-tempdb-use"></a>Mode de surveillance de l’utilisation de tempdb
  Un espace disque insuffisant dans tempdb peut générer des perturbations significatives dans l’environnement de production [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et empêcher les applications en cours d’exécution de terminer leurs opérations. Vous pouvez utiliser la vue de gestion dynamique [sys.dm_db_file_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md) pour surveiller l’espace disque utilisé dans les fichiers tempdb :
  
 ```t-sql
 -- Determining the Amount of Free Space in tempdb
 SELECT SUM(unallocated_extent_page_count) AS [free pages], 
  (SUM(unallocated_extent_page_count)*1.0/128) AS [free space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
 
 ```t-sql
 -- Determining the Amount Space Used by the Version Store
 SELECT SUM(version_store_reserved_page_count) AS [version store pages used],
  (SUM(version_store_reserved_page_count)*1.0/128) AS [version store space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
 
 ```t-sql
 -- Determining the Amount of Space Used by Internal Objects
 SELECT SUM(internal_object_reserved_page_count) AS [internal object pages used],
  (SUM(internal_object_reserved_page_count)*1.0/128) AS [internal object space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
 
 ```t-sql
 -- Determining the Amount of Space Used by User Objects
 SELECT SUM(user_object_reserved_page_count) AS [user object pages used],
  (SUM(user_object_reserved_page_count)*1.0/128) AS [user object space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
  
  En outre, pour surveiller l’activité d’allocation et de désallocation de pages dans tempdb au niveau de la session ou de la tâche, vous pouvez utiliser les vues de gestion dynamique [sys.dm_db_session_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md) et [sys.dm_db_task_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md). Ces vues permettent d’identifier les requêtes, les tables temporaires et les variables de table qui utilisent un espace disque volumineux dans tempdb. Il existe également plusieurs compteurs permettant de surveiller l’espace libre disponible dans tempdb, ainsi que les ressources qui utilisent tempdb. Pour plus d'informations, consultez la section suivante.

 ```t-sql
 -- Obtaining the space consumed by internal objects in all currently running tasks in each session
 SELECT session_id, 
  SUM(internal_objects_alloc_page_count) AS task_internal_objects_alloc_page_count,
  SUM(internal_objects_dealloc_page_count) AS task_internal_objects_dealloc_page_count 
 FROM sys.dm_db_task_space_usage 
 GROUP BY session_id;
 ```
 
 ```t-sql
 -- Obtaining the space consumed by internal objects in the current session for both running and completed tasks
 SELECT R2.session_id,
  R1.internal_objects_alloc_page_count 
  + SUM(R2.internal_objects_alloc_page_count) AS session_internal_objects_alloc_page_count,
  R1.internal_objects_dealloc_page_count 
  + SUM(R2.internal_objects_dealloc_page_count) AS session_internal_objects_dealloc_page_count
 FROM sys.dm_db_session_space_usage AS R1 
 INNER JOIN sys.dm_db_task_space_usage AS R2 ON R1.session_id = R2.session_id
 GROUP BY R2.session_id, R1.internal_objects_alloc_page_count, 
  R1.internal_objects_dealloc_page_count;;
 ```

## <a name="related-content"></a>Contenu associé  
 [Option SORT_IN_TEMPDB pour les index](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)  
 [Bases de données système](../../relational-databases/databases/system-databases.md)  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
 [Déplacer des fichiers de bases de données](../../relational-databases/databases/move-database-files.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de tempdb dans SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81216)  
 [Résolution des problèmes d’espace disque insuffisant dans tempdb](http://msdn.microsoft.com/library/ms176029.aspx) 
