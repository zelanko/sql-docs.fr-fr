---
title: Afficher les propriétés et le contenu d’une unité de sauvegarde logique (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- displaying backup content
- viewing backup content
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
- backing up databases [SQL Server], properties
- displaying backup properties
- backup devices [SQL Server], viewing information
- viewing backup properties
- database backups [SQL Server], properties
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 87a925658b9c41efcef8cb0f857e7cdac19cdd7c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37309989"
---
# <a name="view-the-properties-and-contents-of-a-logical-backup-device-sql-server"></a>Afficher les propriétés et le contenu d'une unité de sauvegarde logique (SQL Server)
  Cette rubrique explique comment afficher les propriétés et le contenu d'une unité de sauvegarde logique dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher les propriétés et le contenu d'une unité de sauvegarde logique, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d’informations sur la sécurité, consultez [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql).  
  
####  <a name="Permissions"></a> Permissions  
 Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures, l'obtention d'informations relatives à un jeu de sauvegarde ou une unité de sauvegarde requiert l'autorisation CREATE DATABASE. Pour plus d’informations, consultez [GRANT – octroi d’autorisations de base de données &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a>Pour afficher les propriétés et le contenu d'une unité de sauvegarde logique  
  
1.  Après la connexion à l'instance appropriée du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Objets serveur**, puis **Unités de sauvegarde**.  
  
3.  Cliquez sur l’unité, puis cliquez avec le bouton droit sur **Propriétés**; la boîte de dialogue **Unité de sauvegarde** s’affiche.  
  
4.  La page **Général** affiche le nom de l'unité et la destination, soit un périphérique à bandes, soit un chemin de fichier.  
  
5.  Dans le volet **Sélectionner une page** , cliquez sur **Contenu du support**.  
  
6.  Le volet de droite affiche les volets de propriétés suivants :  
  
    -   **Support**  
  
         Informations sur la séquence du support (le numéro de la séquence du support et de la famille, et l'identificateur du miroir, s'il existe) et la date et l'heure de la création du support.  
  
    -   **Support de sauvegarde**  
  
         Informations sur le support de sauvegarde : nom et description du support, s'ils existent, et nombre de familles dans ce support.  
  
7.  La grille **Jeux de sauvegarde** affiche des informations sur le contenu du support de sauvegarde.  
  
> [!NOTE]  
>  Pour plus d’informations, consultez [Page Contenu du support](backup-device-media-contents-page.md).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a>Pour afficher les propriétés et le contenu d'une unité de sauvegarde logique  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Utilisez l'instruction [RESTORE LABELONLY](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) . Cet exemple retourne des informations sur l'unité de sauvegarde logique `AdvWrks2008R2Backup` .  
  
```tsql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql)   
 [backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql)   
 [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)   
 [backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql)   
 [backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md)  
  
  
