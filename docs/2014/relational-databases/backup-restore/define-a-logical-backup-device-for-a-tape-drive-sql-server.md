---
title: Définir une unité de sauvegarde logique pour un lecteur de bande (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- tape backup devices, creating
ms.assetid: 66f36e1d-0287-4fac-8a51-71f9f0d7ad5b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 14a96a44967c41b185d3196c9d6577f67547e77a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62877920"
---
# <a name="define-a-logical-backup-device-for-a-tape-drive-sql-server"></a>Définir une unité de sauvegarde logique pour un lecteur de bande (SQL Server)
  Cette rubrique explique comment définir une unité de sauvegarde logique pour un lecteur de bande dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Une unité logique est un nom défini par l'utilisateur qui désigne une unité de sauvegarde physique spécifique (un fichier de disque ou un lecteur de bande).  L'initialisation de l'unité physique se produit ultérieurement, lorsqu'une sauvegarde est écrite sur l'unité de sauvegarde.  
  
> [!NOTE]  
>  La prise en charge des unités de sauvegarde sur bande sera supprimée dans une prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour définir une unité de sauvegarde logique pour un lecteur de bande, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Le ou les lecteurs de bande doivent être pris en charge par le système d'exploitation Microsoft Windows.  
  
-   Le périphérique à bandes doit être connecté physiquement à l'ordinateur qui exécute une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La sauvegarde sur des bandes à distance n'est pas prise en charge.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **diskadmin** .  
  
 Requiert l'autorisation d'écrire sur le disque.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a>Pour définir une unité de sauvegarde logique pour un lecteur de bande  
  
1.  Après vous être connecté à l’instance appropriée du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l’Explorateur d’objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Objets serveur**, puis cliquez avec le bouton droit sur **Unités de sauvegarde**.  
  
3.  Cliquez sur **Nouvelle unité de sauvegarde**, pour ouvrir la boîte de dialogue **Unité de sauvegarde** .  
  
4.  Entrez un nom d'unité.  
  
5.  Pour la destination, cliquez sur **Bande** puis sélectionnez un lecteur de bande qui n'est pas déjà associé à une autre unité de sauvegarde. Si aucun lecteur de bande de ce type n'est disponible, l'option **Bande** est inactive.  
  
6.  Pour définir la nouvelle unité, cliquez sur **OK**.  
  
 Pour procéder à une sauvegarde sur cette nouvelle unité, ajoutez-la au champ **Sauvegarde sur** dans la boîte de dialogue **Sauvegarder la base de données** (**Général**). Pour plus d’informations, consultez [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a>Pour définir une unité de sauvegarde logique pour un lecteur de bande  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) pour définir une unité de sauvegarde logique pour une bande. Cet exemple ajoute l'unité de sauvegarde sur bande appelée `tapedump1`, dont le nom physique est `\\.\tape0`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)   
 [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [Définir une unité de sauvegarde logique pour un fichier de disque &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
