---
title: Sauvegarder et restaurer des bases de données répliquées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- backups [SQL Server replication]
- administering replication, restoring
- backing up replicated databases
- backups [SQL Server replication], about backups
- restoring replicated databases [SQL Server replication]
- recovery [SQL Server replication], about recovery
- restoring databases [SQL Server], replicated databases
- backing up databases [SQL Server], replicated databases
- restoring [SQL Server replication], about restoring
- recovery [SQL Server replication]
- replication [SQL Server], administering
- distribution databases [SQL Server replication], backing up
- restoring [SQL Server replication]
- administering replication, backing up
ms.assetid: 04588807-21e7-4bbe-9727-b72f692cffa7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e91505bacf67f7f4628bd1b3f6b2cc78a6bc4c3a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068730"
---
# <a name="back-up-and-restore-replicated-databases"></a>Sauvegarder et restaurer des bases de données répliquées
  Les bases de données répliquées nécessitent une attention toute particulière en ce qui concerne la sauvegarde et la restauration de données. Cette rubrique fournit des informations introductives et des liens vers des informations plus complètes sur les stratégies de sauvegarde et de restauration pour chaque type de réplication.  
  
 La réplication prend en charge la restauration de bases de données répliquées sur le même serveur et dans la même base de données à partir desquels la sauvegarde a été créée. Si vous restaurez une sauvegarde d'une base de données répliquée sur un autre serveur ou dans une autre base de données, les paramètres de réplication ne peuvent pas être conservés. Dans ce cas, vous devez recréer toutes les publications et tous les abonnements après la restauration des sauvegardes.  
  
> [!NOTE]  
>  Il est possible de restaurer une base de données répliquée vers un serveur mis en veille à condition que la copie des journaux de transaction soit utilisée. Pour plus d’informations, consultez [Copie des journaux de transaction et réplication &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).  
  
 Les bases de données répliquées et leurs bases de données système associées doivent être sauvegardées régulièrement. Sauvegardez les bases de données suivantes :  
  
-   La base de données de publication au niveau du serveur de publication  
  
-   La base de données de distribution au niveau du serveur de distribution  
  
-   La base de données d'abonnement sur chaque Abonné  
  
-   Bases de données système **master** et **msdb** sur le serveur de publication, sur le serveur de distribution et sur tous les Abonnés. Il est recommandé de sauvegarder ces bases de données en même temps, ainsi que la base de données de réplication appropriée. Par exemple, sauvegardez les bases de données **master** et **msdb** au niveau du serveur de publication en même temps que la base de données de publication. Si la base de données de publication est restaurée, vérifiez que les bases de données **master** et **msdb** sont cohérentes avec la base de données de publication en termes de configuration de la réplication et de paramètres.  
  
 Si vous effectuez des sauvegardes régulières des journaux, toutes les modifications liées à la réplication doivent être capturées dans les sauvegardes des journaux. Si vous n'effectuez pas de sauvegardes de fichiers journaux, une sauvegarde doit être effectuée chaque fois qu'une modification portant sur un paramètre de réplication a lieu. Pour en savoir plus, voir [Common Actions Requiring an Updated Backup](common-actions-requiring-an-updated-backup.md).  
  
## <a name="backup-and-restore-strategies"></a>Stratégies de sauvegarde et de restauration  
 Les stratégies de sauvegarde et de restauration de chaque nœud d'une topologie de réplication sont différentes selon le type de réplication utilisé. Pour plus d'informations sur les stratégies de sauvegarde et de restauration pour chaque type de réplication, consultez les rubriques suivantes :  
  
-   [Stratégies de sauvegarde et de restauration de la réplication transactionnelle et d’instantané](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)  
  
-   [Stratégies de sauvegarde et de restauration de la réplication de fusion](strategies-for-backing-up-and-restoring-merge-replication.md)  
  
 Quelle que soit votre stratégie de récupération, conservez toujours dans un endroit sûr un script à jour de vos paramètres de réplication. En cas de panne sur un serveur, ou si vous avez besoin de créer un environnement de test, vous pouvez modifier ce script en changeant des références de nom de serveur et l'utiliser pour recréer vos paramètres de réplication. Outre vos paramètres de réplication courants, prévoyez d'intégrer dans un script l'activation et la désactivation de la réplication. Pour plus d'informations sur les scripts d'objets de réplication, consultez [Scripting Replication](../scripting-replication.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration des bases de données SQL Server](../../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Best Practices for Replication Administration](best-practices-for-replication-administration.md)  
  
  
