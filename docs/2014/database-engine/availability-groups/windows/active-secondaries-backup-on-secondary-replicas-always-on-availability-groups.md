---
title: 'Secondaires actifs : sauvegarde sur les réplicas secondaires (groupes de disponibilité Always On) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a94db154042f2cc6314459b6af4b52a43c2c9966
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62790678"
---
# <a name="active-secondaries-backup-on-secondary-replicas-always-on-availability-groups"></a>Secondaires actifs : sauvegarde sur les réplicas secondaires (groupes de disponibilité Always On)
  Les fonctions secondaires actives [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] incluent la prise en charge des opérations de sauvegarde sur les réplicas secondaires. Les opérations de sauvegarde peuvent solliciter de manière significative les E/S et l'UC (avec la compression de sauvegarde). Le déchargement des sauvegardes vers un réplica secondaire synchronisé ou en cours de synchronisation vous permet d'utiliser les ressources sur l'instance de serveur qui héberge le réplica principal pour vos charges de travail de niveau 1.  
  
> [!NOTE]  
>  Les instructions RESTORE ne sont pas autorisées sur les bases de données primaire ou secondaire d'un groupe de disponibilité.  
  
  
  
##  <a name="backup-types-supported-on-secondary-replicas"></a><a name="SupportedBuTypes"></a> Types de sauvegardes pris en charge sur les réplicas secondaires  
  
-   `BACKUP DATABASE`prend en charge uniquement la copie seule des sauvegardes complètes de la base de données, des fichiers ou des groupes de fichiers lorsqu'elle est exécutée sur les réplicas secondaires. Notez que les sauvegardes de type copie seule n'affectent pas la séquence de journaux de transactions consécutifs ou n'effacent pas la bitmap différentielle.  
  
-   Les sauvegardes différentielles ne sont pas prises en charge sur les réplicas secondaires.  
  
-   **BACKUP LOG** prend uniquement en charge les sauvegardes de journaux régulières (l’option COPY_ONLY n’est pas prise en charge pour les sauvegardes de fichiers journaux sur des réplicas secondaires).  
  
     Une séquence de journaux de transactions consécutifs cohérente est garantie sur les sauvegardes des journaux effectuées sur les réplicas (principaux ou secondaires), quel que soit leur mode de disponibilité (avec validation synchrone ou validation asynchrone).  
  
-   Pour sauvegarder une base de données secondaire, un réplica secondaire doit pouvoir communiquer avec le réplica principal et doit être `SYNCHRONIZED` ou `SYNCHRONIZING`.  
  
##  <a name="configuring-where-backup-jobs-run"></a><a name="WhereBuJobsRun"></a>Configuration de l’emplacement d’exécution des travaux de sauvegarde  
 L'exécution de sauvegardes sur un réplica secondaire pour décharger la charge de travail de sauvegarde du serveur de production principal constitue un énorme avantage. Cependant, les sauvegardes sur des réplicas secondaires compliquent considérablement la détermination de l'emplacement d'exécution des travaux de sauvegarde. Pour résoudre ce problème, configurez l'emplacement d'exécution des travaux de sauvegarde comme suit :  
  
1.  Configurez le groupe de disponibilité pour spécifier les réplicas de disponibilité de votre choix pour effectuer les sauvegardes. Pour plus d’informations, consultez les paramètres *AUTOMATED_BACKUP_PREFERENCE* et *BACKUP_PRIORITY* dans [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) ou [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).  
  
2.  Créez les travaux de sauvegarde par script pour chaque base de données de disponibilité sur chaque instance de serveur qui héberge un réplica de disponibilité candidat pour effectuer des sauvegardes. Pour plus d’informations, consultez la section « Suivi : Après la configuration de la sauvegarde sur les réplicas secondaires » dans [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
 **Pour configurer la sauvegarde sur les réplicas secondaires**  
  
-   [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
 **Pour déterminer si le réplica actuel est le réplica de sauvegarde par défaut**  
  
-   [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 **Pour créer un travail de sauvegarde**  
  
-   [Utiliser l'Assistant Plan de maintenance](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
-   [Implémenter des travaux](../../../ssms/agent/implement-jobs.md)  
  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Sauvegardes de copie uniquement &#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md)   
 [CRÉER un groupe de disponibilité &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
