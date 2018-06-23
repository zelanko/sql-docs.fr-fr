---
title: Effectuer un basculement manuel planifié d'un groupe de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.availabilitygroup.manualfailover.f1
helpviewer_keywords:
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
caps.latest.revision: 34
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 2573df633ca63b480869831b2f5edc0993ad4a56
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042080"
---
# <a name="perform-a-planned-manual-failover-of-an-availability-group-sql-server"></a>Effectuer un basculement manuel planifié d'un groupe de disponibilité (SQL Server)
  Cette rubrique explique comment effectuer un basculement manuel sans perte de données (*basculement manuel planifié*) sur un groupe de disponibilité AlwaysOn à l’aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou de PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Un groupe de disponibilité bascule au niveau d'un réplica de disponibilité. Un basculement manuel planifié, à l'instar de tout basculement [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , entraîne la transition d'un réplica secondaire vers le rôle principal et, simultanément, celle de l'ancien réplica principal vers le rôle secondaire.  
  
 Un basculement manuel planifié, pris en charge uniquement lorsque le réplica principal et le réplica secondaire cible s'exécutent en mode de validation synchrone et sont actuellement synchronisés, conserve toutes les données dans les bases de données secondaires jointes au groupe de disponibilité sur le réplica secondaire cible. Une fois la transition du réplica principal précédent vers le rôle secondaire terminé, ses bases de données deviennent les bases de données secondaires et démarrent la synchronisation avec les nouvelles bases de données primaires. Une fois que toutes ont passé à l'état SYNCHRONIZED, le nouveau réplica secondaire devient éligible pour servir de cible d'un futur basculement manuel planifié.  
  
> [!NOTE]  
>  Si les réplicas principal et secondaire sont tous les deux configurés pour le mode de basculement automatique, une fois que le réplica secondaire est synchronisé, il peut également servir de cible à un basculement automatique. Pour plus d’informations, consultez [Modes de disponibilité &#40;groupes de disponibilité AlwaysOn&#41;](availability-modes-always-on-availability-groups.md).  
  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Une commande de basculement retourne dès que le réplica secondaire cible a accepté la commande. Toutefois, la récupération de la base de données est asynchrone après que le basculement du groupe de disponibilité est terminé.  
  
-   La cohérence entre bases de données sur plusieurs bases de données dans le groupe de disponibilité n'est pas conservée lors d'un basculement.  
  
    > [!NOTE]  
    >  Les transactions entre bases de données et les transactions distribuées ne sont pas prises en charge par [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Pour plus d’informations, consultez [Transactions entre bases de données non prises en charge pour la mise en miroir de bases de données ou les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).  
  
###  <a name="Prerequisites"></a> Conditions préalables requises et restrictions  
  
-   Le réplica secondaire cible et le réplica principal doivent tous les deux s'exécuter en mode de disponibilité avec validation synchrone.  
  
-   Le réplica secondaire cible doit être actuellement synchronisé avec le réplica principal. Pour cela, il faut que toutes les bases de données secondaires sur ce réplica secondaire aient été jointes au groupe de disponibilité et soient synchronisées avec leurs bases de données primaires correspondantes (autrement dit, les bases de données secondaires locales doivent avoir l'état SYNCHRONIZED).  
  
    > [!TIP]  
    >  Pour déterminer la disponibilité de basculement d’un réplica secondaire, interrogez la colonne **is_failover_ready** dans la vue de gestion dynamique [sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql), ou regardez dans la colonne **Disponibilité du basculement** du [tableau de bord du groupe AlwaysOn](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
-   Cette tâche est prise en charge uniquement sur le réplica secondaire cible. Vous devez être connecté à l'instance de serveur qui héberge le réplica secondaire cible.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour basculer manuellement un groupe de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance de serveur qui héberge un réplica secondaire du groupe de disponibilité qui doit être basculé, et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Cliquez avec le bouton droit sur le groupe de disponibilité à basculer et sélectionnez la commande **Basculement**.  
  
4.  Cette commande lance l'Assistant Basculer le groupe de disponibilité. Pour plus d’informations, consultez [Utiliser l’Assistant Basculer le groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour basculer manuellement un groupe de disponibilité**  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica secondaire cible.  
  
2.  Utilisez l'instruction [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) , comme suit :  
  
     ALTER AVAILABILITY GROUP *nom_groupe* FAILOVER  
  
     où *nom_groupe* correspond au nom du groupe de disponibilité.  
  
     L’exemple suivant effectue un basculement manuel du groupe de disponibilité *MyAg* vers le réplica secondaire connecté.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Pour basculer manuellement un groupe de disponibilité**  
  
1.  Accédez au répertoire (`cd`) à l’instance de serveur qui héberge le réplica secondaire cible.  
  
2.  Utilisez le `Switch-SqlAvailabilityGroup` applet de commande.  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d’une applet de commande, utilisez le `Get-Help` applet de commande dans le [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] environnement PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
     L’exemple suivant effectue un basculement manuel du groupe de disponibilité *MyAg* vers le réplica secondaire dont le chemin est spécifié.  
  
    ```  
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="FollowUp"></a> Suivi : Après avoir basculé manuellement un groupe de disponibilité  
 Si vous avez effectué le basculement en dehors de [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] du groupe de disponibilité, ajustez les votes de quorum des nœuds WSFC afin de refléter la nouvelle configuration du groupe de disponibilité. Pour plus d’informations, consultez [Clustering de basculement Windows Server &#40;WSFC&#41; avec SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Basculement et Modes de basculement &#40;groupes de disponibilité AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md)   
 [Effectuer un basculement manuel forcé d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
  
