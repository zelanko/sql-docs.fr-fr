---
title: tempdb, base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- temporary tables [SQL Server], tempdb database
- tempdb database [SQL Server], about tempdb
- temporary stored procedures [SQL Server]
- tempdb database [SQL Server]
ms.assetid: ce4053fb-e37a-4851-b711-8e504059a780
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7150ca05e536214d43d4992ed1e7f79138ac2be9
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965689"
---
# <a name="tempdb-database"></a>Base de données tempdb
  La base de données système **tempdb** est une ressource globale disponible pour tous les utilisateurs connectés à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sert de conteneur aux éléments suivants :  
  
-   Les objets utilisateurs temporaires créés explicitement, tels que les tables temporaires locales ou globales, les procédures stockées temporaires, les variables de table ou les curseurs.  
  
-   Des objets internes créés par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], par exemple, les tables de travail servant à stocker des résultats intermédiaires pour les mises en attente ou le tri.  
  
-   Les versions de ligne générées par les transactions de modification de données dans une base de données qui utilise l'isolement basé sur le contrôle de version de ligne read committed ou les transactions d'isolement d'instantané.  
  
-   Versions de ligne qui sont générées par les transactions de modification de données pour les fonctionnalités telles que : opérations d'index en ligne, MARS (Multiple Active Result Sets) et déclencheurs AFTER.  
  
 Les opérations effectuées dans **tempdb** sont soumises à un enregistrement minimal dans le journal. Cela permet de restaurer des transactions. **tempdb** est recréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à chaque démarrage, de sorte que le système démarre toujours avec une copie propre de la base de données. Les tables et les procédures stockées temporaires sont automatiquement supprimées à la déconnexion et aucune connexion n'est active lorsque le système est arrêté. Par conséquent, il n’y a jamais de contenu dans **tempdb** à enregistrer d’une session de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’autre. La sauvegarde et la restauration ne sont pas autorisées sur la base de données **tempdb**.  
  
## <a name="physical-properties-of-tempdb"></a>Propriétés physiques de tempdb  
 Le tableau suivant répertorie les valeurs de configuration initiales des fichiers de données et des journaux de **tempdb** . La taille de ces fichiers peut varier légèrement en fonction des éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Fichier|Nom logique|Nom physique|Croissance du fichier|  
|----------|------------------|-------------------|-----------------|  
|Données primaires|tempdev|tempdb.mdf|Croissance automatique de 10 pour cent jusqu'à ce que le disque soit plein|  
|Journal|templog|templog.ldf|Croissance automatique de 10 % jusqu'à un maximum de 2 téraoctets|  
  
 La taille de **tempdb** peut affecter les performances d’un système. Par exemple, si la taille de **tempdb** est trop petite, le traitement du système peut être trop occupé avec la croissance automatique de la base de données pour prendre en charge les exigences de votre charge de travail chaque fois que vous démarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez éviter cette surcharge en accroissant la taille de **tempdb**.  
  
## <a name="performance-improvements-in-tempdb"></a>Performances accrues dans tempdb  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les performances de **tempdb** connaissent les améliorations suivantes :  
  
-   Les tables temporaires et les variables de table peuvent être mises en cache. La mise en cache permet aux opérations de création et de suppression des objets temporaires de s'exécuter très rapidement et réduit la contention d'allocation des pages.  
  
-   Le protocole d'accès aux pages d'allocation est amélioré. Cela réduit le nombre de verrous de mise à jour utilisés.  
  
-   La surcharge d'enregistrement pour **tempdb** est réduite. Cela réduit la consommation de bande passante au niveau des E/S de disque sur le fichier journal **tempdb** .  
  
-   L’algorithme d’allocation des pages mixtes dans **tempdb** est amélioré.  
  
### <a name="moving-the-tempdb-data-and-log-files"></a>Déplacement des fichiers de données et des journaux de tempdb  
 Pour déplacer les fichiers de données et les fichiers journaux **tempdb** , consultez [déplacer des bases de données système](system-databases.md).  
  
### <a name="database-options"></a>Options de base de données  
 Le tableau suivant répertorie la valeur par défaut de chaque option de base de données de la base de données **tempdb** et indique si l’option peut être modifiée. Pour afficher les valeurs actuelles de ces options, utilisez l'affichage catalogue [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Option de base de données|Valeur par défaut|Peut être modifiée|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Yes|  
|ANSI_NULL_DEFAULT|OFF|Yes|  
|ANSI_NULLS|OFF|Yes|  
|ANSI_PADDING|OFF|Yes|  
|ANSI_WARNINGS|OFF|Yes|  
|ARITHABORT|OFF|Yes|  
|AUTO_CLOSE|OFF|No|  
|AUTO_CREATE_STATISTICS|ACTIVÉ|Yes|  
|AUTO_SHRINK|OFF|No|  
|AUTO_UPDATE_STATISTICS|ACTIVÉ|Yes|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Yes|  
|CHANGE_TRACKING|OFF|Non|  
|CONCAT_NULL_YIELDS_NULL|OFF|Yes|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Yes|  
|CURSOR_DEFAULT|GLOBAL|Oui|  
|Options de disponibilité de base de données|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|Non<br /><br /> Non<br /><br /> Non |  
|DATE_CORRELATION_OPTIMIZATION|OFF|Yes|  
|DB_CHAINING|ACTIVÉ|Non|  
|ENCRYPTION|OFF|Non|  
|NUMERIC_ROUNDABORT|OFF|Oui|  
|PAGE_VERIFY|CHECKSUM pour les nouvelles installations de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NONE pour les mises à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Yes|  
|PARAMETERIZATION|SIMPLE|Oui|  
|QUOTED_IDENTIFIER|OFF|Oui|  
|READ_COMMITTED_SNAPSHOT|OFF|Non|  
|RECOVERY|SIMPLE|Non|  
|RECURSIVE_TRIGGERS|OFF|Oui|  
|Options de Service Broker|ENABLE_BROKER|Oui|  
|TRUSTWORTHY|OFF|No|  
  
 Pour obtenir une description de ces options de base de données, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
## <a name="restrictions"></a>Restrictions  
 Les opérations suivantes ne peuvent pas être effectuées sur la base de données **tempdb** :  
  
-   Ajout de groupes de fichiers  
  
-   Sauvegarde ou restauration de la base de données  
  
-   Modification du classement. Le classement par défaut est le classement du serveur.  
  
-   Modification du propriétaire de la base de données. **tempdb** appartient à **sa**.  
  
-   Création d'un instantané de base de données  
  
-   Suppression de la base de données  
  
-   Suppression de l’utilisateur **invité** de la base de données.  
  
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
  
## <a name="related-content"></a>Contenu associé  
 [Option SORT_IN_TEMPDB pour les index](../indexes/indexes.md)  
  
 [Bases de données système](system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Déplacer des fichiers de bases de données](move-database-files.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de tempdb dans SQL Server 2005](https://chresandro.wordpress.com/2014/09/29/working-with-tempdb-in-sql-server-2005/)  
  
  
