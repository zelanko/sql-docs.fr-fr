---
title: "tempdb, base de données | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary tables [SQL Server], tempdb database
- tempdb database [SQL Server], about tempdb
- temporary stored procedures [SQL Server]
- tempdb database [SQL Server]
ms.assetid: ce4053fb-e37a-4851-b711-8e504059a780
caps.latest.revision: 66
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 003196d8c30ca45c54750587c03c8d7d6e5a358d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/31/2017

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
  
|Fichier|Nom logique|Nom physique|Taille initiale|Croissance du fichier|  
|----------|------------------|-------------------|------------------|-----------------|  
|Données primaires|tempdev|tempdb.mdf|8 mégaoctets|Croissance automatique de 64 Mo jusqu’à saturation du disque.|  
|Fichiers de données secondaires*|temp#|tempdb_mssql_#.ndf|8 mégaoctets|Croissance automatique de 64 Mo jusqu’à saturation du disque.|  
|Journal|templog|templog.ldf|8 mégaoctets|Croissance automatique de 64 mégaoctets jusqu’à un maximum de 2 téraoctets.|  
  
 \* Le nombre de fichiers dépend du nombre de cœurs (logiques) sur l’ordinateur. La valeur sera le nombre de cœurs ou 8, la valeur la plus petite étant retenue.   
La valeur par défaut du nombre de fichiers de données est basée sur les directives générales de l’article [KB 2154845](https://support.microsoft.com/en-us/kb/2154845/).  
  
## <a name="performance-improvements-in-tempdb"></a>Performances accrues dans tempdb  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les performances de **tempdb** connaissent les améliorations suivantes :  
  
-   Les tables temporaires et les variables de table peuvent être mises en cache. La mise en cache permet aux opérations de création et de suppression des objets temporaires de s'exécuter très rapidement et réduit la contention d'allocation des pages.  
  
-   Le protocole d'accès aux pages d'allocation est amélioré. Cela réduit le nombre de verrous de mise à jour utilisés.  
  
-   La surcharge d'enregistrement pour **tempdb** est réduite. Cela réduit la consommation de bande passante au niveau des E/S de disque sur le fichier journal **tempdb** .  
  
-   Le programme d’installation ajoute plusieurs fichiers de données tempdb lors de l’installation d’une nouvelle instance. Cette tâche peut être réalisée par le biais du nouveau contrôle d’entrée de l’interface utilisateur dans la rubrique **Configuration du moteur de base de données** et d’un paramètre de ligne de commande /SQLTEMPDBFILECOUNT. Par défaut, le programme d’installation ajoute 8 fichiers tempdb ou autant de fichiers tempdb que de processeurs, la valeur la plus petite étant retenue.  
  
-   S’il existe plusieurs fichiers de base de données **tempdb** , ces fichiers continuent tous de croître de la même manière en même temps en fonction des paramètres de croissance.  L’indicateur de trace 1117 n’est plus nécessaire.  
  
-   Toutes les allocations dans **tempdb** utilisent des extensions uniformes. L’indicateur de trace 1118 n’est plus nécessaire.  
  
-   Pour le groupe de fichiers primaire, la propriété AUTOGROW_ALL_FILES est activée et la propriété ne peut pas être modifiée.  
  
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
  
## <a name="permissions"></a>Autorisations  
 Tous les utilisateurs peuvent créer des objets temporaires dans tempdb. Les utilisateurs n'ont accès qu'aux objets qu'ils possèdent, sauf s'ils ont reçu des autorisations supplémentaires. Il est possible de révoquer l’autorisation de connexion à tempdb pour empêcher un utilisateur d’utiliser tempdb. Cependant, cela n’est pas recommandé, car certaines opérations courantes nécessitent l’utilisation de tempdb.  
  
## <a name="related-content"></a>Contenu connexe  
 [Option SORT_IN_TEMPDB pour les index](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)  
  
 [Bases de données système](../../relational-databases/databases/system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
 [Déplacer des fichiers de bases de données](../../relational-databases/databases/move-database-files.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de tempdb dans SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81216)  
  
  

