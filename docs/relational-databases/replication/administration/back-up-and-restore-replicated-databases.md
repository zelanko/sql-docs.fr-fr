---
title: "Sauvegarder et restaurer des bases de donn&#233;es r&#233;pliqu&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sauvegardes [réplication SQL Server]"
  - "administration de la réplication, restauration"
  - "sauvegarde des bases de données répliquées"
  - "sauvegardes [réplication SQL Server], à propos des sauvegardes"
  - "restauration des bases de données répliquées [réplication SQL Server]"
  - "récupération [réplication SQL Server], à propos de la récupération"
  - "restauration des bases de données [SQL Server], bases de données répliquées"
  - "sauvegarde des bases de données [SQL Server], bases de données répliquées"
  - "restauration [réplication SQL Server], à propos de la restauration"
  - "récupération [réplication SQL Server]"
  - "réplication [SQL Server], administration"
  - "bases de données de distribution [réplication SQL Server], sauvegarde"
  - "restauration [réplication SQL Server]"
  - "administration de la réplication, sauvegarde"
ms.assetid: 04588807-21e7-4bbe-9727-b72f692cffa7
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Sauvegarder et restaurer des bases de donn&#233;es r&#233;pliqu&#233;es
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Les bases de données répliquées nécessitent une attention toute particulière en ce qui concerne la sauvegarde et la restauration de données. Cette rubrique fournit des informations introductives et des liens vers des informations plus complètes sur les stratégies de sauvegarde et de restauration pour chaque type de réplication.  
  
 La réplication prend en charge la restauration de bases de données répliquées sur le même serveur et dans la même base de données à partir desquels la sauvegarde a été créée. Si vous restaurez une sauvegarde d'une base de données répliquée sur un autre serveur ou dans une autre base de données, les paramètres de réplication ne peuvent pas être conservés. Dans ce cas, vous devez recréer toutes les publications et tous les abonnements après la restauration des sauvegardes.  
  
> [!NOTE]  
>  Il est possible de restaurer une base de données répliquée vers un serveur mis en veille à condition que la copie des journaux de transaction soit utilisée. Pour plus d’informations, consultez [l’envoi de journaux et la réplication & #40 ; SQL Server & #41 ;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).  
  
 Les bases de données répliquées et leurs bases de données système associées doivent être sauvegardées régulièrement. Sauvegardez les bases de données suivantes :  
  
-   La base de données de publication au niveau du serveur de publication  
  
-   La base de données de distribution au niveau du serveur de distribution  
  
-   La base de données d'abonnement sur chaque Abonné  
  
-   Bases de données système **master** et **msdb** sur le serveur de publication, sur le serveur de distribution et sur tous les Abonnés. Il est recommandé de sauvegarder ces bases de données en même temps, ainsi que la base de données de réplication appropriée. Par exemple, sauvegardez les bases de données **master** et **msdb** au niveau du serveur de publication en même temps que la base de données de publication. Si la base de données de publication est restaurée, vérifiez que les bases de données **master** et **msdb** sont cohérentes avec la base de données de publication en termes de configuration de la réplication et de paramètres.  
  
 Si vous effectuez des sauvegardes régulières des journaux, toutes les modifications liées à la réplication doivent être capturées dans les sauvegardes des journaux. Si vous n'effectuez pas de sauvegardes de fichiers journaux, une sauvegarde doit être effectuée chaque fois qu'une modification portant sur un paramètre de réplication a lieu. Pour plus d’informations, consultez [Common Actions Requiring an Updated Backup](../../../relational-databases/replication/administration/common-actions-requiring-an-updated-backup.md).  
  
## Stratégies de sauvegarde et de restauration  
 Les stratégies de sauvegarde et de restauration de chaque nœud d'une topologie de réplication sont différentes selon le type de réplication utilisé. Pour plus d'informations sur les stratégies de sauvegarde et de restauration pour chaque type de réplication, consultez les rubriques suivantes :  
  
-   [Stratégies de sauvegarde et de restauration de la réplication transactionnelle et d'instantané](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)  
  
-   [Stratégies de sauvegarde et de restauration de la réplication de fusion](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-merge-replication.md)  
  
 Quelle que soit votre stratégie de récupération, conservez toujours dans un endroit sûr un script à jour de vos paramètres de réplication. En cas de panne sur un serveur, ou si vous avez besoin de créer un environnement de test, vous pouvez modifier ce script en changeant des références de nom de serveur et l'utiliser pour recréer vos paramètres de réplication. Outre vos paramètres de réplication courants, prévoyez d'intégrer dans un script l'activation et la désactivation de la réplication. Pour plus d'informations sur les scripts d'objets de réplication, consultez [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
## Voir aussi  
 [Sauvegarde et restauration des bases de données SQL Server](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Méthodes conseillées pour l'administration de la réplication](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)  
  
  