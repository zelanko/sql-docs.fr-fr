---
title: Créer un groupe de disponibilité (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: bc69a7df-20fa-41e1-9301-11317c5270d2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8085fa23357c5901ed350e81410ae4d38a3005dd
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228796"
---
# <a name="create-an-availability-group-sql-server-powershell"></a>Créer un groupe de disponibilité (SQL Server PowerShell)
  Cette rubrique explique comment utiliser des applets de commande PowerShell pour créer et configurer un groupe de disponibilité AlwaysOn à l'aide de PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Un *groupe de disponibilité* définit un jeu de bases de données utilisateur qui basculent en tant qu'unité unique et un jeu de partenaires de basculement, appelés *réplicas de disponibilité*, qui prennent en charge le basculement.  
  
> [!NOTE]  
>  Pour obtenir une présentation des groupes de disponibilité, consultez [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  

> [!NOTE]  
>  Comme alternative à l'utilisation des applets de commande PowerShell, vous pouvez utiliser l'Assistant Création d'un groupe de disponibilité ou [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Pour plus d’informations, consultez [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) ou [Créer un groupe de disponibilité &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).  
  
##  <a name="BeforeYouBegin"></a>Avant de commencer  
 Nous vous recommandons fortement de lire cette section avant d'essayer de créer votre premier groupe de disponibilité.  
  
###  <a name="PrerequisitesRestrictions"></a>Conditions préalables requises, restrictions et recommandations  
  
-   Avant de créer un groupe de disponibilité, vérifiez que les instances hôtes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] résident chacune sur un nœud WSFC (Clustering de basculement Windows Server) différent au sein du même clustering de basculement WSFC. En outre, vérifiez que vos instances de serveur respectent les autres conditions préalables applicables, que toutes les autres spécifications [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sont respectées et que vous avez pris note des recommandations. Pour plus d’informations, nous vous conseillons vivement de lire la rubrique [Conditions préalables requises, restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="Security"></a>Caution  
  
####  <a name="Permissions"></a>Autorisations  
 Requiert l’appartenance au rôle serveur fixe **sysadmin** et l’autorisation de serveur CREATE AVAILABILITY GROUP, l’autorisation ALTER ANY AVAILABILITY GROUP ou l’autorisation CONTROL SERVER.  
  
###  <a name="SummaryPSStatements"></a>Résumé des tâches et applets de commande PowerShell correspondantes  
 Le tableau suivant répertorie les tâches de base impliquées dans la configuration d'un groupe de disponibilité et indique celles qui sont prises en charge par les applets de commande PowerShell. Les tâches [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] doivent être effectuées dans la séquence dans laquelle elles sont présentées dans le tableau.  
  
|Tâche|Applets de commande PowerShell (le cas échéant) ou instruction Transact-SQL|Où effectuer la tâche**<sup>*</sup>**|  
|----------|--------------------------------------------------------------------|-------------------------------------------|  
|Créer le point de terminaison de mise en miroir de bases de données (une fois par instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] )|`New-SqlHadrEndPoint`|Exécutez sur chaque instance de serveur dans laquelle le point de terminaison de mise en miroir de bases de données est manquant.<br /><br /> Remarque : pour modifier un point de terminaison de mise en miroir de bases de données existant, utilisez `Set-SqlHadrEndpoint`.|  
|Créer un groupe de disponibilité|En premier lieu, utilisez l'applet de commande `New-SqlAvailabilityReplica` avec le paramètre `-AsTemplate` pour créer un objet réplica de disponibilité en mémoire pour chacun des deux réplicas de disponibilité que vous envisagez d'inclure dans le groupe de disponibilité.<br /><br /> Puis, créez le groupe de disponibilité en utilisant l'applet de commande `New-SqlAvailabilityGroup` et en référençant vos objets réplica de disponibilité.|Exécutez sur l'instance de serveur qui hébergera le réplica principal initial.|  
|Joindre le réplica secondaire au groupe de disponibilité|`Join-SqlAvailabilityGroup`|Exécutez sur chaque instance de serveur qui héberge un réplica secondaire.|  
|Préparer la base de données secondaire|`Backup-SqlDatabase`les`Restore-SqlDatabase`|Créez des sauvegardes sur l'instance de serveur qui héberge le réplica principal.<br /><br /> Restaurez les sauvegardes sur chaque instance de serveur qui héberge un réplica secondaire, à l'aide du paramètre de restauration `NoRecovery`. Si les chemins d'accès de fichier diffèrent entre les ordinateurs qui hébergent le réplica principal et le réplica secondaire cible, utilisez également le paramètre de restauration `RelocateFile`.|  
|Démarrer la synchronisation des données en joignant chaque base de données secondaire au groupe de disponibilité|`Add-SqlAvailabilityDatabase`|Exécutez sur chaque instance de serveur qui héberge un réplica secondaire.|  
  
 **<sup>*</sup>** Pour effectuer une tâche donnée, remplacez le répertoire`cd`() par l’instance ou les instances de serveur indiquées.  
  
###  <a name="PsProviderLinks"></a>Pour configurer et utiliser le fournisseur SQL Server PowerShell  
  
-   [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Obtenir de l’aide SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="PowerShellProcedure"></a>Utilisation de PowerShell pour créer et configurer un groupe de disponibilité  
  
> [!NOTE]  
>  Pour afficher la syntaxe et un exemple d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement PowerShell [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
1.  Accédez au répertoire (`cd`) de l'instance de serveur qui héberge le réplica principal.  
  
2.  Créez un objet réplica de disponibilité en mémoire pour le réplica principal.  
  
3.  Créez un objet réplica de disponibilité en mémoire pour chacun des réplicas secondaires.  
  
4.  Créez le groupe de disponibilité.  
  
    > [!NOTE]  
    >  La longueur maximale d'un nom de groupe de disponibilité est de 128 caractères.  
  
5.  Joignez le nouveau réplica secondaire au groupe de disponibilité. Pour plus d’informations, consultez [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
6.  Pour chaque base de données dans le groupe de disponibilité, créez une base de données secondaire en restaurant des sauvegardes récentes de la base de données primaire, à l'aide de RESTORE WITH NORECOVERY.  
  
7.  Joignez chaque nouvelle base de données secondaire au groupe de disponibilité. Pour plus d’informations, consultez [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
8.  Éventuellement, utilisez la commande `dir` Windows pour vérifier le contenu du nouveau groupe de disponibilité.  
  
> [!NOTE]  
>  Si les comptes de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des instances serveur s'exécutent sous des comptes utilisateur de domaine différents, sur chaque instance serveur, créez une connexion pour l'autre instance serveur et accordez l'autorisation CONNECT sur le point de terminaison de mise en miroir de bases de données local.  
  
##  <a name="ExampleConfigureGroup"></a>Exemple : utilisation de PowerShell pour créer un groupe de disponibilité  
 L'exemple PowerShell suivant crée et configure un groupe de disponibilité simple nommé `MyAG` avec deux réplicas de disponibilité et une base de données de disponibilité. L'exemple :  
  
1.  Sauvegarde `MyDatabase` et son journal des transactions.  
  
2.  Restaure `MyDatabase` et son journal des transactions, à l'aide de l'option `-NoRecovery`.  
  
3.  Crée une représentation en mémoire du réplica principal, qui sera hébergée par l'instance locale de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (nommée `PrimaryComputer\Instance`).  
  
4.  Crée une représentation en mémoire du réplica secondaire, qui sera hébergée par une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (nommée `SecondaryComputer\Instance`).  
  
5.  Crée un groupe de disponibilité nommé `MyAG`.  
  
6.  Joint le réplica secondaire au groupe de disponibilité.  
  
7.  Joint la base de données secondaire au groupe de disponibilité.  
  
```powershell
# Backup my database and its log on the primary  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "PrimaryComputer\Instance"  
  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "PrimaryComputer\Instance" `  
    -BackupAction Log   
  
# Restore the database and log on the secondary (using NO RECOVERY)  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -NoRecovery  
  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -RestoreAction Log `  
    -NoRecovery  
  
# Create an in-memory representation of the primary replica.  
$primaryReplica = New-SqlAvailabilityReplica `  
    -Name "PrimaryComputer\Instance" `  
    -EndpointURL "TCP://PrimaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create an in-memory representation of the secondary replica.  
$secondaryReplica = New-SqlAvailabilityReplica `  
    -Name "SecondaryComputer\Instance" `  
    -EndpointURL "TCP://SecondaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create the availability group  
New-SqlAvailabilityGroup `  
    -Name "MyAG" `  
    -Path "SQLSERVER:\SQL\PrimaryComputer\Instance" `  
    -AvailabilityReplica @($primaryReplica,$secondaryReplica) `  
    -Database "MyDatabase"  
  
# Join the secondary replica to the availability group.  
Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryComputer\Instance" -Name "MyAG"  
  
# Join the secondary database to the availability group.  
Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryComputer\Instance\AvailabilityGroups\MyAG" -Database "MyDatabase"  
```  
  
##  <a name="RelatedTasks"></a>Tâches associées  
 **Pour configurer une instance de serveur pour les groupes de disponibilité AlwaysOn**  
  
-   [Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [Créer un point de terminaison de mise en miroir de bases de données pour groupes de disponibilité AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
 **Pour configurer les propriétés du groupe de disponibilité et du réplica**  
  
-   [Modifier le mode de disponibilité d’un réplica de disponibilité &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Modifier le mode de basculement d’un réplica de disponibilité &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Créez ou configurez un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Configurer la stratégie de basculement flexible pour contrôler les conditions du basculement automatique (groupes de disponibilité AlwaysOn)](configure-flexible-automatic-failover-policy.md)  
  
-   [Spécifiez l’URL du point de terminaison lors de l’ajout ou de la modification d’un réplica de disponibilité &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Configurez la sauvegarde sur les réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Configurez l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Configurer le routage en lecture seule pour un groupe de disponibilité &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Modifiez le délai d’expiration de session pour un réplica de disponibilité &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **Pour terminer la configuration du groupe de disponibilité**  
  
-   [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Créez ou configurez un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Autres manières de créer un groupe de disponibilité**  
  
-   [Utilisez l’Assistant groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utilisez la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Créer un groupe de disponibilité &#40;&#41;Transact-SQL](create-an-availability-group-transact-sql.md)  
  
 **Pour résoudre les problèmes de configuration des groupes de disponibilité AlwaysOn**  
  
-   [Résoudre les problèmes de configuration de groupes de disponibilité AlwaysOn (SQL Server)](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Résoudre les problèmes liés à l’échec d’une opération d’ajout de fichier &#40;groupes de disponibilité AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a>Contenu connexe  
  
-   **Blogs**  
  
     [AlwaysON - HADRON Learning Series : Worker Pool Usage for HADRON Enabled Databases (en anglais)](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Configuration d'AlwaysOn avec SQL Server PowerShell](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/configuring-alwayson-with-sql-server-powershell.aspx)  
  
     [Blogs de l'équipe de SQL Server AlwaysOn : Blog officiel de l'équipe de SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs des ingénieurs SQL Servers CSS](https://blogs.msdn.com/b/psssql/)  
  
-   **Vidéos**  
  
     [Microsoft SQL Server, nom de code « Denali », série AlwaysOn, Partie 1 : Présentation de la solution haute disponibilité de la prochaine génération](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server, nom de code « Denali », série AlwaysOn, Partie 2 : Génération d'une solution haute disponibilité critique à l'aide d'AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Livres**  
  
     [Guide de solutions Microsoft SQL Server AlwaysOn pour la haute disponibilité et la récupération d'urgence](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Livres blancs Microsoft pour SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Livres blancs de l’équipe de conseil clientèle SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Voir aussi  
 [Le point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
