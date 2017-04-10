---
title: "Restaurer une sauvegarde &#224; partir d&#39;une unit&#233; (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "restauration des bases de données [SQL Server], restaurations de périphériques"
  - "unités de sauvegarde [SQL Server], restauration à partir de"
  - "restaurations de bases de données [SQL Server], restaurations de périphériques"
  - "unités [SQL Server]"
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# Restaurer une sauvegarde &#224; partir d&#39;une unit&#233; (SQL Server)
  Cette rubrique explique comment restaurer une sauvegarde à partir d'une unité dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Pour plus d’informations sur la sauvegarde SQL Server dans le service de stockage d’objets blob Microsoft Azure, consultez [Sauvegarde et restauration SQL Server avec le service de stockage d’objets blob Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour restaurer une sauvegarde à partir d'une unité, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Si la base de données restaurée n'existe pas, l'utilisateur doit posséder les autorisations CREATE DATABASE afin de pouvoir exécuter RESTORE. Si la base de données existe, les autorisations RESTORE reviennent par défaut aux membres des rôles serveur fixes **sysadmin** et **dbcreator** et au propriétaire (**dbo**) de la base de données (pour l’option FROM DATABASE_SNAPSHOT, la base de données existe toujours).  
  
 Les autorisations RESTORE sont attribuées aux rôles dont les informations d'appartenance sont toujours immédiatement accessibles à partir du serveur. Étant donné que l’appartenance au rôle de base de données fixe ne peut être contrôlée que quand la base de données est accessible et non endommagée, ce qui n’est pas toujours le cas quand RESTORE est exécuté, les membres du rôle de base de données fixe **db_owner** ne détiennent pas d’autorisations RESTORE.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour restaurer une sauvegarde à partir d'une unité  
  
1.  Après la connexion à l'instance appropriée du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Bases de données**puis, selon la base de données, sélectionnez une base de données utilisateur ou développez **Bases de données système** et sélectionnez une base de données système.  
  
3.  Cliquez avec le bouton droit sur la base de données, pointez sur **Tâches**, puis cliquez sur **Restaurer**.  
  
4.  Cliquez sur le type de restauration de votre choix (**Base de données**, **Fichiers et groupes de fichiers** ou **Journal des transactions**). Cette opération permet d'ouvrir la boîte de dialogue de restauration correspondante.  
  
5.  Dans la page **Général** , dans la section **Source de restauration** , cliquez sur **À partir de l'unité**.  
  
6.  Cliquez sur le bouton d'exploration de la zone de texte **À partir de l'unité** afin d'ouvrir la boîte de dialogue **Spécifier la sauvegarde** .  
  
7.  Dans la zone de texte **Support de sauvegarde** , sélectionnez **Unité de sauvegarde**, puis cliquez sur le bouton **Ajouter** pour ouvrir la boîte de dialogue **Sélectionner l'unité de sauvegarde** .  
  
8.  Dans la zone de texte **Unité de sauvegarde** , sélectionnez l'unité à utiliser pour la restauration.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour restaurer une sauvegarde à partir d'une unité  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Dans l'instruction [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) , spécifiez une unité de sauvegarde logique ou physique à utiliser pour l'opération de sauvegarde. Cet exemple effectue une restauration à partir d’un fichier disque qui a le nom physique `Z:\SQLServerBackups\AdventureWorks2012.bak`.  
  
```tsql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## Voir aussi  
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20VERIFYONLY%20\(Transact-SQL\).md)   
 [Restaurer une sauvegarde de base de données en mode de récupération simple &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)   
 [Restaurer une sauvegarde de base de données à l’aide de SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)   
 [Restaurer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-differential-database-backup-sql-server.md)   
 [Restaurer une base de données à un nouvel emplacement &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Sauvegarder des fichiers et des groupes de fichiers &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md)   
 [Sauvegarder un journal des transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)   
 [Créer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
  