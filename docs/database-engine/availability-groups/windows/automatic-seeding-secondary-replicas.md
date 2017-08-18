---
title: "Amorçage automatique pour les réplicas secondaires (SQL Server) | Microsoft Docs"
description: "Utilisez l’amorçage automatique pour initialiser les réplicas secondaires."
services: data-lake-analytics
ms.custom: 
ms.date: 06/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Automatic seeding [SQL Server], secondary replica
ms.assetid: 
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1b72f9f5bf58f72bb4284b1a6cc8d0af7a722aed
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="automatic-seeding-for-secondary-replicas"></a>Amorçage automatique pour les réplicas secondaires

[!INCLUDE [tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Dans SQL Server 2012 et 2014, la seule façon d’initialiser un réplica secondaire dans un groupe de disponibilité est d’utiliser la sauvegarde, la copie et la restauration. SQL Server 2016 introduit une nouvelle fonctionnalité pour initialiser un réplica secondaire, *l’amorçage automatique*. L’amorçage automatique utilise le transport de flux de journaux pour transmettre en continu la sauvegarde à l’aide de VDI vers le réplica secondaire pour chaque base de données du groupe de disponibilité, en utilisant les points de terminaison configurés. Cette nouvelle fonctionnalité peut être utilisée lors de la création initiale d’un groupe de disponibilité ou quand une base de données lui est ajoutée. L’amorçage automatique est disponible dans toutes les éditions de SQL Server prenant en charge les groupes de disponibilité Always On et peut être utilisé avec les groupes de disponibilité traditionnels et les [groupes de disponibilité distribués](distributed-availability-groups.md).

## <a name="considerations"></a>Observations

Voici des considérations sur l’utilisation de l’amorçage automatique :

* [Impact en termes de performances et de journal des transactions sur le réplica principal](#performance-and-transaction-log-impact-on-the-primary-replica)
* [Disposition du disque](#disk-layout)
* [Sécurité](#security)


### <a name="performance-and-transaction-log-impact-on-the-primary-replica"></a>Impact en termes de performances et de journal des transactions sur le réplica principal

L’amorçage automatique peut ou non être pratique pour initialiser un réplica secondaire, selon la taille de la base de données, la vitesse du réseau, et la distance entre le réplica principal et les réplicas secondaires. Prenons l’exemple suivant :

* La taille de la base de données est de 5 To.
* La vitesse du réseau est de 1 Gbit/s.
* La distance entre les deux sites est de 1 600 kilomètres.

Un réseau à 1 Gbit/s peut fournir un débit constant de 125 Mo par seconde si toute la bande passante est disponible. Dans cet exemple, l’amorçage automatique prendrait un peu plus de 11 heures. Dans la pratique, le processus d’amorçage automatique est un peu plus lent, car le signal sur le réseau se dégrade sur les longues distances et la liaison est habituellement partagée avec d’autres ressources du réseau. Pendant l’amorçage, le journal des transactions sur la base de données du réplica principal continue de croître et il ne peut pas être tronqué tant que l’amorçage automatique de cette base de données n’est pas terminé.  Le journal des transactions peut ensuite être tronqué via une sauvegarde du journal des transactions.

L’amorçage automatique est un processus monothread qui peut gérer jusqu’à cinq bases de données. Ceci peut affecter les performances, surtout si le groupe de disponibilité a plusieurs bases de données.

La compression peut être utilisée pour l’amorçage automatique, mais elle est désactivée par défaut. L’activation de la compression réduit la bande passante réseau et accélère éventuellement le processus, mais l’inconvénient est une charge supplémentaire pour le processeur. Pour utiliser la compression pendant l’amorçage automatique, activez l’indicateur de trace 9567. Consultez [Régler la compression pour un groupe de disponibilité](tune-compression-for-availability-group.md).

### <a name="disk-layout"></a>Disposition du disque

Le dossier où la base de données sera créée par l’amorçage automatique doit déjà exister et avoir le même chemin que sur le réplica principal.

### <a name="security"></a>Sécurité

Les autorisations de sécurité varient selon le type de réplica à initialiser :

* Pour un groupe de disponibilité traditionnel, les autorisations doivent être accordées au groupe de disponibilité sur le réplica secondaire quand il est joint au groupe de disponibilité. Dans Transact-SQL, utilisez la commande ALTER AVAILABILITY GROUP [nom_groupe_de_disponibilité] GRANT CREATE ANY DATABASE.
* Pour un groupe de disponibilité distribué où les bases de données du réplica à créer sont sur le réplica principal du deuxième groupe de disponibilité, aucune autorisation supplémentaire n’est nécessaire, car il s’agit déjà d’un réplica principal.
* Pour un réplica secondaire sur le deuxième groupe de disponibilité d’un groupe de disponibilité distribué, vous devez utiliser la commande ALTER AVAILABILITY GROUP [nom_deuxième_groupe_de_disponibilité] GRANT CREATE ANY DATABASE. Ce réplica secondaire est amorcé à partir du réplica principal du deuxième groupe de disponibilité.

## <a name="create-an-availability-group-with-automatic-seeding"></a>Créer un groupe de disponibilité par amorçage automatique

Vous créez un groupe de disponibilité par amorçage automatique avec Transact-SQL ou SQL Server Management Studio (SSMS, version 17 ou ultérieure). Pour utiliser l’Assistant Groupe de disponibilité dans SSMS, suivez [ces instructions](use-the-availability-group-wizard-sql-server-management-studio.md). Quand vous arrivez à l’étape 9, vous voyez l’amorçage automatique comme première option (et aussi comme option par défaut).

![Sélectionner la synchronisation de données initiale][1]

L’exemple suivant crée un groupe de disponibilité avec Transact-SQL. Consultez aussi la rubrique [Créer un groupe de disponibilité (Transact-SQL)](create-an-availability-group-transact-sql.md). L’amorçage est activé sur un réplica secondaire en définissant l’option SEEDING_MODE sur AUTOMATIC. Le comportement par défaut est MANUAL, qui est le comportement des versions antérieures à SQL Server 2016 nécessitant la réalisation d’une sauvegarde de la base de données sur le réplica principal, la copie du fichier de sauvegarde sur le réplica secondaire et la restauration de la sauvegarde WITH NORECOVERY.

```
CREATE AVAILABILITY GROUP [AGName]
  FOR DATABASE db1
  REPLICA ON N'Primary_Replica'
WITH (
  ENDPOINT_URL = N'TCP://Primary_Replica.Contoso.com:5022', 
  FAILOVER_MODE = AUTOMATIC, 
  AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
),
  N'Secondary_Replica' WITH (
    ENDPOINT_URL = N'TCP://Secondary_Replica.Contoso.com :5022', 
    FAILOVER_MODE = AUTOMATIC, 
    SEEDING_MODE = AUTOMATIC);
 GO
```

La définition de SEEDING_MODE sur un réplica principal pendant une instruction CREATE AVAILABILITY GROUP n’a pas d’effet, car le réplica principal contient déjà la copie principale en lecture/écriture de la base de données. SEEDING_MODE peut s’appliquer seulement quand un autre réplica a été changé en réplica principal et qu’une base de données a été ajoutée. Le mode d’amorçage peut être changé ultérieurement. Consultez [Changer le mode d’amorçage d’un réplica](#change-the-seeding-mode-of-a-replica).

Sur une instance qui devient un réplica secondaire, une fois que l’instance est jointe, le message suivant est ajouté dans le journal SQL Server :

Le réplica de disponibilité local pour le groupe de disponibilité « nom_groupe_de_disponibilité » n’a pas reçu l’autorisation de créer des bases de données, mais son paramètre SEEDING_MODE est défini sur AUTOMATIC. Utilisez la commande ALTER AVAILABILITY GROUP… GRANT CREATE ANY DATABASE pour autoriser la création de bases de données amorcée par le réplica de disponibilité principal.

Après la jonction, lancez l’instruction suivante :

```
ALTER AVAILABILITY GROUP [AGName] GRANT CREATE ANY DATABASE
 GO
````

> [!NOTE] 
> Il existe actuellement un problème connu dans SQL Server 2016 SP1 CU2, où un réplica secondaire doit attendre trois minutes pour permettre au groupe de disponibilité d’amorcer la base de données avant d’exécuter une instruction ALTER AVAILABILITY GROUP... Avant ce délai, l’instruction ne retourne pas d’erreur et indique à la place une réussite de l’opération. Ceci est également un problème connu. Ces problèmes seront corrigés dans une prochaine mise à jour de SQL Server. Pour contourner ce problème, insérez une instruction WAITFOR :

```
WAITFOR DELAY '00:03:15';
ALTER AVAILABILITY GROUP [AGName] GRANT CREATE ANY DATABASE;
GO
```

En cas de réussite, la ou les bases de données sont créées automatiquement sur le réplica secondaire avec un état qui peut être :

* SYNCHRONIZED si le réplica secondaire est configuré pour être synchrone et que les données sont complètement synchronisées.
* SYNCHRONIZING si le réplica secondaire est configuré avec le déplacement des données asynchrones, ou quand il est configuré pour être synchrone mais n’est pas encore synchronisé avec le réplica principal.

<a name="sql-server-log"></a> En plus des [vues de gestion dynamiques](#dynamic-management-views) décrites ci-dessous, le démarrage et l’achèvement de l’amorçage automatique figurent dans le journal SQL Server :

![Journal SQL Server][2]

## <a name="combine-backup-and-restore-with-automatic-seeding"></a>Combiner la sauvegarde et la restauration avec l’amorçage automatique

Il est possible de combiner la sauvegarde, la copie et la restauration traditionnelles avec l’amorçage automatique. Dans ce cas, restaurez d’abord la base de données sur un réplica secondaire, y compris tous les journaux de transactions disponibles. Ensuite, activez l’amorçage automatique lors de la création du groupe de disponibilité pour « rattraper »la base de données du réplica secondaire, comme si une sauvegarde de la fin du journal était restaurée (consultez [Sauvegardes de la fin du journal (SQL Server)](../../../relational-databases/backup-restore/tail-log-backups-sql-server.md)).

## <a name="add-a-database-to-an-availability-group-with-automatic-seeding"></a>Ajouter une base de données à un groupe de disponibilité par amorçage automatique

Vous pouvez ajouter une base de données à un groupe de disponibilité par amorçage automatique avec Transact-SQL ou SQL Server Management Studio (SSMS, version 17 ou ultérieure).
Si le réplica secondaire a utilisé l’amorçage automatique quand il a été ajouté au groupe de disponibilité, aucune opération supplémentaire ne doit être effectuée. Si la sauvegarde, la copie et la restauration ont été utilisées, changez d’abord le mode d’amorçage (voir la section suivante) puis, lors de l’ajout de la base de données, utilisez l’instruction GRANT. Consultez [Groupe de disponibilité - Ajouter une base de données](availability-group-add-a-database.md).

## <a name="change-the-seeding-mode-of-a-replica"></a>Changer le mode d’amorçage d’un réplica

Le mode d’amorçage d’un réplica peut être changé après la création du groupe de disponibilité : l’amorçage automatique peut donc être activé ou désactivé. L’activation de l’amorçage automatique après la création permet de créer une base de données à ajouter au groupe de disponibilité en utilisant l’amorçage automatique si elle a été créée avec la sauvegarde, la copie et la restauration. Exemple :

```
ALTER AVAILABILITY GROUP [AGName]
  MODIFY REPLICA ON 'Replica_Name'
  WITH (SEEDING_MODE = AUTOMATIC)
```

Pour désactiver l’amorçage automatique, utilisez la valeur MANUAL.

## <a name="prevent-automatic-seeding-after-an-availability-group-is-created"></a>Empêcher l’amorçage automatique après la création d’un groupe de disponibilité

Si vous ne souhaitez pas désactiver complètement l’amorçage automatique pour un réplica secondaire, mais que vous voulez empêcher temporairement le réplica secondaire de pouvoir créer automatiquement des bases de données, refuser l’autorisation CREATE au groupe de disponibilité. C’est le cas quand une base de données est ajoutée au groupe de disponibilité, mais que le groupe de disponibilité ne doit pas être autorisé à créer la base de données sur un réplica secondaire.

```
ALTER AVAILABILITY GROUP [AGName] DENY CREATE ANY DATABASE
GO
```

## <a name="monitor-automatic-seeding"></a>Surveiller l’amorçage automatique

Il existe quatre façons de surveiller et de résoudre les problèmes de l’amorçage automatique :

* [Journal SQL Server](#sql-server-log) comme décrit précédemment
* [Vues de gestion dynamique](#dynamic-management-views)
* [Tables d’historique des sauvegardes](#backup-history-tables)
* [Événements étendus](#extended-events)

### <a name="dynamic-management-views"></a>Vues de gestion dynamique

Il existe deux vues de gestion dynamique pour la surveillance de l’amorçage : sys.dm_hadr_automatic_seeding et sys.dm_hadr_physical_seeding_stats.

* sys.dm_hadr_automatic_seeding contient l’état général de l’amorçage automatique et conserve l’historique à chaque fois qu’il est exécuté (qu’il soit ou non réussi). La colonne current_state a la valeur COMPLETED ou FAILED. Si la valeur est FAILED, utilisez la valeur de failure_state_desc pour diagnostiquer le problème. Il peut être nécessaire de combiner ces informations avec celles qui se trouvent dans le [journal SQL Server](#sql-server-log) pour voir ce qui s’est mal déroulé. Cette vue de gestion dynamique contient des données sur le réplica principal et sur tous les réplicas secondaires.

* sys.dm_hadr_physical_seeding_stats indique l’état de l’opération d’amorçage automatique au fil de son exécution. Comme avec sys.dm_hadr_automatic_seeding, les valeurs figurent pour le réplica principal et les réplicas secondaires, mais cet historique n’est pas stocké. Les valeurs concernent seulement l’exécution en cours et ne sont pas conservées. Les colonnes intéressantes sont include start_time_utc, end_time_utc, estimate_time_complete_utc, total_disk_io_wait_time_ms, total_network_wait_time_ms et, si l’opération d’amorçage échoue, failure_message.

### <a name="backup-history-tables"></a>Tables d’historique des sauvegardes

L’amorçage automatique place également des entrées dans les tables `msdb`, qui stockent l’historique pour les sauvegardes et les restaurations. Sur le réplica secondaire qui reçoit l’amorçage automatique, la colonne physical_device_name de la table `backupmediafamily` a comme valeur un GUID, et l’entrée correspondante dans `backupset` a le nom du réplica principal pour server_name and machine_name.

### <a name="extended-events"></a>Événements étendus

L’amorçage automatique ajoute de nouveaux événements étendus pour le suivi des modifications d’état, des échecs et des statistiques de performances lors de l’initialisation.
Par exemple, le script suivant crée une session d’événements étendus qui capture les événements liés à l’amorçage automatique.

```
CREATE EVENT SESSION [AG_autoseed] ON SERVER 
    ADD EVENT sqlserver.hadr_automatic_seeding_state_transition,
    ADD EVENT sqlserver.hadr_automatic_seeding_timeout,
    ADD EVENT sqlserver.hadr_db_manager_seeding_request_msg,
    ADD EVENT sqlserver.hadr_physical_seeding_backup_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_failure,
    ADD EVENT sqlserver.hadr_physical_seeding_forwarder_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_forwarder_target_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_progress,
    ADD EVENT sqlserver.hadr_physical_seeding_restore_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_submit_callback
    ADD TARGET package0.event_file(SET filename=N’autoseed.xel’,max_file_size=(5),max_rollover_files=(4))
  WITH (MAX_MEMORY=4096 KB,EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,MAX_DISPATCH_LATENCY=30 SECONDS,MAX_EVENT_SIZE=0 KB,MEMORY_PARTITION_MODE=NONE,TRACK_CAUSALITY=OFF,STARTUP_STATE=ON)
GO

ALTER EVENT SESSION AlwaysOn_autoseed ON SERVER STATE=START
GO
```

Le tableau suivant répertorie les événements étendus relatifs à l’amorçage automatique.

|Nom|Description|
|----|-----------|
|hadr_db_manager_seeding_request_msg|Message de demande d’amorçage.|
|hadr_physical_seeding_backup_state_change|Modification d’état côté sauvegarde d’amorçage physique.|
|hadr_physical_seeding_restore_state_change|Modification d’état côté restauration d’amorçage physique.|
|hadr_physical_seeding_forwarder_state_change|Modification d’état côté redirecteur d’amorçage physique.|
|hadr_physical_seeding_forwarder_target_state_change|Modification d’état côté cible du redirecteur d’amorçage physique.|
|hadr_physical_seeding_submit_callback|Événement de rappel de soumission d’amorçage physique.|
|hadr_physical_seeding_failure|Événement d’échec d’amorçage physique.|
|hadr_physical_seeding_progress|Événement de progression d’amorçage physique.|
|hadr_physical_seeding_schedule_long_task_failure|Événement d’échec de tâche longue de planification d’amorçage physique.|
|hadr_automatic_seeding_start|Se produit quand une opération d’amorçage automatique est soumise.|
|hadr_automatic_seeding_state_transition|Se produit quand une opération d’amorçage automatique change d’état.|
|hadr_automatic_seeding_success|Se produit quand une opération d’amorçage automatique aboutit.|
|hadr_automatic_seeding_failure|Se produit quand une opération d’amorçage automatique échoue.|
|hadr_automatic_seeding_timeout|Se produit quand une opération d’amorçage automatique expire.|

## <a name="see-also"></a>Voir aussi

[ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql)

[CREATE AVAILABILITY GROUP (Transact-SQL)](https://msdn.microsoft.com/library/ff878399.aspx)

[Guide de surveillance et de résolution des problèmes des groupes de disponibilité Always On](http://technet.microsoft.com/library/dn135328.aspx)

> Ce contenu a été écrit par [Allan Hirt](http://mvp.microsoft.com/en-us/PublicProfile/4025254?fullName=Allan%20Hirt), Microsoft Most Valued Professional.

<!--Image references-->
[1]: ./media/auto-seed-new-availability-group.png
[2]: ./media/auto-seed-sql-server-log.png

