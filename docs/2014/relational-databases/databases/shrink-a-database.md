---
title: Réduire une base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkdatabase.f1
helpviewer_keywords:
- shrinking databases
- databases [SQL Server], shrinking
- decreasing database size
- database shrinking [SQL Server]
- reducing database size
ms.assetid: 83afbf74-fd50-4c39-831c-b1f473a50620
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 21f58cd6991b760edeefb81c37e02c617f8e09cd
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52784022"
---
# <a name="shrink-a-database"></a>Réduire une base de données
  Cette rubrique explique comment réduire une base de données au moyen de l'Explorateur d'objets dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 La réduction des fichiers de données permet de récupérer de l'espace en déplaçant des pages de données de la fin du fichier vers un espace inoccupé plus proche de l'avant du fichier. Quand une quantité d'espace libre suffisante est créée à la fin du fichier, des pages de données à la fin du fichier peuvent être désallouées et retournées au système de fichiers.  
  

  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   La base de données ne peut pas être réduite à une taille inférieure à la taille minimale de la base de données. La taille minimale d'une base de données correspond à la taille spécifiée lors de sa création ou lors de la dernière définition de taille explicite lors d'une opération de modification de taille, notamment au moyen de DBCC SHRINKFILE. Par exemple, la plus petite taille que pourrait avoir une base de données de 10 Mo initialement et de 100 Mo avant réduction, même si toutes les données qu'elle contient ont été supprimées, est de 10 Mo après réduction.  
  
-   Vous ne pouvez pas réduire la taille d'une base de données en cours de sauvegarde. Inversement, vous ne pouvez pas sauvegarder une base de données alors qu'elle fait l'objet d'une opération de réduction.  
  
-   DBCC SHRINKDATABASE échoue lorsqu'il rencontre un index columnstore optimisé en mémoire xVelocity. Le travail effectué avant de rencontrer l'index columnstore réussit, de sorte que la base de données peut être plus petite. Pour exécuter DBCC SHRINKDATABASE, désactivez tous les index columnstore avant d'exécuter DBCC SHRINKDATABASE, puis reconstruisez les index.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Pour visualiser la quantité d'espace actuellement libre (non allouée) dans la base de données. Pour plus d'informations, consultez [Afficher les informations sur l'espace occupé par les données et par le journal d'une base de données](display-data-and-log-space-information-for-a-database.md)  
  
-   Prenez en compte les informations suivantes lorsque vous envisagez de réduire une base de données :  
  
    -   Une opération de réduction de taille de fichier est plus efficace après l'exécution d'une opération qui crée une grande quantité d'espace inutilisé, telle qu'une troncature de table ou une suppression de table.  
  
    -   Un certain espace libre doit exister pour les opérations quotidiennes courantes pour la plupart des bases de données. Si vous réduisez plusieurs fois la taille d'une base de données et que vous constatez que la taille augmente de nouveau, cela indique que l'espace qui a été réduit est nécessaire pour les opérations courantes. Dans ce cas, la réduction de la taille de la base de données ne sert à rien.  
  
    -   Une opération de réduction ne conserve pas l'état de fragmentation des index de la base de données, et augmente généralement la fragmentation. Il s'agit là d'une raison supplémentaire pour ne pas réduire la taille de la base de données de manière répétitive.  
  
    -   Sauf en cas de besoin précis, n'attribuez pas la valeur ON à l'option de base de données AUTO_SHRINK.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l’appartenance au rôle de serveur fixe **sysadmin** ou au rôle de base de données fixe **db_owner** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-shrink-a-database"></a>Pour réduire une base de données  
  
1.  Dans **l’Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], puis développez-la.  
  
2.  Développez **Bases de données**, puis cliquez avec le bouton droit sur la base de données à réduire.  
  
3.  Pointez sur **Tâches**puis sur **Réduire**, puis cliquez sur **Base de données**.  
  
     **Sauvegarde de la base de données**  
     Affiche le nom de la base de données sélectionnée.  
  
     **Espace actuellement alloué**  
     Affiche l'espace total, utilisé et non utilisé, pour la base de données sélectionnée.  
  
     **Espace libre disponible**  
     Affiche la totalité de l'espace disponible dans les fichiers de données et les fichiers journaux de la base de données sélectionnée.  
  
     **Réorganiser les fichiers avant de libérer de l'espace inutilisé**  
     Activer cette option équivaut à exécuter DBCC SHRINKDATABASE en spécifiant une option de pourcentage cible. Désactiver cette option équivaut à exécuter DBCC SHRINKDATABASE avec l'option TRUNCATEONLY. Par défaut, cette option n'est pas sélectionnée à l'ouverture de la boîte de dialogue. Si cette option est sélectionnée, l'utilisateur doit spécifier une option de pourcentage cible.  
  
     **Espace libre maximal dans les fichiers après réduction**  
     Entrez le pourcentage maximal d'espace disponible à conserver dans les fichiers de base de données après la réduction de la base de données. Les valeurs autorisées sont comprises entre 0 et 99.  
  
4.  Cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-shrink-a-database"></a>Pour réduire une base de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple suivant utilise [DBCC SHRINKDATABASE](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) pour diminuer la taille des fichiers de données et journaux de la base de données utilisateur `UserDB` pour obtenir `10` % d'espace libre dans la base de données.  
  
 [!code-sql[DBCC#DBCC_SHRINKDB1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkdb1)]  
  
##  <a name="FollowUp"></a> Suivi : Après avoir réduit une base de données  
 Les données qui sont déplacées pour réduire un fichier peuvent être dispersées à n'importe quel emplacement disponible dans le fichier. Cela provoque la fragmentation de l'index et peut ralentir les performances des requêtes qui recherchent une plage de l'index. Pour éliminer la fragmentation, reconstruisez les index dans le fichier après réduction.  
  
## <a name="see-also"></a>Voir aussi  
 [Réduire un fichier](shrink-a-file.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)   
 [DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql)   
 [DBCC SHRINKFILE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql)   
 [Groupes de fichiers et fichiers de base de données](database-files-and-filegroups.md)  
  
  
