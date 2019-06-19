---
title: Sauvegardes de la fin du journal (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], tail of log
- transaction log backups [SQL Server], tail-log backups
- NO_TRUNCATE clause
- backups [SQL Server], log backups
- tail-log backups
- backups [SQL Server], tail-log backups
ms.assetid: 313ddaf6-ec54-4a81-a104-7ffa9533ca58
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6da8f9de22f1b3191d6fba1918e8c05a64d062f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62920671"
---
# <a name="tail-log-backups-sql-server"></a>Sauvegardes de la fin du journal (SQL Server)
  Cette rubrique s'applique uniquement à la sauvegarde et la restauration des bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] employant le mode de récupération complète ou le mode de récupération utilisant les journaux de transactions.  
  
 Une *sauvegarde de la fin du journal* capture tous les enregistrements de journal qui n’ont pas encore été sauvegardés (la *fin du journal*) pour empêcher toute perte de travail et préserver la continuité de la séquence de journaux de transactions consécutifs. Avant de pouvoir récupérer une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aux date et heure les plus récentes, vous devez sauvegarder la fin de son journal des transactions. La sauvegarde de la fin du journal est la dernière sauvegarde intéressante dans le plan de récupération de la base de données.  
  
> [!NOTE]  
>  Les scénarios de restauration ne nécessitent pas tous une sauvegarde de la fin du journal. Vous n'avez pas besoin d'une sauvegarde de la fin du journal si le point de récupération est contenu dans une sauvegarde de journal antérieure. En outre, une sauvegarde de la fin du journal est inutile si vous déplacez ou remplacez (par écrasement) la base de données et ne souhaitez pas la restaurer à un point donné après la sauvegarde la plus récente.  
  
 
  
##  <a name="TailLogScenarios"></a> Scénarios qui nécessitent une sauvegarde de la fin du journal  
 Nous vous recommandons d'effectuer une sauvegarde de la fin du journal dans les scénarios suivants :  
  
-   Si la base de données est en ligne et que vous envisagez d'effectuer une opération de restauration de la base de données, commencez par sauvegarder la fin du journal. Pour éviter une erreur de base de données en ligne, vous devez utiliser ... l’option WITH NORECOVERY de l’instruction [BACKUP](/sql/t-sql/statements/backup-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
-   Si une base de données est hors connexion, ne démarre pas et que vous devez restaurer la base de données, sauvegardez d'abord la fin du journal. Comme il est exclu d'effectuer une transaction à ce stade, l'utilisation de WITH NORECOVERY est facultative.  
  
-   Si une base de données est endommagée, essayez d'effectuer une sauvegarde de la fin du journal à l'aide de l'option WITH CONTINUE_AFTER_ERROR de l'instruction BACKUP.  
  
     Sur une base de données endommagée, la sauvegarde de la fin du journal n'aboutit que si les fichiers journaux ne sont pas endommagés, la base de données est en mesure de prendre en charge cette sauvegarde de la fin du journal, et la base de données ne contient pas de modifications journalisées en bloc. Si une sauvegarde de la fin du journal ne peut pas être créée, toutes les transactions validées après la dernière sauvegarde de fichier journal sont perdues.  
  
 Le tableau suivant résume les options BACKUP NORECOVERY et CONTINUE_AFTER_ERROR.  
  
|Option BACKUP LOG|Commentaires|  
|-----------------------|--------------|  
|NORECOVERY|Utilisez NORECOVERY chaque fois que vous envisagez de poursuivre une opération de restauration sur la base de données. NORECOVERY fait passer la base de données en état de restauration. Ceci permet d'éviter des modifications dans la base de données après la sauvegarde de la fin du journal.  Le journal est tronqué sauf si l'option NO_TRUNCATE ou COPY_ONLY est aussi spécifiée.<br /><br /> **\*\* Important \* \***  nous recommandons d’éviter d’utiliser NO_TRUNCATE, sauf si la base de données est endommagée.|  
|CONTINUE_AFTER_ERROR|Utilisez CONTINUE_AFTER_ERROR uniquement si vous sauvegardez la fin d'une base de données endommagée.<br /><br /> Remarque : Si vous sauvegardez la fin du journal sur une base de données endommagée, certaines métadonnées capturées normalement dans des sauvegardes de journaux sont parfois indisponibles. Pour plus d’informations, consultez [Sauvegardes de la fin du journal avec des métadonnées de sauvegarde incomplètes](#IncompleteMetadata), plus loin dans cette rubrique.|  
  
##  <a name="IncompleteMetadata"></a> Sauvegardes de la fin du journal avec des métadonnées de sauvegarde incomplètes  
 Les sauvegardes de la fin du journal capturent la fin du journal même si la base de données est hors connexion ou endommagée, ou s'il y manque des fichiers de données. Cela peut aboutir à des métadonnées incomplètes à partir des commandes d'informations de restauration et de **msdb**. Mais seules les métadonnées sont incomplètes ; le journal capturé est complet et exploitable.  
  
 Si une sauvegarde de la fin du journal contient des métadonnées incomplètes, dans la table [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) , **has_incomplete_metadata** a la valeur **1**. De plus, dans le résultat de [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql), **HasIncompleteMetadata** a la valeur **1**.  
  
 Si les métadonnées d’une sauvegarde de la fin du journal sont incomplètes, la plupart des informations relatives aux groupes de fichiers sont absentes de la table [backupfilegroup](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) au moment de la sauvegarde de la fin du journal. La plupart des colonnes de la table **backupfilegroup** ont la valeur NULL ; seules les colonnes suivantes ont une signification :  
  
-   **backup_set_id**  
  
-   **filegroup_id**  
  
-   **type**  
  
-   **type_desc**  
  
-   **is_readonly**  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 Pour créer une sauvegarde de la fin du journal, consultez [Sauvegarder le journal des transactions lorsque la base de données est endommagée &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md).  
  
 Pour restaurer une sauvegarde du journal des transactions, consultez [Restaurer une sauvegarde du journal des transactions &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Sauvegarde et restauration des bases de données SQL Server](back-up-and-restore-of-sql-server-databases.md)   
 [Sauvegardes de type copie seule &#40;SQL Server&#41;](copy-only-backups-sql-server.md)   
 [Sauvegardes des journaux de transactions &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](apply-transaction-log-backups-sql-server.md)  
  
  
