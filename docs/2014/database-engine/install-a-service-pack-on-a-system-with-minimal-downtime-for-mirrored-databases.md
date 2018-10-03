---
title: Installer un Service Pack sur un système avec un temps mort Minimal pour les bases de données miroir | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- hotfixes [SQL Server]
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
- service packs [SQL Server]
- upgrading mirrored database systems
- upgrading SQL Server, mirrored databases
ms.assetid: bdc63142-027d-4ead-9d3e-147331387ef5
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6f654292e1d756cd655766851e0bc056e41ce3f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053009"
---
# <a name="install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases"></a>Installer un Service Pack sur un système avec un temps mort minimal pour les bases de données mises en miroir
  Cette rubrique décrit comment réduire le temps mort pour les bases de données mises en miroir lorsque vous installez des Service Packs et des correctifs. Ce processus implique la mise à niveau séquentielle des instances de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] qui participent à la mise en miroir de bases de données. Cette forme de mise à jour, ce qui est appelé un *mise à jour propagée*, réduit le temps mort que pour un seul basculement. Notez que pour les sessions en mode hautes performances dans lequel le serveur miroir est géographiquement distant du serveur principal, une mise à jour propagée peut être inappropriée.  
  
 Une mise à jour propagée est un processus en plusieurs étapes impliquant les différentes étapes suivantes :  
  
-   Protéger vos données.  
  
-   Si la session inclut un témoin, nous vous recommandons de le supprimer. Sinon, lorsque l'instance de serveur miroir est mise à jour, la disponibilité de la base de données dépend du témoin qui reste connecté à l'instance de serveur principal. Après avoir supprimé un témoin, vous pouvez le mettre à jour à tout moment pendant le processus de mise à jour propagée sans risquer un temps mort de la base de données.  
  
    > [!NOTE]  
    >  Pour plus d’informations, consultez [Quorum : effets d’un témoin sur la disponibilité de la base de données &#40;mise en miroir de bases de données&#41;](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).  
  
-   Si une session s'exécute en mode hautes performances, convertissez le mode d'opération en mode haute sécurité.  
  
-   Mettre à jour chaque instance de serveur impliquée dans la mise en miroir de bases de données. Une mise à jour propagée implique la mise à niveau de l'instance de serveur qui est actuellement le serveur miroir, le basculement manuel de chacune de ses bases de données mises en miroir et la mise à niveau de l'instance de serveur qui était auparavant le serveur principal (et qui est désormais le nouveau serveur miroir). Vous devrez à ce stade, reprendre la mise en miroir.  
  
    > [!NOTE]  
    >  Avant de démarrer une mise à jour propagée, nous vous recommandons d'effectuer un basculement manuel d'essai sur au moins une de vos sessions de mise en miroir.  
  
-   Rétablir si nécessaire le mode hautes performances.  
  
-   Faire revenir le témoin dans la session de mise en miroir, si nécessaire.  
  
 Les procédures de ces étapes sont décrites ici.  
  
> [!IMPORTANT]  
>  Une instance de serveur peut remplir différents rôles de mise en miroir (serveur principal, serveur miroir ou témoin) dans des sessions de mise en miroir simultanées. Dans ce cas, vous devez adapter le processus de mise à jour propagée de base en conséquence.  
  
### <a name="to-protect-your-data-before-an-update-a-best-practice"></a>Pour protéger vos données avant une mise à jour (meilleure pratique)  
  
1.  Effectuez une sauvegarde complète de chaque base de données principale.  
  
     **Pour sauvegarder une base de données**  
  
    -   [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
2.  Exécutez la commande [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) sur chaque base de données principale.  
  
### <a name="to-remove-a-witness-from-a-session"></a>Pour supprimer un témoin d'une session  
  
1.  Si une session de mise en miroir fait intervenir un témoin, nous vous recommandons de le supprimer avant d'effectuer une mise à jour propagée.  
  
     **Pour supprimer le témoin**  
  
    -   [Supprimer le témoin d’une session de mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a>Pour faire passer une session du mode hautes performances en mode haute sécurité  
  
1.  Si une session de mise en miroir s'exécute en mode hautes performances, avant d'effectuer une mise à jour propagée, convertissez le mode d'opération en mode haute sécurité sans basculement automatique. Appliquez l'une des méthodes suivantes :  
  
    -   Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] : affectez la valeur **Haute sécurité sans basculement automatique (synchrone)** à l’option **Mode d’opération** dans la [page Mise en miroir](../relational-databases/databases/database-properties-mirroring-page.md) de la boîte de dialogue **Propriétés de la base de données**. Pour plus d’informations sur la façon d’accéder à cette page, consultez [Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md).  
  
    -   Dans [!INCLUDE[tsql](../includes/tsql-md.md)] : attribuez à la sécurité des transactions la valeur FULL. Pour plus d’informations, consultez [Modifier la sécurité des transactions dans une session de mise en miroir de bases de données &#40;Transact-SQL&#41;](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).  
  
### <a name="to-perform-the-rolling-update"></a>Pour effectuer la mise à jour propagée  
  
1.  Pour réduire le temps mort, nous vous recommandons d'appliquer la procédure suivante : démarrez la mise à jour propagée en mettant à jour tout serveur partenaire de mise en miroir qui fait actuellement office de serveur miroir dans toutes ses sessions de mise en miroir. Vous pourriez devoir mettre à jour plusieurs instances de serveur à ce stade.  
  
    > [!NOTE]  
    >  Un témoin peut être mis à jour à tout moment au cours du processus de mise à jour propagée. Par exemple, si une instance de serveur est un serveur miroir dans la session 1 et un témoin dans la session 2, vous pouvez la mettre à jour dès maintenant.  
  
     L'instance de serveur à mettre à jour en premier dépend de la configuration actuelle de vos sessions de mise en miroir, à savoir :  
  
    -   Si une instance de serveur est déjà le serveur miroir dans toutes ses sessions de mise en miroir, installez le Service Pack ou le correctif sur cette instance de serveur.  
  
    -   Si toutes vos instances de serveur sont actuellement le serveur principal dans toutes les sessions de mise en miroir, sélectionnez une instance de serveur à mettre à jour en premier. Puis, faites basculer manuellement chacune de ses bases de données principales et mettez à jour cette instance de serveur en installant le Service Pack ou le correctif.  
  
     Après sa mise à jour, une instance de serveur réintègre automatiquement chacune de ses sessions de mise en miroir.  
  
     **Pour effectuer un basculement manuel**  
  
    -   [Basculer manuellement une session de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Basculer manuellement une session de mise en miroir de bases de données &#40;Transact-SQL&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md).  
  
     Pour plus d’informations sur le fonctionnement du basculement manuel, consultez [Basculement de rôle durant une session de mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).  
  
2.  Attendez la synchronisation de chaque session de mise en miroir dont l'instance de serveur miroir vient d'être mise à jour. Puis, connectez-vous à l'instance de serveur principal, et basculez manuellement la session. Lors du basculement, l'instance de serveur mise à jour devient le serveur principal pour cette session, et l'ancien serveur principal devient le serveur miroir.  
  
     Le but de cette étape est de permettre à une autre instance de serveur de devenir le serveur miroir dans chaque session de mise en miroir dans laquelle elle est un serveur partenaire.  
  
3.  Après avoir effectué le basculement, nous vous recommandons d'exécuter la commande [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) sur la base de données principale.  
  
4.  Installez le Service Pack ou le correctif sur chaque instance de serveur qui est désormais le serveur miroir dans toutes les sessions de mise en miroir dans lesquelles il est un serveur partenaire. Vous pourriez devoir mettre à jour plusieurs serveurs à ce stade.  
  
    > [!IMPORTANT]  
    >  Dans une configuration de mise en miroir complexe, certaines instances de serveur pourraient encore être le serveur principal d'origine dans une ou plusieurs sessions de mise en miroir. Répétez les étapes 2 à 4 pour ces instances de serveur jusqu'à ce que toutes les instances concernées soient mises à jour.  
  
5.  Reprenez la session de mise en miroir.  
  
    > [!NOTE]  
    >  Le basculement automatique ne fonctionne pas tant que le témoin n'a pas été mis à jour.  
  
6.  Installez les Service Packs ou les correctifs sur une instance de serveur restante qui est le témoin dans toutes ses sessions de mise en miroir. Une fois qu'un témoin mis à jour a réintégré une session de mise en miroir, il est de nouveau possible d'effectuer un basculement automatique. Vous pourriez devoir mettre à jour plusieurs serveurs à ce stade.  
  
### <a name="to-return-a-session-to-high-performance-mode"></a>Pour rétablir le mode hautes performances d'une session  
  
1.  Rétablissez éventuellement le mode hautes performances en appliquant l'une des méthodes suivantes :  
  
    -   Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: affectez la valeur **Haute performance (asynchrone)** à l’option **Mode d’opération** dans la [page Mise en miroir](../relational-databases/databases/database-properties-mirroring-page.md) de la boîte de dialogue **Propriétés de la base de données** .  
  
    -   Dans [!INCLUDE[tsql](../includes/tsql-md.md)]: utilisez [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) pour définir la sécurité des transactions désactivée (OFF).  
  
### <a name="to-return-a-witness-to-a-mirroring-session"></a>Pour réintégrer un témoin dans une session de mise en miroir  
  
1.  En mode haute sécurité, rétablissez éventuellement le témoin sur chaque session de mise en miroir.  
  
     **Pour rétablir le témoin**  
  
    -   [Ajouter ou remplacer un témoin de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [Ajouter un témoin de mise en miroir de bases de données à l’aide de l’authentification Windows &#40;Transact-SQL&#41;](database-mirroring/add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md)   
 [Modes de fonctionnement de la mise en miroir de bases de données](database-mirroring/database-mirroring-operating-modes.md)   
 [Basculement de rôle durant une session de mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)   
 [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Afficher l’état d’une base de données mise en miroir &#40;SQL Server Management Studio&#41;](database-mirroring/view-the-state-of-a-mirrored-database-sql-server-management-studio.md)  
  
  
