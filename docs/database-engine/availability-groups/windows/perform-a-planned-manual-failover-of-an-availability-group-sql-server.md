---
title: "Effectuer un basculement manuel planifié d'un groupe de disponibilité (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.availabilitygroup.manualfailover.f1
helpviewer_keywords:
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
caps.latest.revision: 36
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5017d65bb6324f7137c4b5a2a2e0e59b95829748
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="perform-a-planned-manual-failover-of-an-availability-group-sql-server"></a>Effectuer un basculement manuel planifié d'un groupe de disponibilité (SQL Server)
  Cette rubrique explique comment effectuer un basculement manuel sans perte de données ( *basculement manuel planifié*) sur un groupe de disponibilité Always On à l’aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou de PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Un groupe de disponibilité bascule au niveau d'un réplica de disponibilité. Un basculement manuel planifié, à l'instar de tout basculement [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , entraîne la transition d'un réplica secondaire vers le rôle principal et, simultanément, celle de l'ancien réplica principal vers le rôle secondaire.  
  
 Un basculement manuel planifié, pris en charge uniquement lorsque le réplica principal et le réplica secondaire cible s'exécutent en mode de validation synchrone et sont actuellement synchronisés, conserve toutes les données dans les bases de données secondaires jointes au groupe de disponibilité sur le réplica secondaire cible. Une fois la transition du réplica principal précédent vers le rôle secondaire terminé, ses bases de données deviennent les bases de données secondaires et démarrent la synchronisation avec les nouvelles bases de données primaires. Une fois que toutes ont passé à l'état SYNCHRONIZED, le nouveau réplica secondaire devient éligible pour servir de cible d'un futur basculement manuel planifié.  
  
> [!NOTE]  
>  Si les réplicas principal et secondaire sont tous les deux configurés pour le mode de basculement automatique, une fois que le réplica secondaire est synchronisé, il peut également servir de cible à un basculement automatique. Pour plus d’informations, consultez [Modes de disponibilité &#40;groupes de disponibilité Always On&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md).  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Conditions préalables requises et restrictions](#Prerequisites)  
  
     [Sécurité](#Security)  
  
-   **Pour basculer manuellement un groupe de disponibilité, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Suivi :**  [Après avoir manuellement basculé un groupe de disponibilité](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Une commande de basculement retourne dès que le réplica secondaire cible a accepté la commande. Toutefois, la récupération de la base de données est asynchrone après que le basculement du groupe de disponibilité est terminé.  
  
-   La cohérence entre les bases de données sur plusieurs bases de données dans le groupe de disponibilité peut ne pas être conservée lors d’un basculement.  
  
    > [!NOTE]  
    >  La prise en charge des transactions distribuées et entre les bases de données varie selon les versions de système d’exploitation et SQL Server. Pour plus d’informations, consultez [Transactions entre bases de données et transactions distribuées pour des groupes de disponibilité Always On et la mise en miroir de bases de données &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  
###  <a name="Prerequisites"></a> Conditions préalables requises et restrictions  
  
-   Le réplica secondaire cible et le réplica principal doivent tous les deux s'exécuter en mode de disponibilité avec validation synchrone.  
  
-   Le réplica secondaire cible doit être actuellement synchronisé avec le réplica principal. Pour cela, il faut que toutes les bases de données secondaires sur ce réplica secondaire aient été jointes au groupe de disponibilité et soient synchronisées avec leurs bases de données primaires correspondantes (autrement dit, les bases de données secondaires locales doivent avoir l'état SYNCHRONIZED).  
  
    > [!TIP]  
    >  Pour déterminer la disponibilité de basculement d’un réplica secondaire, interrogez la colonne **is_failover_ready** dans la vue de gestion dynamique [sys.dm_hadr_database_cluster_states](../../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql.md) , ou regardez dans la colonne **Disponibilité du basculement** du [tableau de bord du groupe Always On](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md).  
  
-   Cette tâche est prise en charge uniquement sur le réplica secondaire cible. Vous devez être connecté à l'instance de serveur qui héberge le réplica secondaire cible.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour basculer manuellement un groupe de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance de serveur qui héberge un réplica secondaire du groupe de disponibilité qui doit être basculé, et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité Always On** et le nœud **Groupes de disponibilité** .  
  
3.  Cliquez avec le bouton droit sur le groupe de disponibilité à basculer et sélectionnez la commande **Basculement** .  
  
4.  Cette commande lance l'Assistant Basculer le groupe de disponibilité. Pour plus d'informations, consultez [Utiliser l’Assistant Basculer le groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour basculer manuellement un groupe de disponibilité**  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica secondaire cible.  
  
2.  Utilisez l'instruction [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) , comme suit :  
  
     ALTER AVAILABILITY GROUP *nom_groupe* FAILOVER  
  
     où *nom_groupe* correspond au nom du groupe de disponibilité.  
  
     L’exemple suivant effectue un basculement manuel du groupe de disponibilité *MyAg* vers le réplica secondaire connecté.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Pour basculer manuellement un groupe de disponibilité**  
  
1.  Remplacez le répertoire (**cd**) par l’instance de serveur qui héberge le réplica secondaire cible.  
  
2.  Utilisez l’applet de commande **Switch-SqlAvailabilityGroup** .  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d’une applet de commande, utilisez l’applet de commande **Get-Help** dans l’environnement [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
     L’exemple suivant effectue un basculement manuel du groupe de disponibilité *MyAg* vers le réplica secondaire dont le chemin est spécifié.  
  
    ```  
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [fournisseur PowerShell SQL Server](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)  
  
##  <a name="FollowUp"></a> Suivi : Après avoir basculé manuellement un groupe de disponibilité  
 Si vous avez effectué le basculement en dehors de [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] du groupe de disponibilité, ajustez les votes de quorum des nœuds WSFC afin de refléter la nouvelle configuration du groupe de disponibilité. Pour plus d’informations, consultez [Clustering de basculement Windows Server &#40;WSFC&#41; avec SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Basculement et modes de basculement &#40;groupes de disponibilité Always On&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)   
 [Effectuer un basculement manuel forcé d’un groupe de disponibilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
  

