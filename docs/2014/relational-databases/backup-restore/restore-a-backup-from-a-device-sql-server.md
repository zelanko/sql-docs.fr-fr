---
title: Restaurer une sauvegarde à partir d’une unité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], device restores
- backup devices [SQL Server], restoring from
- database restores [SQL Server], device restores
- devices [SQL Server]
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 50d7f7b8e255aea470a1065df669c0cc3169a8dd
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84957283"
---
# <a name="restore-a-backup-from-a-device-sql-server"></a>Restaurer une sauvegarde à partir d'une unité (SQL Server)
  Cette rubrique explique comment restaurer une sauvegarde à partir d'une unité dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Pour plus d’informations sur la sauvegarde de SQL Server dans le service de stockage d’objets BLOB Azure, consultez, [SQL Server sauvegarde et restauration avec le service de stockage d’objets BLOB Azure](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour restaurer une sauvegarde à partir d'une unité, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Si la base de données restaurée n'existe pas, l'utilisateur doit posséder les autorisations CREATE DATABASE afin de pouvoir exécuter RESTORE. Si la base de données existe, les autorisations RESTORE reviennent par défaut aux membres des rôles serveur fixe **sysadmin** et **dbcreator** et au propriétaire (**dbo**) de la base de données (pour l’option FROM DATABASE_SNAPSHOT, la base de données existe toujours).  
  
 Les autorisations RESTORE sont attribuées aux rôles dont les informations d'appartenance sont toujours immédiatement accessibles à partir du serveur. Étant donné que l’appartenance au rôle de base de données fixe ne peut être contrôlée que quand la base de données est accessible et non endommagée, ce qui n’est pas toujours le cas lorsque RESTORE est exécuté, les membres du rôle de base de données fixe **db_owner** ne détiennent pas d’autorisations RESTORE.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-restore-a-backup-from-a-device"></a>Pour restaurer une sauvegarde à partir d'une unité  
  
1.  Après vous être connecté à l’instance appropriée du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)], dans l’Explorateur d’objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Bases de données**puis, selon la base de données, sélectionnez une base de données utilisateur ou développez **Bases de données système** et sélectionnez une base de données système.  
  
3.  Cliquez avec le bouton droit sur la base de données, pointez sur **Tâches**, puis cliquez sur **Restaurer**.  
  
4.  Cliquez sur le type de restauration de votre choix (**Base de données**, **Fichiers et groupes de fichiers**ou **Journal des transactions**). Cette opération permet d'ouvrir la boîte de dialogue de restauration correspondante.  
  
5.  Dans la page **Général** , dans la section **Source de restauration** , cliquez sur **À partir de l'unité**.  
  
6.  Cliquez sur le bouton d'exploration de la zone de texte **À partir de l'unité** afin d'ouvrir la boîte de dialogue **Spécifier la sauvegarde** .  
  
7.  Dans la zone de texte **Support de sauvegarde** , sélectionnez **Unité de sauvegarde**, puis cliquez sur le bouton **Ajouter** pour ouvrir la boîte de dialogue **Sélectionner l'unité de sauvegarde** .  
  
8.  Dans la zone de texte **Unité de sauvegarde** , sélectionnez l'unité à utiliser pour la restauration.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-restore-a-backup-from-a-device"></a>Pour restaurer une sauvegarde à partir d'une unité  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Dans l'instruction [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) , spécifiez une unité de sauvegarde logique ou physique à utiliser pour l'opération de sauvegarde. Cet exemple effectue une restauration à partir d’un fichier disque qui a le nom physique `Z:\SQLServerBackups\AdventureWorks2012.bak`.  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## <a name="see-also"></a> Voir aussi  
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)   
 [Restaurer une sauvegarde de base de données en mode de récupération simple &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)   
 [Restaurer une sauvegarde de base de données &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)   
 [Restaurer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md)   
 [Restaurer une base de données à un nouvel emplacement &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md)   
 [Sauvegarder des fichiers et des groupes de fichiers &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)   
 [Sauvegarder un journal des transactions &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)   
 [Créer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
  
