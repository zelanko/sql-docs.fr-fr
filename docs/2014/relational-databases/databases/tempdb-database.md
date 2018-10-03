---
title: tempdb, base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- temporary tables [SQL Server], tempdb database
- tempdb database [SQL Server], about tempdb
- temporary stored procedures [SQL Server]
- tempdb database [SQL Server]
ms.assetid: ce4053fb-e37a-4851-b711-8e504059a780
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 81d2bf84e758ccfd8664408a760e77700a323e0e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141059"
---
# <a name="tempdb-database"></a>Base de données tempdb
  La base de données système **tempdb** est une ressource globale disponible pour tous les utilisateurs connectés à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sert de conteneur aux éléments suivants :  
  
-   Les objets utilisateurs temporaires créés explicitement, tels que les tables temporaires locales ou globales, les procédures stockées temporaires, les variables de table ou les curseurs.  
  
-   Des objets internes créés par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], par exemple, les tables de travail servant à stocker des résultats intermédiaires pour les mises en attente ou le tri.  
  
-   Les versions de ligne générées par les transactions de modification de données dans une base de données qui utilise l'isolement basé sur le contrôle de version de ligne read committed ou les transactions d'isolement d'instantané.  
  
-   Versions de ligne qui sont générées par les transactions de modification de données pour les fonctionnalités telles que : opérations d'index en ligne, MARS (Multiple Active Result Sets) et déclencheurs AFTER.  
  
 Les opérations effectuées dans **tempdb** sont soumises à un enregistrement minimal dans le journal. Cela permet de restaurer des transactions. La base de données**tempdb** étant recréée chaque fois que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est démarré, le système démarre toujours avec une copie propre de la base de données. Les tables et les procédures stockées temporaires sont automatiquement supprimées à la déconnexion et aucune connexion n'est active lorsque le système est arrêté. Par conséquent, aucune donnée de la base de données **tempdb** ne doit être enregistrée d'une session de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'autre. La sauvegarde et la restauration ne sont pas autorisées sur la base de données **tempdb**.  
  
## <a name="physical-properties-of-tempdb"></a>Propriétés physiques de tempdb  
 Le tableau suivant répertorie les valeurs de configuration initiales des fichiers de données et des journaux de **tempdb** . La taille de ces fichiers peut varier légèrement en fonction des éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Fichier|Nom logique|Nom physique|Croissance du fichier|  
|----------|------------------|-------------------|-----------------|  
|Données primaires|tempdev|tempdb.mdf|Croissance automatique de 10 pour cent jusqu'à ce que le disque soit plein|  
|Journal|templog|templog.ldf|Croissance automatique de 10 % jusqu'à un maximum de 2 téraoctets|  
  
 La taille de **tempdb** peut affecter les performances d’un système. Par exemple, si le **tempdb** taille est trop petite, le traitement du système est peut-être trop occupée à faire croître la base de données pour prendre en charge les besoins de votre charge de travail chaque fois que vous démarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez éviter cette surcharge en augmentant la taille de **tempdb**.  
  
## <a name="performance-improvements-in-tempdb"></a>Performances accrues dans tempdb  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les performances de **tempdb** connaissent les améliorations suivantes :  
  
-   Les tables temporaires et les variables de table peuvent être mises en cache. La mise en cache permet aux opérations de création et de suppression des objets temporaires de s'exécuter très rapidement et réduit la contention d'allocation des pages.  
  
-   Le protocole d'accès aux pages d'allocation est amélioré. Cela réduit le nombre de verrous de mise à jour utilisés.  
  
-   La surcharge d'enregistrement pour **tempdb** est réduite. Cela réduit la consommation de bande passante au niveau des E/S de disque sur le fichier journal **tempdb** .  
  
-   L’algorithme d’allocation de pages mixtes dans **tempdb** est améliorée.  
  
### <a name="moving-the-tempdb-data-and-log-files"></a>Déplacement des fichiers de données et des journaux de tempdb  
 Pour déplacer les données **tempdb** et les fichiers journaux, consultez [Déplacer des bases de données système](system-databases.md).  
  
### <a name="database-options"></a>Options de base de données  
 Le tableau suivant répertorie les valeurs par défaut de chaque option de la base de données **tempdb** et précise si elles sont modifiables. Pour afficher les valeurs actuelles de ces options, utilisez l'affichage catalogue [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Option de base de données|Valeur par défaut|Peut être modifiée|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Oui|  
|ANSI_NULL_DEFAULT|OFF|Oui|  
|ANSI_NULLS|OFF|Oui|  
|ANSI_PADDING|OFF|Oui|  
|ANSI_WARNINGS|OFF|Oui|  
|ARITHABORT|OFF|Oui|  
|AUTO_CLOSE|OFF|non|  
|AUTO_CREATE_STATISTICS|ON|Oui|  
|AUTO_SHRINK|OFF|non|  
|AUTO_UPDATE_STATISTICS|ON|Oui|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Oui|  
|CHANGE_TRACKING|OFF|non|  
|CONCAT_NULL_YIELDS_NULL|OFF|Oui|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Oui|  
|CURSOR_DEFAULT|GLOBAL|Oui|  
|Options de disponibilité de base de données|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|non<br /><br /> non<br /><br /> non|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Oui|  
|DB_CHAINING|ON|non|  
|ENCRYPTION|OFF|non|  
|NUMERIC_ROUNDABORT|OFF|Oui|  
|PAGE_VERIFY|CHECKSUM pour les nouvelles installations de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NONE pour les mises à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Oui|  
|PARAMETERIZATION|SIMPLE|Oui|  
|QUOTED_IDENTIFIER|OFF|Oui|  
|READ_COMMITTED_SNAPSHOT|OFF|non|  
|RECOVERY|SIMPLE|non|  
|RECURSIVE_TRIGGERS|OFF|Oui|  
|Options de Service Broker|ENABLE_BROKER|Oui|  
|TRUSTWORTHY|OFF|non|  
  
 Pour obtenir une description de ces options de base de données, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
## <a name="restrictions"></a>Restrictions  
 Les opérations suivantes ne peuvent pas être effectuées sur la base de données **tempdb** :  
  
-   Ajout de groupes de fichiers  
  
-   Sauvegarde ou restauration de la base de données  
  
-   Modification du classement. Le classement par défaut est le classement du serveur.  
  
-   Modification du propriétaire de la base de données. La base de données**tempdb** appartient à **sa**.  
  
-   Création d'un instantané de base de données  
  
-   Suppression de la base de données  
  
-   Suppression de l'utilisateur **Invité** de la base de données  
  
-   Activation de la capture des données modifiées.  
  
-   Participation à la mise en miroir de bases de données  
  
-   Suppression du groupe de fichiers primaire, du fichier de données primaire ou du fichier journal  
  
-   Changement du nom de la base de données ou du groupe de fichiers primaire  
  
-   Exécution de DBCC CHECKALLOC  
  
-   Exécution de DBCC CHECKCATALOG  
  
-   Affectation de la valeur OFFLINE à la base de données.  
  
-   Affectation de la valeur READ_ONLY à la base de données ou au groupe de fichiers primaire  
  
## <a name="permissions"></a>Permissions  
 Tous les utilisateurs peuvent créer des objets temporaires dans tempdb. Les utilisateurs n'ont accès qu'aux objets qu'ils possèdent, sauf s'ils ont reçu des autorisations supplémentaires. Il est possible de révoquer l’autorisation de connexion à tempdb pour empêcher un utilisateur d’utiliser tempdb. Cependant, cela n’est pas recommandé, car certaines opérations courantes nécessitent l’utilisation de tempdb.  
  
## <a name="related-content"></a>Contenu associé  
 [Option SORT_IN_TEMPDB pour les index](../indexes/indexes.md)  
  
 [Bases de données système](system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Déplacer des fichiers de bases de données](move-database-files.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de tempdb dans SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81216)  
  
  
