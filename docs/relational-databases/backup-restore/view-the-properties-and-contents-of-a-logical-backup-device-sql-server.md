---
title: "Afficher les propri&#233;t&#233;s et le contenu d&#39;une unit&#233; de sauvegarde logique (SQL&#160;Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "affichage du contenu de la sauvegarde"
  - "visualisation du contenu de la sauvegarde"
  - "sauvegardes de bases de données [SQL Server], affichage du contenu"
  - "sauvegarde de bases de données [SQL Server], affichage du contenu"
  - "sauvegarde de bases de données [SQL Server], propriétés"
  - "affichage des propriétés de sauvegarde"
  - "unités de sauvegarde [SQL Server], affichage des informations"
  - "visualisation des propriétés de sauvegarde"
  - "sauvegardes de bases de données [SQL Server], propriétés"
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Afficher les propri&#233;t&#233;s et le contenu d&#39;une unit&#233; de sauvegarde logique (SQL&#160;Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment afficher les propriétés et le contenu d'une unité de sauvegarde logique dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher les propriétés et le contenu d'une unité de sauvegarde logique, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d’informations sur la sécurité, consultez [RESTORE LABELONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md).  
  
####  <a name="Permissions"></a> Autorisations  
 Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures, l'obtention d'informations relatives à un jeu de sauvegarde ou une unité de sauvegarde requiert l'autorisation CREATE DATABASE. Pour plus d’informations, consultez [GRANT – octroi d’autorisations de base de données &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour afficher les propriétés et le contenu d'une unité de sauvegarde logique  
  
1.  Après la connexion à l'instance appropriée du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Objets serveur**, puis **Unités de sauvegarde**.  
  
3.  Cliquez sur l’unité, puis cliquez avec le bouton droit sur **Propriétés** ; la boîte de dialogue **Unité de sauvegarde** s’affiche.  
  
4.  La page **Général** affiche le nom de l'unité et la destination, soit un périphérique à bandes, soit un chemin de fichier.  
  
5.  Dans le volet **Sélectionner une page** , cliquez sur **Contenu du support**.  
  
6.  Le volet de droite affiche les volets de propriétés suivants :  
  
    -   **Support**  
  
         Informations sur la séquence du support (le numéro de la séquence du support et de la famille, et l'identificateur du miroir, s'il existe) et la date et l'heure de la création du support.  
  
    -   **Support de sauvegarde**  
  
         Informations sur le support de sauvegarde : nom et description du support, s'ils existent, et nombre de familles dans ce support.  
  
7.  La grille **Jeux de sauvegarde** affiche des informations sur le contenu du support de sauvegarde.  
  
> [!NOTE]  
>  Pour plus d’informations, consultez [Page Contenu du support](../../relational-databases/backup-restore/backup-device-media-contents-page.md).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour afficher les propriétés et le contenu d'une unité de sauvegarde logique  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Utilisez l'instruction [RESTORE LABELONLY](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md) . Cet exemple retourne des informations sur l'unité de sauvegarde logique `AdvWrks2008R2Backup`.  
  
```tsql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## Voir aussi  
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [Unités de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
  