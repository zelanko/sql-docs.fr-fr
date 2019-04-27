---
title: Réduire le temps mort pour les bases de données miroir lors de la mise à niveau des Instances de serveur | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server, rolling upgrade of mirrored databases
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
ms.assetid: 0e73bd23-497d-42f1-9e81-8d5314bcd597
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 857e18b1b956d3d8c9d2fc4c5692dbf022bf85fe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62754276"
---
# <a name="minimize-downtime-for-mirrored-databases-when-upgrading-server-instances"></a>Réduire le temps d'indisponibilité des bases de données mises en miroir lors de la mise à niveau d'instances de serveur
  Lors de la mise à niveau des instances de serveur [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez réduire les temps d’arrêt pour chaque base de données mise en miroir à un seul basculement manuel en effectuant une mise à niveau séquentielle, appelé un *mise à niveau propagée*. Une mise à niveau propagée est un processus en plusieurs étapes qui, dans sa forme la plus simple, consiste à mettre à niveau l'instance de serveur qui agit actuellement en tant que serveur miroir dans une session de mise en miroir, puis à basculer manuellement la base de données mise en miroir, à mettre à niveau l'ancien serveur principal et à reprendre la mise en miroir. En pratique, le processus exact dépend du mode d'opération, du nombre et de la disposition de sessions de mise en miroir qui s'exécutent sur les instances de serveur que vous mettez à niveau.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’exécution d’une mise à niveau propagée pour installer un service pack ou le correctif logiciel, consultez [installer un Service Pack sur un système avec un temps mort Minimal pour les bases de données mise en miroir](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md).  
  
 **Préparation recommandée (meilleures pratiques)**  
  
 Avant de commencer une mise à niveau propagée, nous recommandons d'effectuer les opérations suivantes :  
  
1.  Procédez à un essai de basculement manuel sur au moins une de vos sessions de mise en miroir :  
  
    -   [Basculer manuellement une session de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Basculer manuellement une session de mise en miroir de bases de données &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md).  
  
    > [!NOTE]  
    >  Pour plus d’informations sur le fonctionnement du basculement manuel, consultez [Basculement de rôle durant une session de mise en miroir de bases de données &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).  
  
2.  Protégez vos données :  
  
    1.  Effectuez une sauvegarde complète de chaque base de données principale :  
  
         [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
    2.  Exécutez la commande [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) sur chaque base de données principale.  
  
 **Étapes d’une mise à niveau propagée**  
  
 Les étapes spécifiques d'une mise à niveau propagée dépendent du mode d'opération de la configuration de mise en miroir. Toutefois, les étapes de base sont les mêmes.  
  
> [!NOTE]  
>  Pour plus d’informations sur les modes d’opération, consultez [Modes de fonctionnement de la mise en miroir de bases de données](database-mirroring-operating-modes.md).  
  
 L'organigramme suivant illustre les étapes de base d'une mise à niveau propagée pour chaque mode d'opération. Les procédures correspondantes sont décrites après l'illustration.  
  
 ![Organigramme montrant les étapes d’une mise à niveau propagée](../media/dbm-rolling-upgrade.gif "Organigramme montrant les étapes d’une mise à niveau propagée")  
  
> [!IMPORTANT]  
>  Une instance de serveur peut remplir différents rôles de mise en miroir (serveur principal, serveur miroir ou témoin) dans des sessions de mise en miroir simultanées. Dans ce cas, vous devez adapter le processus de mise à niveau propagée de base en conséquence. Pour plus d’informations, consultez [Basculement de rôle durant une session de mise en miroir de bases de données &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a>Pour faire passer une session du mode hautes performances en mode haute sécurité  
  
1.  Si une session de mise en miroir s'exécute en mode hautes performances, avant d'effectuer une mise à niveau propagée, convertissez le mode d'opération en mode haute sécurité sans basculement automatique.  
  
    > [!IMPORTANT]  
    >  Si le serveur miroir est géographiquement distant du serveur principal, une mise à niveau propagée peut être inappropriée.  
  
    -   Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: Modifier le **mode d’opération** option **haute sécurité sans basculement automatique (synchrone)** à l’aide de la [Page mise en miroir](../../relational-databases/databases/database-properties-mirroring-page.md) de la **base de données Propriétés** boîte de dialogue. Pour plus d’informations sur la façon d’accéder à cette page, consultez [Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md).  
  
    -   Dans [!INCLUDE[tsql](../../includes/tsql-md.md)]: Sécurité des transactions la valeur FULL. Pour plus d’informations, consultez [Modifier la sécurité des transactions dans une session de mise en miroir de bases de données &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).  
  
### <a name="to-remove-a-witness-from-a-session"></a>Pour supprimer un témoin d'une session  
  
1.  Si une session de mise en miroir fait intervenir un témoin, nous vous recommandons de le supprimer avant d'effectuer une mise à niveau propagée. Sinon, lorsque l'instance de serveur miroir est mise à niveau, la disponibilité de la base de données dépend du témoin qui reste connecté à l'instance de serveur principal. Après avoir supprimé un témoin, vous pouvez le mettre à niveau à tout moment pendant le processus de mise à niveau propagée sans risquer un temps mort de la base de données.  
  
    > [!NOTE]  
    >  Pour plus d’informations, consultez [Quorum : effets d’un témoin sur la disponibilité de la base de données &#40;Mise en miroir de bases de données&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).  
  
    -   [Supprimer le témoin d’une session de mise en miroir de bases de données &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-perform-the-rolling-upgrade"></a>Pour effectuer la mise à niveau propagée  
  
1.  Pour réduire le temps mort, nous recommandons ce qui suit : Démarrer la mise à niveau propagée en mettant à jour tout serveur partenaire de mise en miroir est actuellement le serveur miroir dans toutes ses sessions de mise en miroir. Vous pourriez devoir mettre à jour plusieurs instances de serveur à ce stade.  
  
    > [!NOTE]  
    >  Un témoin peut être mis à niveau à tout moment au cours du processus de mise à niveau propagée. Par exemple, si une instance de serveur est un serveur miroir dans la session 1 et un témoin dans la session 2, vous pouvez la mettre à niveau dès maintenant.  
  
     L'instance de serveur à mettre à niveau en premier dépend de la configuration actuelle de vos sessions de mise en miroir, à savoir :  
  
    -   Si une instance de serveur est déjà le serveur miroir dans toutes ses sessions de mise en miroir, mettez-la à niveau vers la nouvelle version.  
  
    -   Si toutes vos instances de serveur correspondent actuellement au serveur principal dans toutes les sessions de mise en miroir, sélectionnez une instance de serveur à mettre niveau en premier. Ensuite, basculez manuellement chacune de ses bases de données principales et mettez à niveau cette instance de serveur.  
  
     Après sa mise à niveau, une instance de serveur réintègre automatiquement chacune de ses sessions de mise en miroir.  
  
2.  Attendez la synchronisation de chaque session de mise en miroir dont l'instance de serveur miroir vient d'être mise à niveau. Puis, connectez-vous à l'instance de serveur principal, et basculez manuellement la session. Lors du basculement, l'instance de serveur mise à niveau devient le serveur principal pour cette session, et l'ancien serveur principal devient le serveur miroir.  
  
     Le but de cette étape est de permettre à une autre instance de serveur de devenir le serveur miroir dans chaque session de mise en miroir dans laquelle elle est un serveur partenaire.  
  
     **Restrictions après le basculement sur une instance de serveur mise à niveau.**  
  
     Après un basculement à partir d'une instance de serveur antérieure vers une instance de serveur [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , la session de base de données est interrompue. Elle ne peut pas reprendre tant que l'autre serveur partenaire n'a pas été mis à niveau. Toutefois, le serveur principal accepte encore des connexions et autorise l'accès aux données et des modifications sur la base de données principale.  
  
    > [!NOTE]  
    >  L'établissement d'une nouvelle session de mise en miroir requiert que toutes les instances de serveur exécutent la même version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Après avoir basculé, nous vous recommandons d’exécuter le [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) commande theprincipal de base de données.  
  
4.  Mettez à niveau chaque instance de serveur qui est désormais le serveur miroir dans toutes les sessions de mise en miroir dans lesquelles elle est un serveur partenaire. Vous pourriez devoir mettre à jour plusieurs serveurs à ce stade.  
  
    > [!IMPORTANT]  
    >  Dans une configuration de mise en miroir complexe, certaines instances de serveur pourraient encore être le serveur principal d'origine dans une ou plusieurs sessions de mise en miroir. Répétez les étapes 2 à 4 pour ces instances de serveur jusqu’à ce que toutes les instances concernées soient mises à niveau.  
  
5.  Reprenez la session de mise en miroir.  
  
    > [!NOTE]  
    >  Le basculement automatique ne fonctionne pas tant que le témoin n'a pas été mis à niveau et de nouveau ajouté à la session de mise en miroir.  
  
6.  Mettez à niveau toute instance de serveur restante qui est le témoin dans toutes ses sessions de mise en miroir. Une fois qu'un témoin mis à niveau a réintégré une session de mise en miroir, il est de nouveau possible d'effectuer un basculement automatique. Vous pourriez devoir mettre à jour plusieurs serveurs à ce stade.  
  
### <a name="to-return-a-session-to-high-performance-mode"></a>Pour rétablir le mode hautes performances d'une session  
  
1.  Rétablissez éventuellement le mode hautes performances en appliquant l'une des méthodes suivantes :  
  
    -   Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: Modifier le **mode d’opération** option **haute performance (asynchrone)** à l’aide de la [Page mise en miroir](../../relational-databases/databases/database-properties-mirroring-page.md) du **propriétés de base de données**boîte de dialogue.  
  
    -   Dans [!INCLUDE[tsql](../../includes/tsql-md.md)]: Utilisez [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)pour définir la sécurité des transactions désactivée (OFF).  
  
### <a name="to-add-a-witness-back-into-a-mirroring-session"></a>Pour ajouter de nouveau un témoin dans une session de mise en miroir  
  
1.  En mode haute sécurité, rétablissez éventuellement le témoin sur chaque session de mise en miroir.  
  
     **Pour réintégrer un témoin**  
  
    -   [Ajouter ou remplacer un témoin de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [Ajouter un témoin de mise en miroir de bases de données à l’aide de l’authentification Windows &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Afficher l’état d’une base de données mise en miroir &#40;SQL Server Management Studio&#41;](view-the-state-of-a-mirrored-database-sql-server-management-studio.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Installer un Service Pack sur un système avec un temps mort Minimal pour les bases de données miroir](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md)   
 [Basculement de rôle durant une session de mise en miroir de bases de données &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)   
 [Forcer le service dans une session de mise en miroir de bases de données &#40;Transact-SQL&#41;](force-service-in-a-database-mirroring-session-transact-sql.md)   
 [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Modes de fonctionnement de la mise en miroir de bases de données](database-mirroring-operating-modes.md)  
  
  
