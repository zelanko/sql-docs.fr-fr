---
title: "Initialiser un abonnement transactionnel &#224; partir d&#39;une sauvegarde (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/29/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "initialisation manuelle des abonnements [réplication SQL Server]"
  - "abonnements [réplication SQL Server], initialisation"
  - "initialisation d’abonnements [réplication SQL Server], sans instantanés"
  - "réplication transactionnelle, sauvegarde et restauration"
  - "sauvegardes [réplication SQL Server], réplication transactionnelle"
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Initialiser un abonnement transactionnel &#224; partir d&#39;une sauvegarde (programmation Transact-SQL de la r&#233;plication)
  Bien qu'un abonnement à une publication transactionnelle soit en général initialisé à l'aide d'un instantané, il est possible d'initialiser un abonnement à partir d'une sauvegarde en utilisant les procédures stockées de réplication. Pour plus d’informations, consultez [initialiser un abonnement transactionnel sans instantané](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
### Pour initialiser un Abonné transactionnel à partir d'une sauvegarde  
  
1.  Pour une publication existante, assurez-vous que la publication prend en charge la capacité d’initialiser à partir de la sauvegarde en exécutant [sp_helppublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) sur la base de données de publication de l’éditeur. Notez la valeur de **allow_initialize_from_backup** dans le résultat défini.  
  
    -   Si la valeur est **1**, la publication prend en charge cette fonctionnalité.  
  
    -   Si la valeur est **0**, exécutez [sp_changepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) sur la base de données de publication de l’éditeur. Spécifiez la valeur **allow_initialize_from_backup** pour **@property** et la valeur **true** pour **@value**.  
  
2.  Pour une nouvelle publication, exécutez [sp_addpublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) sur la base de données de publication de l’éditeur. Spécifiez la valeur **true** pour **allow_initialize_from_backup**. Pour plus d'informations, voir [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
    > [!WARNING]  
    >  Pour éviter de manquer des données de l’abonné, lorsque vous utilisez **sp_addpublication** avec `@allow_initialize_from_backup = N'true'`, utilisez toujours `@immediate_sync = N'true'`.  
  
3.  Créer une sauvegarde de la base de données de publication à l’aide de la [sauvegarde & #40 ; Transact-SQL & #41 ;](../../t-sql/statements/backup-transact-sql.md) instruction.  
  
4.  Restaurez la sauvegarde sur l’abonné à l’aide de le [restauration & #40 ; Transact-SQL & #41 ;](../Topic/RESTORE%20\(Transact-SQL\).md) instruction.  
  
5.  Le serveur de publication sur la base de données de publication, exécutez la procédure stockée [sp_addsubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Spécifiez les paramètres suivants :  
  
    -   **@sync_type** -valeur **initialisation avec sauvegarde**.  
  
    -   **@backupdevicetype** -le type d’unité de sauvegarde : **logique** (par défaut), **disque**, ou **bande**.  
  
    -   **@backupdevicename** -l’unité de sauvegarde logique ou physique à utiliser pour la restauration.  
  
         Pour une unité logique, spécifiez le nom de l’unité de sauvegarde spécifié lorsque **sp_addumpdevice** a été utilisé pour créer le périphérique.  
  
         Pour une unité physique, spécifiez un chemin d'accès complet et un nom de fichier, tels que `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\BACKUP\Mybackup.dat'` ou `TAPE = '\\.\TAPE0'` ;  
  
    -   (Facultatif) **@password** -un mot de passe a été fourni lors de la création du jeu de sauvegarde.  
  
    -   (Facultatif) **@mediapassword** -un mot de passe qui a été fournie lorsque le support de sauvegarde a été mis en forme.  
  
    -   (Facultatif) **@fileidhint** -identificateur de jeu de sauvegarde à restaurer. Par exemple, la spécification **1** indique la premier jeu de sauvegarde sur le support de sauvegarde et **2** indique le deuxième jeu de sauvegarde.  
  
    -   (Facultatif pour les périphériques à bandes) **@unload** -spécifier la valeur **1** (par défaut) si la bande doit être déchargée du lecteur une fois la restauration terminée et **0** si elle ne doit pas être déchargé.  
  
6.  (Facultatif) Pour un abonnement par extraction de données, exécutez [sp_addpullsubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md) et [sp_addpullsubscription_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) sur la base de données d’abonnement de l’abonné. Pour plus d’informations, consultez [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
7.  (Facultatif) Démarrez l'Agent de distribution. Pour plus d'informations, consultez [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) ou [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
## Voir aussi  
 [Copier des bases de données avec la sauvegarde et la restauration](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [Sauvegarde et restauration des bases de données SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  