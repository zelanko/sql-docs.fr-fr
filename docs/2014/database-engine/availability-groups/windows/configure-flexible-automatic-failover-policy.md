---
title: Configurer la stratégie de basculement Flexible pour contrôler les Conditions pour le basculement automatique (groupes de disponibilité) Always On | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], flexible failover policy
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
caps.latest.revision: 22
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4868c07427230de655fc8a1742458f4b4c72cfbb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37193979"
---
# <a name="configure-the-flexible-failover-policy-to-control-conditions-for-automatic-failover-always-on-availability-groups"></a>Configurer la stratégie de basculement flexible pour contrôler les conditions du basculement automatique (groupes de disponibilité Always On)
  Cette rubrique explique comment configurer la stratégie de basculement flexible pour un groupe de disponibilité AlwaysOn à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Une stratégie de basculement flexible vous offre un contrôle granulaire sur les conditions qui entraînent un basculement automatique d'un groupe de disponibilité. En changeant les conditions d'échec qui déclenchent un basculement automatique et la fréquence des contrôles d'intégrité, vous pouvez augmenter ou diminuer la probabilité d'un basculement automatique pour assurer le contrat de niveau de service relatif à la haute disponibilité.  
  
  
  
    > [!NOTE]  
    >  The flexible failover policy of an availability group cannot be configured by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Limitations"></a> Limitations relatives aux basculements automatiques  
  
-   Pour qu'un basculement automatique se produise, le réplica principal et un réplica secondaire doivent être configurés pour le mode de disponibilité avec validation synchrone et basculement automatique et le réplica secondaire doit être synchronisé avec le réplica principal.  
  
-   Si un groupe de disponibilité dépasse le seuil d'échec WSFC, le cluster WSFC ne tente pas un basculement automatique du groupe de disponibilité. En outre, le groupe de ressources WSFC du groupe de disponibilité reste à l'état d'échec jusqu'à ce que l'administrateur de cluster mette manuellement le groupe de ressources en ligne ou jusqu'à ce que l'administrateur de base de données exécute un basculement manuel du groupe de disponibilité. Le *seuil d'échec WSFC* est le nombre maximal d'échecs autorisés pour le groupe de disponibilité au cours d'une période donnée. La période par défaut est de six heures, et la valeur par défaut du nombre maximal d’échecs au cours de cette période est *n*-1, où *n* est le nombre de nœuds de WSFC. Pour modifier les valeurs de seuil/d'échec pour un groupe de disponibilité donné, utilisez la console du gestionnaire de basculement WSFC.  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Vous devez être connecté à l'instance de serveur qui héberge le réplica principal.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
  
|Tâche|Autorisations|  
|----------|-----------------|  
|Pour configurer la stratégie de basculement flexible pour un nouveau groupe de disponibilité|Requiert l’appartenance au rôle serveur fixe **sysadmin** et l’autorisation de serveur CREATE AVAILABILITY GROUP, l’autorisation ALTER ANY AVAILABILITY GROUP ou l’autorisation CONTROL SERVER.|  
|Pour modifier la stratégie d'un groupe de disponibilité existant|Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.|  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour configurer la stratégie de basculement flexible**  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica principal.  
  
2.  Pour un nouveau groupe de disponibilité, utilisez l’instruction [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] . Si vous modifiez un groupe de disponibilité existant, utilisez l’instruction [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] .  
  
    -   Pour définir le niveau de condition de basculement, utilisez l’option FAILURE_CONDITION_LEVEL = *n* , où *n* est un entier compris entre 1 et 5.  
  
         Par exemple, l'instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] suivante modifie le niveau de condition d'échec d'un groupe de disponibilité existant, `AG1`, sur le niveau un :  
  
        ```  
  
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         La relation de ces valeurs entières avec les niveaux de condition d'échec est la suivante :  
  
        |[!INCLUDE[tsql](../../../includes/tsql-md.md)] Valeur|Level|Le basculement automatique démarre lorsque…|  
        |------------------------------|-----------|-------------------------------------------|  
        | 1|Un|Le serveur est arrêté. Le service SQL Server s'arrête à cause d'un basculement ou d'un redémarrage.|  
        |2|Deux|Le serveur ne répond pas. Toutes les conditions qui correspondent à une valeur inférieure sont remplies, le service SQL Server est connecté au cluster et le seuil du délai d'attente de contrôle d'intégrité est dépassé, ou le réplica principal actuel est dans un état d'échec.|  
        |3|Trois|Erreur critique du serveur. Toutes les conditions qui correspondent à une valeur inférieure sont remplies ou une erreur interne et critique de serveur est survenue.<br /><br /> C'est le niveau par défaut.|  
        |4|Quatre|Erreur de serveur modérée. Toutes les conditions qui correspondent à une valeur inférieure sont remplies ou une erreur modérée de serveur s'est produite.|  
        |5|Cinq|Conditions d'échec qualifiées. Toutes les conditions qui correspondent à une valeur inférieure sont remplies ou une condition d'échec qualifiée s'est produite.|  
  
         Pour plus d’informations sur les niveaux de condition de basculement, consultez [Stratégie flexible pour le basculement automatique d’un groupe de disponibilité &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).  
  
    -   Pour configurer le seuil du délai d’attente de contrôle d’intégrité, utilisez l’optionHEALTH_CHECK_TIMEOUT = *n*, où *n* est un entier compris entre 15000 millisecondes (15 secondes) et 4294967295 millisecondes. La valeur par défaut est 30 000 millisecondes (ou 30 secondes).  
  
         Par exemple, l'instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] suivante modifie le seuil du délai d'attente de contrôle d'intégrité d'un groupe de disponibilité existant, `AG1`, sur 60 000 millisecondes (une minute).  
  
        ```  
  
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Pour configurer la stratégie de basculement flexible**  
  
1.  Définir par défaut (`cd`) à l’instance de serveur qui héberge le réplica principal.  
  
2.  Lorsque vous ajoutez un réplica de disponibilité à un groupe de disponibilité, utilisez l'applet de commande `New-SqlAvailabilityGroup`. Lorsque vous modifiez un réplica de disponibilité existant, utilisez l'applet de commande `Set-SqlAvailabilityGroup`.  
  
    -   Pour définir le niveau de condition de basculement, utilisez le `FailureConditionLevel` *niveau* paramètre, où *niveau* est une des valeurs suivantes :  
  
        |Valeur|Niveau|Le basculement automatique démarre lorsque…|  
        |-----------|-----------|-------------------------------------------|  
        |`OnServerDown`|Un|Le serveur est arrêté. Le service SQL Server s'arrête à cause d'un basculement ou d'un redémarrage.|  
        |`OnServerUnresponsive`|Deux|Le serveur ne répond pas. Toutes les conditions qui correspondent à une valeur inférieure sont remplies, le service SQL Server est connecté au cluster et le seuil du délai d'attente de contrôle d'intégrité est dépassé, ou le réplica principal actuel est dans un état d'échec.|  
        |`OnCriticalServerError`|Trois|Erreur critique du serveur. Toutes les conditions qui correspondent à une valeur inférieure sont remplies ou une erreur interne et critique de serveur est survenue.<br /><br /> C'est le niveau par défaut.|  
        |`OnModerateServerError`|Quatre|Erreur de serveur modérée. Toutes les conditions qui correspondent à une valeur inférieure sont remplies ou une erreur modérée de serveur s'est produite.|  
        |`OnAnyQualifiedFailureConditions`|Cinq|Conditions d'échec qualifiées. Toutes les conditions qui correspondent à une valeur inférieure sont remplies ou une condition d'échec qualifiée s'est produite.|  
  
         Pour plus d’informations sur les niveaux de condition de basculement, consultez [Stratégie flexible pour le basculement automatique d’un groupe de disponibilité &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).  
  
         Par exemple, la commande suivante modifie le niveau de condition d'échec d'un groupe de disponibilité existant, `AG1`, sur le niveau un.  
  
        ```  
        Set-SqlAvailabilityGroup `   
        -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `   
        -FailureConditionLevel OnServerDown  
        ```  
  
    -   Pour définir le seuil de délai d’attente de contrôle d’intégrité, utilisez le `HealthCheckTimeout` *n* paramètre, où *n* est un entier compris entre 15000 millisecondes (15 secondes) et 4294967295 millisecondes. La valeur par défaut est 30 000 millisecondes (ou 30 secondes).  
  
         Par exemple, la commande suivante modifie le seuil du délai d'attente de contrôle d'intégrité d'un groupe de disponibilité existant, `AG1`, sur 120 000 millisecondes (deux minutes).  
  
        ```  
        Set-SqlAvailabilityGroup `   
        -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `   
        -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  Pour afficher la syntaxe d’une applet de commande, utilisez le `Get-Help` applet de commande dans le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] environnement PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Modes de disponibilité (groupes de disponibilité AlwaysOn)](availability-modes-always-on-availability-groups.md)   
 [Basculement et Modes de basculement &#40;groupes de disponibilité AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md)   
 [Clustering de basculement Windows Server &#40;WSFC&#41; avec SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [Stratégie de basculement pour les instances de cluster de basculement](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)   
 [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)  
  
  
