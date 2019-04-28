---
title: Démarrer un mouvement de données sur une base de données secondaire AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], databases
ms.assetid: 498eb3fb-6a43-434d-ad95-68a754232c45
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b0626ce7dee34ed21aad3e902e3c3f555f27ab97
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813553"
---
# <a name="start-data-movement-on-an-alwayson-secondary-database-sql-server"></a>Démarrer un mouvement de données sur une base de données secondaire AlwaysOn (SQL Server)
  Cette rubrique contient des informations sur le démarrage de la synchronisation des données après avoir ajouté une base de données à un groupe de disponibilité AlwaysOn. Pour chaque nouveau réplica principal, les bases de données secondaires doivent être préparées sur les instances de serveur qui hébergent les réplicas secondaires. Puis, chacune de ces bases de données secondaires doit être attachée manuellement au groupe de disponibilité.  
  
> [!NOTE]  
>  Si les chemins d’accès aux fichiers sont identiques sur chaque instance de serveur qui héberge un réplica de disponibilité pour un groupe de disponibilité, [l’Assistant Nouveau groupe de disponibilité](use-the-availability-group-wizard-sql-server-management-studio.md), [l’Assistant Ajouter un réplica au groupe de disponibilité](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)ou [l’Assistant Ajouter une base de données au groupe de disponibilité](availability-group-add-database-to-group-wizard.md) peut être en mesure de démarrer automatiquement la synchronisation des données.  
  
 Pour démarrer la synchronisation des données manuellement, vous devez vous connecter, tour à tour, à chaque instance de serveur qui héberge un réplica secondaire pour le groupe de disponibilité et procéder comme suit :  
  
1.  Restaurez les sauvegardes actuelles de chaque base de données primaire et de son journal des transactions (à l'aide de RESTORE WITH NORECOVERY). Vous pouvez utiliser l'une des autres approches suivantes :  
  
    -   Restaurez manuellement une sauvegarde récente de la base de données primaire à l'aide de RESTORE WITH NORECOVERY, puis restaurez chaque sauvegarde de journal suivante à l'aide de RESTORE WITH NORECOVERY. Effectuez cette séquence de restauration sur chaque instance de serveur qui héberge un réplica secondaire pour le groupe de disponibilité.  
  
         **Pour plus d'informations, consultez :**  
  
         [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
    -   Si vous ajoutez une ou plusieurs bases de données principales pour la copie des journaux de transaction à un groupe de disponibilité, vous pourrez peut-être effectuer une migration d'une ou de plusieurs des bases de données secondaires correspondantes depuis la copie des journaux de transaction vers des groupes de disponibilité AlwaysOn. La migration d'une base de données secondaire pour la copie des journaux de transaction nécessite l'utilisation du même nom de base de données que la base de données principale et sa présence sur une instance de serveur qui héberge un réplica secondaire pour le groupe de disponibilité. Par ailleurs, le groupe de disponibilité doit être configuré de sorte que le réplica principal corresponde à la préférence pour les sauvegardes et qu'il soit candidat à l'exécution de sauvegardes (autrement dit, que sa priorité de sauvegarde soit >0). Une fois que le travail de sauvegarde a été exécuté sur la base de données principale, vous devez le désactiver. De même, une fois que le travail de restauration a été exécuté sur une base de données secondaire donnée, vous devez le désactiver.  
  
        > [!NOTE]  
        >  Après avoir créé toutes les bases de données secondaires pour le groupe de disponibilité, si vous souhaitez effectuer des sauvegardes sur des réplicas secondaires, vous devez reconfigurer la préférence de sauvegarde automatisée du groupe de disponibilité.  
  
         **Pour plus d'informations, consultez :**  
  
         [Prérequis pour la migration à partir des journaux de transaction vers les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
         [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
2.  Dès que possible, attachez chaque base de données secondaire récemment préparée au groupe de disponibilité.  
  
     **Pour plus d'informations, consultez :**  
  
     [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
##  <a name="LaunchWiz"></a> Tâches associées  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter une base données au groupe de disponibilité &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
