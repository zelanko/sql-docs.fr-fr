---
title: "Définir une unité de sauvegarde logique pour un lecteur de disque (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
ms.assetid: 86331d43-c738-4523-ae3d-7d6700348ed1
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bd550f0690603132f53452f064af24e05426398a
ms.lasthandoff: 04/11/2017

---
# <a name="define-a-logical-backup-device-for-a-disk-file-sql-server"></a>Définir une unité de sauvegarde logique pour un fichier de disque (SQL Server)
  Cette rubrique explique comment définir une unité de sauvegarde logique pour un fichier de disque dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Une unité logique est un nom défini par l'utilisateur qui désigne une unité de sauvegarde physique spécifique (un fichier de disque ou un lecteur de bande).  L'initialisation de l'unité physique se produit ultérieurement, lorsqu'une sauvegarde est écrite sur l'unité de sauvegarde.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour définir une unité de sauvegarde logique pour un fichier de disque, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Le nom d'unité logique doit être unique parmi toutes les unités de sauvegarde logiques résidant sur l'instance de serveur. Pour afficher les noms d’unités logiques existantes, interrogez l’affichage catalogue [sys.backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md) .  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   À titre de recommandation, il est préférable que le disque de sauvegarde ne soit pas le même que les disques de données ou de journal de la base de données. Ce paramètre est primordial pour garantir l'accès aux sauvegardes en cas d'échec du disque de données ou de journal.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **diskadmin** .  
  
 Requiert l'autorisation d'écrire sur le disque.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-define-a-logical-backup-device-for-a-disk-file"></a>Pour définir une unité de sauvegarde logique pour un fichier de disque  
  
1.  Après la connexion à l'instance appropriée du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Objets serveur**, puis cliquez avec le bouton droit sur **Unités de sauvegarde**.  
  
3.  Cliquez sur **Nouvelle unité de sauvegarde**. La boîte de dialogue **Unité de sauvegarde** s'ouvre.  
  
4.  Entrez un nom d'unité.  
  
5.  Pour la destination, cliquez sur **Fichier** et spécifiez le chemin d'accès complet du fichier.  
  
6.  Pour définir la nouvelle unité, cliquez sur **OK**.  
  
 Pour procéder à une sauvegarde sur cette nouvelle unité, ajoutez-la au champ **Sauvegarde sur** dans la boîte de dialogue **Sauvegarder la base de données** (**Général**). Pour plus d’informations, consultez [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-define-a-logical-backup-for-a-disk-file"></a>Pour définir une unité logique pour un fichier de disque  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md) pour définir une unité de sauvegarde logique pour un fichier de disque. Cet exemple ajoute l'unité de sauvegarde sur disque appelée `mydiskdump`, dont le nom physique est `c:\dump\dump1.bak`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Unités de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sys.backup_devices &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Définir une unité de sauvegarde logique pour un lecteur de bande &#40;SQL Server&#41;](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
