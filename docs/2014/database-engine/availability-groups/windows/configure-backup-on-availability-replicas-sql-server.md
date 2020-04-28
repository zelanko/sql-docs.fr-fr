---
title: Configurer la sauvegarde sur des réplicas de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
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
ms.assetid: 74bc40bb-9f57-44e4-8988-1d69c0585eb6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 95f1e2cec530ee65dce60ceea1679281a9d3ba5c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72782997"
---
# <a name="configure-backup-on-availability-replicas-sql-server"></a>Configurer la sauvegarde sur des réplicas de disponibilité (SQL Server)
  Cette rubrique explique comment configurer la sauvegarde sur des réplicas secondaires pour un groupe de disponibilité AlwaysOn à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou de PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Pour une introduction à la sauvegarde sur les réplicas secondaires, consultez secondaires [actifs : sauvegarde sur les réplicas secondaires (groupes de disponibilité AlwaysOn)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).  
  
 
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Vous devez être connecté à l'instance de serveur qui héberge le réplica principal.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
  
|Tâche|Autorisations|  
|----------|-----------------|  
|Pour configurer la sauvegarde sur les réplicas secondaires en créant un groupe de disponibilité|Requiert l’appartenance au rôle serveur fixe **sysadmin** et l’autorisation de serveur CREATE AVAILABILITY GROUP, l’autorisation ALTER ANY AVAILABILITY GROUP ou l’autorisation CONTROL SERVER.|  
|Pour modifier un groupe de disponibilité ou un réplica de disponibilité|Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.|  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour configurer la sauvegarde sur les réplicas secondaires**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica principal, cliquez sur le nom du serveur pour développer l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Cliquez sur le groupe de disponibilité dont vous souhaitez configurer les préférences de sauvegarde et sélectionnez la commande **Propriétés** .  
  
4.  Dans la boîte de dialogue **Propriétés de groupe de disponibilité**, sélectionnez la page **Préférences de sauvegarde**.  
  
5.  Dans le panneau **Où les sauvegardes doivent-elles être effectuées ?** , sélectionnez la préférence de sauvegarde automatisée pour le groupe de disponibilité, parmi les options suivantes :  
  
     **Préférer secondaire**  
     Spécifie que les sauvegardes doivent se produire sur un réplica secondaire sauf lorsque le réplica principal est le seul réplica en ligne. Dans ce cas, la sauvegarde doit se produire sur le réplica principal. Il s'agit de l'option par défaut.  
  
     **Secondaire uniquement**  
     Spécifie que les sauvegardes ne doivent jamais être effectuées sur le réplica principal. Si le réplica principal est le seul réplica en ligne, la sauvegarde ne doit pas avoir lieu.  
  
     `Primary`  
     Spécifie que les sauvegardes doivent toujours avoir lieu sur le réplica principal. Cette option est utile si vous avez besoin de fonctionnalités de sauvegarde, telles que la création de sauvegardes différentielles, qui ne sont pas prises en charge lorsque la sauvegarde est exécutée sur un réplica secondaire.  
  
    > [!IMPORTANT]  
    >  Si vous envisagez d'utiliser la copie de journaux de transaction pour préparer des bases de données secondaires pour un groupe de disponibilité, définissez la préférence de sauvegarde automatique sur `Primary` jusqu'à ce que toutes les bases de données secondaires aient été préparées et attachées au groupe de disponibilité.  
  
     **Tout réplica**  
     Spécifie que vous préférez que les travaux de sauvegarde ignorent le rôle des réplicas de disponibilité lorsque vous choisissez le réplica pour effectuer les sauvegardes. Notez que les travaux de sauvegarde peuvent évaluer d'autres facteurs tels que la priorité de sauvegarde de chaque réplica de disponibilité en association avec son état opérationnel et son état connecté.  
  
    > [!IMPORTANT]  
    >  Il n'y a aucune mise en application du paramètre de préférence de sauvegarde automatisée. La traduction de cette préférence dépend de la logique, le cas échéant, que vous avez écrite dans les travaux de sauvegarde pour les bases de données dans un groupe de disponibilité donné. Le paramètre de préférence de sauvegarde automatisée n'a aucun impact sur les sauvegardes ad-hoc. Pour plus d’informations, consultez [suivi : après avoir configuré la sauvegarde sur les réplicas secondaires](#FollowUp) , plus loin dans cette rubrique.  
  
6.  Utilisez la grille **Priorités de sauvegarde de réplica** pour modifier la priorité de sauvegarde des réplicas de disponibilité. Cette grille affiche la priorité de sauvegarde actuelle de chaque instance de serveur qui héberge un réplica pour le groupe de disponibilité. Les colonnes de la grille sont les suivantes :  
  
     **Instance de serveur**  
     Nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui héberge le réplica de disponibilité.  
  
     **Priorité de sauvegarde (Minimale=1, Maximale=100)**  
     Spécifie la priorité d'exécution des sauvegardes sur ce réplica par rapport aux autres réplicas dans le même groupe de disponibilité. La valeur est un entier compris entre 0 et 100. 1 indique la priorité la plus faible, 100 la priorité la plus élevée. Si **Priorité de sauvegarde** = 1, le réplica de disponibilité est choisi pour l'exécution des sauvegardes uniquement si aucun réplica de disponibilité ayant une priorité plus élevée n'est actuellement disponible.  
  
     **Exclure le réplica**  
     Sélectionnez cette option si vous ne souhaitez jamais que ce réplica de disponibilité soit choisi pour effectuer des sauvegardes. Cela est utile, par exemple, pour un réplica de disponibilité distant sur lequel vous ne souhaitez jamais basculer de sauvegardes.  
  
7.  Cliquez sur **OK**pour valider vos modifications.  
  
 **Autres manières d'accéder à la page des préférences de sauvegarde**  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour configurer la sauvegarde sur les réplicas secondaires**  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica principal.  
  
2.  Pour un nouveau groupe de disponibilité, utilisez l’instruction [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql). Si vous modifiez un groupe de disponibilité existant, utilisez l’instruction [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Utilisation de PowerShell  

### <a name="to-configure-backup-on-secondary-replicas"></a>Pour configurer la sauvegarde sur les réplicas secondaires
  
1.  Définissez la valeur par défaut (`cd`) sur l'instance de serveur qui héberge le réplica principal.  
  
2.  Éventuellement, configurez la priorité de sauvegarde de chaque réplica de disponibilité que vous ajoutez ou modifiez. Cette priorité est utilisée par l'instance de serveur qui héberge le réplica principal pour décider quel réplica doit traiter une demande de sauvegarde automatique sur une base de données dans le groupe de disponibilité (le réplica avec la priorité la plus élevée est choisi). Cette priorité peut être tout nombre compris entre 0 et 100 (inclus). Une priorité de 0 indique que le réplica ne doit pas être considéré comme candidat pour le traitement des demandes de sauvegarde.  La valeur par défaut est 50.  
  
     Lorsque vous ajoutez un réplica de disponibilité à un groupe de disponibilité, utilisez l'applet de commande `New-SqlAvailabilityReplica`. Lorsque vous modifiez un réplica de disponibilité existant, utilisez l'applet de commande `Set-SqlAvailabilityReplica`. Dans les deux cas, spécifiez le `BackupPriority`paramètre *n* , où *n* est une valeur comprise entre 0 et 100.  
  
     Par exemple, la commande suivante définit la priorité de sauvegarde du réplica de disponibilité `MyReplica` à `60`.  
  
    ```powershell
    Set-SqlAvailabilityReplica -BackupPriority 60 -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
3.  Éventuellement, configurez la préférence de sauvegarde automatique pour le groupe de disponibilité que vous créez ou modifiez. Cette préférence indique la manière dont un travail de sauvegarde doit évaluer le réplica principal lorsqu'on choisit où effectuer des sauvegardes. Le paramètre par défaut est de préférer les réplicas secondaires.  
  
     Lors de la création d'un groupe de disponibilité, utilisez l'applet de commande `New-SqlAvailabilityGroup`. Lorsque vous modifiez un groupe de disponibilité existant, utilisez l'applet de commande `Set-SqlAvailabilityGroup`. Dans les deux cas, spécifiez le paramètre `AutomatedBackupPreference`.  
  
     où :  
  
     `Primary`  
     Spécifie que les sauvegardes doivent toujours avoir lieu sur le réplica principal. Cette option est utile si vous avez besoin de fonctionnalités de sauvegarde, telles que la création de sauvegardes différentielles, qui ne sont pas prises en charge lorsque la sauvegarde est exécutée sur un réplica secondaire.  
  
    > [!IMPORTANT]  
    >  Si vous envisagez d'utiliser la copie de journaux de transaction pour préparer des bases de données secondaires pour un groupe de disponibilité, définissez la préférence de sauvegarde automatique sur `Primary` jusqu'à ce que toutes les bases de données secondaires aient été préparées et attachées au groupe de disponibilité.  
  
     `SecondaryOnly`  
     Spécifie que les sauvegardes ne doivent jamais être effectuées sur le réplica principal. Si le réplica principal est le seul réplica en ligne, la sauvegarde ne doit pas avoir lieu.  
  
     `Secondary`  
     Spécifie que les sauvegardes doivent se produire sur un réplica secondaire sauf lorsque le réplica principal est le seul réplica en ligne. Dans ce cas, la sauvegarde doit se produire sur le réplica principal. Il s'agit du comportement par défaut.  
  
     `None`  
     Spécifie que vous préférez que les travaux de sauvegarde ignorent le rôle des réplicas de disponibilité lorsque vous choisissez le réplica pour effectuer les sauvegardes. Notez que les travaux de sauvegarde peuvent évaluer d'autres facteurs tels que la priorité de sauvegarde de chaque réplica de disponibilité en association avec son état opérationnel et son état connecté.  
  
    > [!IMPORTANT]  
    >  Aucune application de `AutomatedBackupPreference`. La traduction de cette préférence dépend de la logique, le cas échéant, que vous avez écrite dans les travaux de sauvegarde pour les bases de données dans un groupe de disponibilité donné. Le paramètre de préférence de sauvegarde automatisée n'a aucun impact sur les sauvegardes ad-hoc. Pour plus d’informations, consultez [suivi : après avoir configuré la sauvegarde sur les réplicas secondaires](#FollowUp) , plus loin dans cette rubrique.  
  
     Par exemple, la commande suivante définit la propriété `AutomatedBackupPreference` sur le groupe de disponibilité `MyAg` à `SecondaryOnly`. Les sauvegardes automatiques des bases de données dans ce groupe de disponibilité ne se produiront jamais sur le réplica principal, mais seront redirigées vers le réplica secondaire avec la priorité de sauvegarde la plus élevée.  
  
    ```powershell
    Set-SqlAvailabilityGroup -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `  
     -AutomatedBackupPreference SecondaryOnly  
    ```  
  
> [!NOTE]  
>  Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
Pour configurer et utiliser le fournisseur de SQL Server PowerShell, consultez [SQL Server PowerShell fournisseur](../../../powershell/sql-server-powershell-provider.md) et [obtenir de l’aide SQL Server PowerShell](../../../powershell/sql-server-powershell.md).
  
##  <a name="follow-up-after-configuring-backup-on-secondary-replicas"></a><a name="FollowUp"></a>Suivi : après la configuration de la sauvegarde sur les réplicas secondaires  
 Pour prendre en compte la préférence de sauvegarde automatisée pour un groupe de disponibilité donné, sur chaque instance de serveur qui héberge un réplica de disponibilité dont la priorité de sauvegarde est supérieure à zéro (>0), vous avez besoin de créer un script pour les travaux de sauvegarde des bases de données du groupe de disponibilité. Pour déterminer si le réplica actuel est le réplica de sauvegarde par défaut, utilisez la fonction [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) dans votre script de sauvegarde. Si le réplica de disponibilité hébergé par l'instance de serveur actuelle est le réplica par défaut des sauvegardes, cette fonction retourne la valeur 1. Dans le cas contraire, la fonction retourne la valeur 0. En exécutant un simple script sur chaque réplica de disponibilité qui interroge cette fonction, vous pouvez déterminer quel réplica doit exécuter un travail de sauvegarde donné. Par exemple, un extrait de code classique d'un script de travail de sauvegarde se présenterait comme suit :  
  
```  
IF (NOT sys.fn_hadr_backup_is_preferred_replica(@DBNAME))  
BEGIN  
      Select 'This is not the preferred replica, exiting with success';  
      RETURN 0 - This is a normal, expected condition, so the script returns success  
END  
BACKUP DATABASE @DBNAME TO DISK=<disk>  
   WITH COPY_ONLY;  
```  
  
 L'écriture d'un script de travail de sauvegarde à l'aide de cette logique vous permet de planifier le travail à exécuter sur chaque réplica de disponibilité sur la même planification. Chacun de ces travaux recherche les mêmes données pour déterminer quel est le travail à exécuter, de sorte qu'un seul des travaux planifiés passe à l'étape de sauvegarde.  En cas de basculement, aucun des scripts ou des travaux ne doit être modifié. De plus, si vous reconfigurez un groupe de disponibilité afin d'ajouter un réplica de disponibilité, la gestion du travail de sauvegarde nécessite simplement la copie ou la planification du travail de sauvegarde. Si vous supprimez un réplica de disponibilité, supprimez simplement le travail de sauvegarde de l'instance de serveur qui a hébergé ce réplica.  
  
> [!TIP]  
>  Si vous utilisez l’[Assistant Plan de maintenance](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)pour créer un travail de sauvegarde donné, le travail inclut automatiquement la logique de script qui appelle et vérifie la fonction **sys.fn_hadr_backup_is_preferred_replica** . Cependant, le travail de sauvegarde ne va pas retourner le message indiquant qu’il ne s’agit pas du réplica par défaut. Veillez donc à créer le ou les travaux pour chaque base de données de disponibilité sur chacune des instances de serveur qui hébergent un réplica de disponibilité pour le groupe de disponibilité.  
  
##  <a name="to-obtain-information-about-backup-preference-settings"></a><a name="ForInfoAboutBuPref"></a>Pour obtenir des informations sur les paramètres de préférence de sauvegarde  
 Voici des ressources utiles pour obtenir des informations pertinentes sur la sauvegarde de réplicas secondaires.  
  
|Affichage|Information|Colonnes appropriées|  
|----------|-----------------|----------------------|  
|[sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)|Le réplica actuel est-il le réplica de sauvegarde par défaut ?|Non applicable.|  
|[sys.availability_groups](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)|préférence de sauvegarde automatisée|**automated_backup_preference**<br /><br /> **automated_backup_preference_desc**|  
|[sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)|Priorité de sauvegarde d'un réplica de disponibilité donné|**backup_priority**|  
|[sys.dm_hadr_availability_replica_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)|Le réplica est-il locale sur l'instance de serveur ?<br /><br /> Rôle actuel<br /><br /> État opérationnel<br /><br /> Étata connecté<br /><br /> Intégrité de synchronisation d'un réplica de disponibilité|**is_local**<br /><br /> **role**, **role_desc**<br /><br /> **operational_state**, **operational_state_desc**<br /><br /> **connected_state**, **connected_state_desc**<br /><br /> **synchronization_health**, **synchronization_health_desc**|  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenu associé  
  
-   [Guide de solutions Microsoft SQL Server AlwaysOn pour la haute disponibilité et la récupération d'urgence](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [Blog de l'équipe de SQL Server AlwaysOn : Blog officiel de l'équipe de SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Secondaires actifs : sauvegarde sur les réplicas secondaires (groupes de disponibilité d'AlwaysOn)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) 
