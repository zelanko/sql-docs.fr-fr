---
title: Ajouter un réplica secondaire à un groupe de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 6669dcce-85f9-495f-aadf-7f62cff4a9da
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 00cf7a7fab52640cc3fc19a3d9da051d281be7c2
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783013"
---
# <a name="add-a-secondary-replica-to-an-availability-group-sql-server"></a>Ajouter un réplica secondaire à un groupe de disponibilité (SQL Server)
  Cette rubrique explique comment ajouter un réplica secondaire à un groupe de disponibilité AlwaysOn existant à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou de PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Avant de commencer :**  
  
     [Conditions préalables requises et restrictions](#PrerequisitesRestrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour ajouter un réplica, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Suivi :**  [Après avoir ajouté un réplica secondaire](#FollowUp)  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Nous vous recommandons fortement de lire cette section avant d'essayer de créer votre premier groupe de disponibilité.  
  
##  <a name="PrerequisitesRestrictions"></a> Conditions préalables requises et restrictions  
  
-   Vous devez être connecté à l'instance de serveur qui héberge le réplica principal.  
  
 Pour plus d’informations, consultez [Conditions préalables requises, restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
##  <a name="Security"></a> Sécurité  
  
###  <a name="Permissions"></a> Permissions  
 Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour ajouter un réplica**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica principal et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Cliquez avec le bouton droit sur le groupe de disponibilité, puis sélectionnez l'une des commandes suivantes :  
  
    -   Sélectionnez la commande **Ajouter un réplica** pour lancer l'Assistant Ajouter un réplica au groupe de disponibilité. Pour plus d’informations, consultez [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).  
  
    -   Vous pouvez également sélectionner la commande **Propriétés** pour ouvrir la boîte de dialogue **Propriétés du groupe de disponibilité** . Les étapes permettant d'ajouter un réplica dans cette boîte de dialogue sont les suivantes :  
  
        1.  Dans le volet **Réplicas de disponibilité** de la boîte de dialogue, cliquez sur le bouton **Ajouter** . Cela permet de créer et de sélectionner une entrée de réplica dans laquelle le champ vide d'instance de serveur est sélectionné.  
  
        2.  Entrez le nom d'une instance de serveur qui satisfait aux conditions préalables requises pour héberger un réplica de disponibilité.  
  
         Pour ajouter des réplicas supplémentaires, répétez les étapes précédentes. Lorsque vous avez terminé de spécifier des réplicas, cliquez sur **OK** pour terminer l'opération.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour ajouter un réplica**  
  
1.  Connectez-vous à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui héberge le réplica principal.  
  
2.  Ajoutez le nouveau réplica secondaire au groupe de disponibilité en utilisant la clause ADD REPLICA ON de l'instruction ALTER AVAILABILITY GROUP. Les options ENDPOINT_URL, AVAILABILITY_MODE et FAILOVER_MODE sont requises dans une clause ADD REPLICA ON. Les autres options de réplica, BACKUP_PRIORITY, SECONDARY_ROLE, PRIMARY_ROLE et SESSION_TIMEOUT, sont facultatives. Pour plus d’informations, consultez [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).  
  
     Par exemple, l'instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] suivante crée un réplica dans un groupe de disponibilité nommé `MyAG` sur l'instance de serveur par défaut hébergée par `COMPUTER04`, dont l'URL du point de terminaison est `TCP://COMPUTER04.Adventure-Works.com:5022'`. Ce réplica prend en charge le basculement manuel et le mode de disponibilité avec validation synchrone.  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG ADD REPLICA ON 'COMPUTER04'   
       WITH (  
             ENDPOINT_URL = 'TCP://COMPUTER04.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );  
    ```  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Pour ajouter un réplica**  
  
1.  Accédez au répertoire (`cd`) de l'instance de serveur qui héberge le réplica principal.  
  
2.  Utilisez l’applet de commande **New-SqlAvailabilityReplica** .  
  
     Par exemple, la commande suivante ajoute un réplica de disponibilité à un groupe de disponibilité existant nommé `MyAg`. Ce réplica prend en charge le basculement manuel et le mode de disponibilité avec validation synchrone. Avec le rôle secondaire, ce réplica prendra en charge les connexions d'accès en lecture. Vous pourrez ainsi décharger le traitement en lecture sur ce réplica.  
  
    ```powershell
    $agPath = "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
    $endpointURL = "TCP://PrimaryServerName.domain.com:5022"  
    $failoverMode = "Manual"  
    $availabilityMode = "AsynchronousCommit"  
    $secondaryReadMode = "AllowAllConnections"  
  
    New-SqlAvailabilityReplica -Name SecondaryServer\Instance `   
    -EndpointUrl $endpointURL `   
    -FailoverMode $failoverMode `   
    -AvailabilityMode $availabilityMode `   
    -ConnectionModeInSecondaryRole $secondaryReadMode `   
    -Path $agPath  
    ```  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour plus d’informations, consultez [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [fournisseur PowerShell SQL Server](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="FollowUp"></a> Suivi : Après avoir ajouté un réplica secondaire  
 Pour ajouter un réplica pour un groupe de disponibilité existant, vous devez effectuer les étapes suivantes :  
  
1.  Connectez-vous à l'instance de serveur qui va héberger le nouveau réplica secondaire.  
  
2.  Joignez le nouveau réplica secondaire au groupe de disponibilité. Pour plus d’informations, consultez [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
3.  Pour chaque base de données du groupe de disponibilité, créez une base de données secondaire sur l'instance de serveur qui héberge le réplica secondaire. Pour plus d’informations, consultez [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
4.  Joignez chacune des nouvelles bases de données secondaires au groupe de disponibilité. Pour plus d’informations, consultez [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Tâches connexes  
 **Pour gérer un réplica de disponibilité**  
  
-   [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Supprimer un réplica secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Modifier le mode de disponibilité d’un réplica de disponibilité &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Modifier le mode de basculement d’un réplica de disponibilité &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Modifier le délai d’expiration de session pour un réplica de disponibilité &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [Modifier le délai d’expiration de session pour un réplica de disponibilité &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)   
 [Vue d’ensemble &#40;de&#41; groupes de disponibilité AlwaysOn SQL Server](overview-of-always-on-availability-groups-sql-server.md)   
 [Création et configuration des groupes de disponibilité &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Utilisez le tableau de &#40;bord&#41; AlwaysOn SQL Server Management Studio](use-the-always-on-dashboard-sql-server-management-studio.md)   
 [Surveiller des groupes de disponibilité &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)  
  
  
