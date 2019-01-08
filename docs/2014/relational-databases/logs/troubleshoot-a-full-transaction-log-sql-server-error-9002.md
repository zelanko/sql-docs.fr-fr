---
title: Résoudre les problèmes liés à un journal des transactions saturé (erreur SQL Server 9002) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], full
- troubleshooting [SQL Server], full transaction log
- 9002 (Database Engine error)
- transaction logs [SQL Server], truncation
- backing up transaction logs [SQL Server], full logs
- transaction logs [SQL Server], full log
- full transaction logs [SQL Server]
ms.assetid: 0f23aa84-475d-40df-bed3-c923f8c1b520
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2c0dc1566693ad8d8c86d7efe47403248788b076
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52759511"
---
# <a name="troubleshoot-a-full-transaction-log-sql-server-error-9002"></a>Résoudre les problèmes liés à un journal des transactions saturé (erreur SQL Server 9002)
  Cette rubrique décrit les réactions possibles et émet quelques suggestions qui vous aideront à éviter cette situation dans le futur. Quand le journal des transactions est saturé, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] émet une erreur 9002. Le journal peut être renseigné lorsque la base de données est en ligne ou en cours de récupération. Si le journal se remplit tandis que la base de données est en ligne, cette dernière reste en ligne et peut uniquement être lue mais pas mise à jour. Si le journal se remplit en cours de récupération, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] marque la base de données comme RESOURCE PENDING. Dans les deux cas, une intervention de l'utilisateur est nécessaire pour libérer de l'espace disque.  
  
## <a name="responding-to-a-full-transaction-log"></a>Réagir à un journal des transactions complet  
 La réponse adéquate à un journal des transactions saturé dépend en partie de la ou des conditions qui ont motivé le remplissage du journal. Pour découvrir les raisons qui empêchent de tronquer le journal dans une situation donnée, utilisez les colonnes **log_reuse_wait** et **log_reuse_wait_desc** de l’affichage catalogue **sys.database**. Pour plus d’informations, consultez [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql). Pour obtenir une description des facteurs susceptibles de retarder la troncation du journal, consultez [Journal des transactions &#40;SQL Server&#41;](the-transaction-log-sql-server.md).  
  
> [!IMPORTANT]  
>  Si la base de données dans laquelle se trouvait récupération s’est produite l’erreur 9002, après avoir résolu le problème, récupérer la base de données à l’aide de ALTER DATABASE *database_name* SET ONLINE.  
  
 D'autres solutions possibles en cas de saturation du journal des transactions sont les suivantes :  
  
-   Sauvegarde du journal.  
  
-   Libération de l'espace disque pour que le journal puisse croître automatiquement.  
  
-   Déplacement du fichier journal vers une unité dotée d'un espace disque suffisant.  
  
-   Augmentation de la taille du fichier journal.  
  
-   Ajout d'un fichier journal sur un autre disque.  
  
-   Achèvement ou suppression d'une transaction longue.  
  
 Ces solutions sont abordées dans les sections qui suivent. Optez pour une solution adaptée à votre situation.  
  
### <a name="backing-up-the-log"></a>Sauvegarde du journal  
 Si vous travaillez en mode de restauration complète ou en mode de récupération utilisant les journaux de transactions et si vous n'avez pas sauvegardé récemment le journal des transactions, la création d'une sauvegarde est ce qui empêche la troncation du journal. Si le journal n’a jamais été sauvegardé, vous devez créer deux sauvegardes du journal pour autoriser le [!INCLUDE[ssDE](../../includes/ssde-md.md)] à le tronquer à l’endroit exact de la dernière sauvegarde. Le fait de tronquer le journal permet de libérer de l'espace pour les nouveaux enregistrements de ce dernier. Pour empêcher le journal de se remplir à nouveau, effectuez les sauvegardes régulièrement.  
  
 **Pour créer une sauvegarde du journal des transactions**  
  
> [!IMPORTANT]  
>  Si la base de données est endommagée, consultez [Sauvegardes de la fin du journal &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md).  
  
-   [Sauvegarder un journal des transactions &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)  
  
### <a name="freeing-disk-space"></a>Libération d’espace disque  
 Vous pouvez libérer de l'espace sur le disque où est stocké le fichier journal des transactions de la base de données en supprimant ou en déplaçant d'autres fichiers. Ceci permet au système de récupération d'augmenter automatiquement la taille du fichier journal.  
  
### <a name="moving-the-log-file-to-a-different-disk"></a>Déplacement du fichier journal vers un autre disque  
 Si vous ne pouvez pas libérer suffisamment d'espace disque sur le lecteur où le fichier journal se trouve actuellement, essayez de déplacer ce fichier sur une autre unité disposant d'espace suffisant.  
  
> [!IMPORTANT]  
>  Les fichiers journaux ne doivent jamais être placés sur des systèmes de fichiers compressés.  
  
 **Pour déplacer un fichier journal**  
  
-   [Déplacer des fichiers de bases de données](../databases/move-database-files.md)  
  
### <a name="increasing-the-size-of-a-log-file"></a>Augmentation de la taille d'un fichier journal  
 Si le disque du journal dispose d'espace libre, vous pouvez augmenter la taille du fichier journal. La taille maximale pour les fichiers journaux est de deux téraoctets (To) par fichier journal.  
  
 **Pour augmenter la taille de fichier**  
  
 Si la fonctionnalité de croissance automatique est désactivée, que la base de données est en ligne et que l'espace disque disponible est suffisant, effectuez l'une des opérations suivantes :  
  
-   Augmentez manuellement la taille du fichier pour générer un seul incrément de croissance.  
  
-   Activez la croissance automatique à l'aide de l'instruction ALTER DATABASE pour définir un incrément de croissance différent de zéro pour l'option FILEGROWTH.  
  
> [!NOTE]  
>  Dans les deux cas, si la limite de taille actuelle est atteinte, augmentez la valeur MAXSIZE.  
  
### <a name="adding-a-log-file-on-a-different-disk"></a>Ajout d'un fichier journal sur un autre disque  
 Ajoutez un nouveau fichier journal à la base de données d'un autre disque doté d'un espace suffisant à l'aide de l'instruction ALTER DATABASE <nom_base_de_données> ADD LOG FILE.  
  
 **Pour ajouter un fichier journal**  
  
-   [Ajouter des fichiers de données ou journaux à une base de données](../databases/add-data-or-log-files-to-a-database.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [Gérer la taille du fichier journal des transactions](manage-the-size-of-the-transaction-log-file.md)   
 [Sauvegardes des journaux de transactions &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md)   
 [sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql)  
  
  
