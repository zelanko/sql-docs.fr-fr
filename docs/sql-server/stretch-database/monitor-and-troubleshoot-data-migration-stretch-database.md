---
title: "Surveillance et résolution des problèmes de migration de données (Stretch Database) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/14/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, monitoring
- monitoring Stretch Database
ms.assetid: 06950858-8c02-4ec6-9c59-42b787316a2d
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 91c10b51a3fec9ccc96c3aa23100abdf2a60ba81
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="monitor-and-troubleshoot-data-migration-stretch-database"></a>Surveillance et résolution des problèmes de migration de données (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Pour surveiller la migration des données dans Stretch Database Monitor, sélectionnez **Tâches | Stretch | Monitor** pour à une base de données dans SQL Server Management Studio.  
  
## <a name="check-the-status-of-data-migration-in-the-stretch-database-monitor"></a>Vérification de l’état de la migration des données dans Stretch Database Monitor  
 Sélectionnez **Tâches | Stretch | Monitor** pour une base de données dans SQL Server Management Studio pour ouvrir Stretch Database Monitor et surveiller la migration des données.  
  
-   La partie supérieure de l’écran contient des informations générales sur la base de données SQL Server Stretch ainsi que sur la base de données Azure distante.  
  
-   La partie inférieure de l’écran affiche l’état de la migration des données pour chaque table Stretch de la base de données.  
  
 ![Surveillance de Stretch Database](../../sql-server/stretch-database/media/stretch-monitor.PNG "Surveillance de Stretch Database")  
  
##  <a name="Migration"></a> Vérification de l’état de la migration des données dans une vue de gestion dynamique  
 Ouvrez la vue de gestion dynamique **sys.dm_db_rda_migration_status** pour afficher le nombre de lots et de lignes de données migrés. Pour plus d’informations, consultez [sys.dm_db_rda_migration_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/stretch-database-sys-dm-db-rda-migration-status.md).  
  
##  <a name="Firewall"></a> Résolution des problèmes liés à la migration des données  
 **Je ne parviens pas à migrer les lignes de ma table Stretch vers Azure. Quel est le problème ?**  
 Plusieurs problèmes peuvent affecter la migration. Vérifiez les points suivants :  
  
-   Vérifiez la connectivité réseau de l’ordinateur SQL Server.  
  
-   Vérifiez que le pare-feu Azure n’empêche pas la connexion de SQL Server au point de terminaison distant.  
  
-   Vérifiez l’état du dernier lot dans la vue de gestion dynamique **sys.dm_db_rda_migration_status** . Si une erreur s’est produite, vérifiez les valeurs error_severity, error_state et error_number du lot concerné.  
  
    -   Pour plus d’informations sur la vue, consultez [sys.dm_db_rda_migration_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/stretch-database-sys-dm-db-rda-migration-status.md).  
  
    -   Pour plus d’informations sur le contenu d’un message d’erreur SQL Server, consultez [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md).  
  
 **Le pare-feu Azure bloque les connexions à partir de mon serveur local.**  
 Vous devez peut-être ajouter une règle dans les paramètres de pare-feu Azure du serveur Azure afin d’autoriser SQL Server à communiquer avec le serveur Azure à distance.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer Stretch Database et résoudre ses problèmes](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  
  
  

