---
title: Suppression de la mise en miroir de bases de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- stopping database mirroring [SQL Server]
- removing database mirroring [SQL Server]
ms.assetid: 40c72091-8f03-4037-8b55-5e95309fe145
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6a1d3bcb83efcd6488ca1e85302aafdc7f7a8b55
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171350"
---
# <a name="removing-database-mirroring-sql-server"></a>Suppression d'une mise en miroir des bases de données (SQL Server)
  Le propriétaire de la base de données peut arrêter manuellement une session de mise en miroir de base de données à tout moment et sur n'importe quel serveur partenaire.  
  
## <a name="impact-of-removing-mirroring"></a>Impact de la suppression d'une mise en mémoire  
 Lorsqu'une mise en miroir est supprimée, les événements suivants se produisent :  
  
-   Les relations qui existaient éventuellement entre les serveurs partenaires d'une part et entre chaque serveur partenaire et le serveur témoin d'autre part sont rompues définitivement.  
  
     Si les serveurs partenaires communiquaient entre eux lorsque la session a été arrêtée, leur relation est immédiatement rompue sur les deux ordinateurs. Si les serveurs partenaires ne communiquaient pas (la base de données présentait alors l'état DISCONNECTED au moment de l'arrêt), la relation est rompue immédiatement sur le serveur partenaire à partir duquel la mise en miroir a été arrêtée ; lorsque l'autre serveur partenaire essaie de se reconnecter, il découvre que la session de mise en miroir est terminée.  
  
-   Les informations sur la session de mise en miroir sont supprimées, ce qui n'est pas le cas lorsqu'une session est suspendue. La mise en miroir est supprimée de la base de données principale et de la base de données miroir. Dans **sys.databases**, la colonne **mirroring_state** et toutes les autres colonnes de mise en miroir indiquent la valeur NULL. Pour plus d’informations, consultez [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).  
  
-   L'instance de chaque serveur partenaire conserve une copie distincte de la base de données.  
  
-   La base de données miroir conserve l’état RESTORING (consultez la colonne **state** de **sys.databases**), car elle a été créée par le biais de RESTORE WITH NORECOVERY. À ce stade, vous pouvez soit supprimer l'ancienne base de données miroir, soit la restaurer avec WITH RECOVERY. Après avoir récupéré la base de données, vous constatez qu'elle est différente de l'ancienne base de données principale. Cela s'explique par le fait que l'opération de récupération débute un nouveau branchement de récupération.  
  
> [!NOTE]  
>  Pour continuer la mise en miroir après l'arrêt d'une session, vous devez établir une nouvelle session de mise en miroir de base de données. Si vous créez une sauvegarde de fichier journal après l'arrêt de la mise en miroir, vous devez l'appliquer à la base de données miroir avant de redémarrer la mise en miroir.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour supprimer une mise en miroir de bases de données**  
  
-   [Supprimer une mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
 **Pour démarrer la mise en miroir de bases de données**  
  
-   [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)  
  

  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Suspension et reprise de la mise en miroir de bases de données &#40;SQL Server&#41;](pausing-and-resuming-database-mirroring-sql-server.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
