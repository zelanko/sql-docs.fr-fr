---
title: Vue d’ensemble des applets de commande PowerShell pour les groupes de disponibilité AlwaysOn (SQL Server) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], PowerShell cmdlets
- Availability Groups [SQL Server], about
- PowerShell [SQL Server], cmdlets
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
caps.latest.revision: 35
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: 3d3b1715a61ed7711217148a3a42bbcd5340308a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052702"
---
# <a name="overview-of-powershell-cmdlets-for-alwayson-availability-groups-sql-server"></a>Vue d'ensemble des applets de commande PowerShell pour les groupes de disponibilité AlwaysOn (SQL Server)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PowerShell est un interpréteur de ligne de commande et un langage de script basé sur des tâches tout spécialement conçu pour l’administration système. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] fournit un ensemble d'applets de commande PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] qui vous permet de déployer, gérer et surveiller des groupes de disponibilité, des réplicas de disponibilité et des bases de données de disponibilité.  
  
> [!NOTE]  
>  Une applet de commande PowerShell peut s'effectuer en initiant correctement une action. Cela n'indique pas si le travail prévu, tel que le basculement d'un groupe de disponibilité, est terminé. Lors de l'écriture sous forme de script d'une séquence d'actions, vous devrez peut-être vérifier l'état des actions et attendre la fin de leur exécution.  
  
 Cette rubrique présente les applets de commande pour les ensembles de tâches suivants :  
  
-   [Configuration d’une instance de serveur pour les groupes de disponibilité AlwaysOn](#ConfiguringServerInstance)  
  
-   [Sauvegarde et restauration de bases de données et de journaux de transactions](#BnRcmdlets)  
  
-   [Création et gestion d'un groupe de disponibilité](#DeployManageAGs)  
  
-   [Création et gestion d'un écouteur de groupe de disponibilité](#AGlisteners)  
  
-   [Création et gestion d'un réplica de disponibilité](#DeployManageARs)  
  
-   [Ajout et gestion d'une base de données de disponibilité](#DeployManageDbs)  
  
-   [Surveillance de l'intégrité d'un groupe de disponibilité](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  Pour obtenir la liste des rubriques dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] la documentation en ligne qui décrivent comment utiliser les applets de commande pour effectuer [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] tâches, consultez la section « Tâches associées » de [vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="ConfiguringServerInstance"></a> Configuration d’une Instance de serveur pour les groupes de disponibilité AlwaysOn  
  
|Applets de commande|Description|Prise en charge sur|  
|-------------|-----------------|------------------|  
|`Disable-SqlAlwaysOn`|Désactive la fonctionnalité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur une instance de serveur.|Instance de serveur spécifiée par le paramètre `Path`, `InputObject` ou `Name`. (Il doit s'agir d'une édition de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui prend en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].)|  
|`Enable-SqlAlwaysOn`|Active [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur une instance de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] qui prend en charge la fonctionnalité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] . Pour plus d’informations sur la prise en charge de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [conditions préalables, Restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).|Toute édition de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui prend en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].|  
|`New-SqlHadrEndPoint`|Crée un nouveau point de terminaison de mise en miroir de bases de données sur une instance de serveur. Ce point de terminaison est requis pour le déplacement des données entre des bases de données primaires et secondaires.|Toute instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|`Set-SqlHadrEndpoint`|Modifie les propriétés d'un point de terminaison de mise en miroir de bases de données existant, telles que le nom, l'état ou les propriétés d'authentification.|Instance de serveur qui prend en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] et ne dispose pas d'un point de terminaison de mise en miroir de bases de données|  
  
##  <a name="BnRcmdlets"></a> Backing Up and Restoring Databases and Transaction Logs  
  
|Applets de commande|Description|Prise en charge sur|  
|-------------|-----------------|------------------|  
|`Backup-SqlDatabase`|Crée une sauvegarde de données ou de journal.|Base de données en ligne (pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], base de données sur l'instance de serveur qui héberge le réplica principal)|  
|`Restore-SqlDatabase`|Restaure une sauvegarde.|Instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], instance de serveur qui héberge un réplica secondaire)<br /><br /> **\*\* Important \* \***  lorsque vous préparez une base de données secondaire, vous devez utiliser le `-NoRecovery` paramètre dans chaque `Restore-SqlDatabase` commande.|  
  
 Pour plus d’informations sur l’utilisation de ces applets de commande pour préparer une base de données secondaire, consultez [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
##  <a name="DeployManageAGs"></a> Creating and Managing an Availability Group  
  
|Applets de commande|Description|Prise en charge sur|  
|-------------|-----------------|------------------|  
|`New-SqlAvailabilityGroup`|Crée un groupe de disponibilité.|Instance de serveur pour héberger le réplica principal|  
|`Remove-SqlAvailabilityGroup`|Supprime un groupe de disponibilité|Instance de serveur activée pour le service HADR|  
|`Set-SqlAvailabilityGroup`|Définit les propriétés d'un groupe de disponibilité ; met un groupe de disponibilité en ligne/hors connexion|Instance de serveur qui héberge le réplica principal|  
|`Switch-SqlAvailabilityGroup`|Démarre l'une des formes de basculement suivantes :<br /><br /> Basculement forcé d'un groupe de disponibilité (avec possible perte de données).<br /><br /> Basculement manuel d'un groupe de disponibilité.|Instance de serveur qui héberge le réplica secondaire cible.|  
  
##  <a name="AGlisteners"></a> Creating and Managing an Availability Group Listener  
  
|Applet de commande|Description|Prise en charge sur|  
|------------|-----------------|------------------|  
|`New-SqlAvailabilityGroupListener`|Crée un écouteur de groupe de disponibilité et l'attache à un groupe de disponibilité existant.|Instance de serveur qui héberge le réplica principal|  
|`Set-SqlAvailabilityGroupListener`|Modifie le paramètre de port sur un écouteur de groupe de disponibilité existant.|Instance de serveur qui héberge le réplica principal|  
|`Add-SqlAvailabilityGroupListenerStaticIp`|Ajoute une adresse IP statique à une configuration existante d'écouteur de groupe de disponibilité. L'adresse IP peut être une adresse IPv4 avec sous-réseau ou une adresse IPv6.|Instance de serveur qui héberge le réplica principal|  
  
##  <a name="DeployManageARs"></a> Creating and Managing an Availability Replica  
  
|Applets de commande|Description|Prise en charge sur|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityReplica**|Crée un réplica de disponibilité. Vous pouvez utiliser la `-AsTemplate` paramètre pour créer un objet réplica de disponibilité en mémoire pour chaque nouveau réplica de disponibilité.|Instance de serveur qui héberge le réplica principal|  
|`Join-SqlAvailabilityGroup`|Joint un réplica secondaire au groupe de disponibilité.|Instance de serveur qui héberge le réplica secondaire.|  
|**Remove-SqlAvailabilityReplica**|Supprime un réplica de disponibilité.|Instance de serveur qui héberge le réplica principal|  
|`Set-SqlAvailabilityReplica`|Définit les propriétés d'un réplica de disponibilité.|Instance de serveur qui héberge le réplica principal|  
  
##  <a name="DeployManageDbs"></a> Adding and Managing an Availability Database  
  
|Applets de commande|Description|Prise en charge sur|  
|-------------|-----------------|------------------|  
|**Add-SqlAvailabilityDatabase**|Sur le réplica principal, ajoute une base de données à un groupe de disponibilité.<br /><br /> Sur un réplica secondaire, joint une base de données secondaire à un groupe de disponibilité.|Instance de serveur qui héberge un réplica de disponibilité (le comportement diffère pour les réplicas principal et secondaire)|  
|**Remove-SqlAvailabilityDatabase**|Sur le réplica principal, supprime la base de données du groupe de disponibilité.<br /><br /> Sur un réplica secondaire, supprime la base de données secondaire locale du réplica secondaire local.|Instance de serveur qui héberge un réplica de disponibilité (le comportement diffère pour les réplicas principal et secondaire)|  
|`Resume-SqlAvailabilityDatabase`|Reprend le déplacement des données pour une base de données de disponibilité interrompue.|Instance de serveur sur laquelle la base de données a été interrompue.|  
|`Suspend-SqlAvailabilityDatabase`|Interrompt le déplacement des données pour une base de données de disponibilité.|Instance de serveur qui héberge un réplica de disponibilité.|  
  
##  <a name="MonitorTblshtAGs"></a> Monitoring Availability Group Health  
 Les applets de commande [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] suivantes vous permettent de surveiller l'intégrité d'un groupe de disponibilité et de ses réplicas et bases de données.  
  
> [!IMPORTANT]  
>  Vous devez disposer des autorisations CONNECT, VIEW SERVER STATE et VIEW ANY DEFINITION pour exécuter ces applets de commande.  
  
|Applet de commande|Description|Prise en charge sur|  
|------------|-----------------|------------------|  
|`Test-SqlAvailabilityGroup`|Évalue l'intégrité d'un groupe de disponibilité lors de l'évaluation des stratégies de gestion basées sur des stratégies SQL Server.|Toute instance de serveur qui héberge un réplica de disponibilité.*|  
|`Test-SqlAvailabilityReplica`|Évalue l'intégrité des réplicas de disponibilité lors de l'évaluation des stratégies de gestion basées sur des stratégies SQL Server.|Toute instance de serveur qui héberge un réplica de disponibilité.*|  
|`Test-SqlDatabaseReplicaState`|Évalue l'intégrité d'une base de données de disponibilité sur tous les réplicas de disponibilité joints par l'évaluation des stratégies de gestion basées sur des stratégies SQL Server.|Toute instance de serveur qui héberge un réplica de disponibilité.*|  
  
 *Pour afficher des informations sur tous les réplicas de disponibilité d’un groupe de disponibilité, utilisez l’instance de serveur qui héberge le réplica principal.  
  
 Pour plus d’informations, consultez [utiliser les stratégies pour afficher l’intégrité d’un groupe de disponibilité AlwaysOn &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
  