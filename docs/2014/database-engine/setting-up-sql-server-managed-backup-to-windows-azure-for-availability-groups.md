---
title: Configuration de SQL Server Managed Backup dans Windows Azure pour les groupes de disponibilité | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4553cd-d8e4-4691-963a-4e414cc0f1ba
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8a367b7835b08c9a5b2b7226b8f3e4d127235487
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142331"
---
# <a name="setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups"></a>Configuration de la sauvegarde managée de SQL Server sur Windows Azure pour les groupes de disponibilité
  Cette rubrique est un didacticiel sur la configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour les bases de données participant à des groupes de disponibilité AlwaysOn.  
  
## <a name="availability-group-configurations"></a>Configurations de groupe de disponibilité  
 La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est prise en charge pour les bases de données du groupe de disponibilité, que les réplicas soient tous configurés localement, qu'ils soient entièrement sur Windows Azure, ou qu'il s'agisse d'une implémentation hybride sur site et sur une ou plusieurs machines virtuelles Windows Azure. Cependant, tenez compte des éléments suivants pour une ou plusieurs implémentations :  
  
-   Fréquence de sauvegarde du journal : la fréquence de sauvegarde du fichier journal dépend de la croissance du journal au cours d'une plage de temps déterminée. Par exemple, la sauvegarde de fichier journal est effectuée une fois toutes les 2 heures sauf si l'espace de journal utilisé pendant la période de 2 heures est de 5 Mo ou plus. Ceci s'applique à toutes les implémentations, locales, dans le cloud, ou hybrides.  
  
-   Bande passante réseau : ceci s'applique aux implementations où les réplicas se trouvent dans des emplacements physiques différents, comme dans un cloud hybride, ou dans des régions Windows Azure différentes dans une configuration de cloud seul. La bande passante réseau peut affecter la latence des serveurs secondaires, et si les serveurs secondaires sont configurés avec la réplication synchrone, cela peut entraîner une croissance du journal sur le serveur principal. Si les serveurs secondaires utilisent la réplication synchrone, il est possible qu'ils n'arrivent pas à garder le pas en raison du temps de réponse du réseau, ce qui peut entraîner une perte de données en cas de basculement vers le réplica secondaire.  
  
### <a name="configuring-includesssmartbackupincludesss-smartbackup-mdmd-for-availability-databases"></a>Configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour les bases de données de disponibilité  
 **Autorisations :**  
  
-   Nécessite l’appartenance au **db_backupoperator** de la base de données de rôle, avec **ALTER ANY CREDENTIAL** autorisations, et `EXECUTE` autorisations sur **sp_delete_backuphistory**procédure stockée.  
  
-   Requiert **sélectionnez** autorisations sur le **smart_admin.fn_get_current_xevent_settings**(fonction).  
  
-   Requiert `EXECUTE` autorisations sur le **smart_admin.sp_get_backup_diagnostics** procédure stockée. En outre, nécessite les autorisations `VIEW SERVER STATE`, car elle appelle en interne d'autres objets système qui nécessitent cette autorisation.  
  
-   Requiert `EXECUTE` autorisations sur le `smart_admin.sp_set_instance_backup` et `smart_admin.sp_backup_master_switch` des procédures stockées.  
  
 Les étapes de base de configuration d'un groupe de disponibilité AlwaysOn avec la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sont les suivantes. Un didacticiel pas à pas détaillé est décrit plus loin dans cette rubrique.  
  
1.  Une fois que vous avez créé le groupe de disponibilité, configurez le réplica de sauvegarde par défaut. Ce paramètre du groupe de disponibilité est également utilisé par la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour déterminer quel réplica utiliser pour la sauvegarde. Pour obtenir des instructions étape par étape sur la façon de configurer la préférence de sauvegarde, consultez [configurer la sauvegarde sur les réplicas de disponibilité &#40;SQL Server&#41;](availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  Si vous créez un nouveau groupe de disponibilité AlwaysOn, consultez [mise en route avec les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md).  
  
2.  Configurez l'accès à la connexion en lecture seule sur les réplicas secondaires. Pour obtenir des instructions étape par étape sur la configuration accès en lecture seule, consultez [configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
3.  Spécifiez le réplica de sauvegarde. Le paramètre du réplica de sauvegarde par défaut est utilisé par la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour déterminer quelle base de données utiliser pour planifier les sauvegardes.  Pour déterminer si le réplica actuel est le réplica de sauvegarde par défaut, utilisez le [sys.fn_hadr_backup_is_preferred_replica &#40;Transact-SQL&#41; ](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) (fonction).  
  
4.  Sur chaque réplica, exécutez [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration pour la base de données à l’aide de la **à puce-admin.sp_set_db_backup** procédure stockée.  
  
     **[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] comportement après un basculement :** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] continuera à fonctionner et de conserver des copies de sauvegarde et de récupération après un événement de basculement. Aucune action spécifique n'est requise après un basculement.  
  
#### <a name="considerations-and-requirements"></a>Conditions requises et éléments à prendre en compte :  
 La configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour des bases de données participant à un groupe de disponibilité AlwaysOn nécessite des conditions spécifiques. Voici la liste des éléments à prendre en considération et des conditions requises :  
  
-   Les paramètres de configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] doivent être identiques pour toutes les bases de données sur tous les nœuds de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui participent au même groupe de disponibilité. Vous pouvez obtenir cela en utilisant la même configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour le réplica principal et tous les réplicas secondaires, ou en utilisant les mêmes paramètres de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] par défaut sur tous les nœuds qui participent aux groupes de disponibilité. Nous recommandons de configurer la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur la base de données, car en configurant la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de la base de données, vous pouvez isoler les paramètres sur la base de données. De plus, les paramètres par défaut modifiés sont appliqués à toutes les autres bases de données sur l'instance.  
  
-   Spécifiez le réplica de sauvegarde. Le paramètre du réplica de sauvegarde par défaut est utilisé par la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour planifier les sauvegardes. Pour déterminer si le réplica actuel est le réplica de sauvegarde par défaut, utilisez le [sys.fn_hadr_backup_is_preferred_replica &#40;Transact-SQL&#41; ](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) (fonction).  
  
-   Si le réplica secondaire est configuré comme réplica par défaut, il doit avoir au moins un accès à la connexion en lecture seule. Les groupes de disponibilité qui n'ont pas d'accès à la connexion sur les bases de données secondaires ne sont pas pris en charge.  Pour plus d’informations, consultez [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
-   Si vous configurez la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] après avoir configuré le groupe de disponibilité, la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] tentera de copier toutes les sauvegardes existantes sur le conteneur de stockage.  Si la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] n'arrive pas à trouver ou à accéder aux sauvegardes existantes, elle planifiera une sauvegarde de bases de données complète. Cela vise précisément à optimiser les opérations de sauvegarde pour les bases de données d'un groupe de disponibilité.  
  
-   Vous pouvez envisager de désactiver les paramètres au niveau de l'instance si vous créez une nouvelle base de données de disponibilité, et que vous n'avez pas l'intention d'appliquer les paramètres au niveau d'instance à la base de données.  
  
-   Lorsque vous utilisez le chiffrement, utilisez le même certificat sur tous les réplicas. Cela permet des opérations de sauvegarde continues et ininterrompues en cas de basculement ou de restauration sur un réplica différent.  
  
#### <a name="enable-and-configure-includesssmartbackupincludesss-smartbackup-mdmd-for-an-availability-database"></a>Activer et configurer la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données de disponibilité  
 Ce didacticiel décrit les étapes d'activation et de configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données (AGTestDB) sur les ordinateurs Node1 et Node2, puis les étapes d'activation de la surveillance de l'état d'intégrité de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
1.  **Créer un compte de stockage Windows Azure :** les sauvegardes sont stockées dans le service de stockage d’objets Blob Windows Azure. Si vous n'avez pas de compte de stockage Windows Azure, vous devez d'abord en créer un. Pour plus d’informations, consultez [création d’un compte de stockage Windows Azure](http://www.windowsazure.com/manage/services/storage/how-to-create-a-storage-account/). Notez le nom du compte de stockage, les clés d'accès et l'URL du compte de stockage. Le nom du compte de stockage et les informations de clé d'accès sont utilisés pour créer un objet contenant les informations d'identification SQL. La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] se sert des informations d'identification SQL pour authentifier le compte de stockage pendant les opérations de sauvegarde.  
  
2.  **Créer des informations d’identification SQL :** créer les informations d’identification SQL à l’aide le nom du compte de stockage en tant que l’identité et la clé d’accès de stockage en tant que le mot de passe.  
  
3.  **Vérifiez que le service SQL Server Agent est démarré et exécuté** . Démarrez SQL Server Agent s'il n'est pas exécuté actuellement. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] nécessite l'exécution de SQL Server Agent sur l'instance pour effectuer les opérations de sauvegarde.  Vous pouvez configurer l'exécution automatique de l'Agent SQL, pour vous assurer que les opérations de sauvegarde se déroulent régulièrement.  
  
4.  **Déterminer la période de rétention :** déterminer la période de rétention souhaitée pour les fichiers de sauvegarde. La période de rétention est spécifiée en jours, sur une plage de 1 à 30. Elle détermine le délai de récupérabilité de la base de données.  
  
5.  **Créer une certificat ou une clé asymétrique à utiliser pour le chiffrement lors de la sauvegarde jusqu'à :** créer le certificat sur le premier nœud Node1, puis l’exporter dans un fichier en utilisant [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)... Sur le nœud 2, créez un certificat en utilisant le fichier exporté du nœud 1. Pour plus d’informations sur la création d’un certificat à partir d’un fichier, consultez l’exemple de [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).  
  
6.  **Activer et configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour AGTestDB sur Node1 :** démarrez SQL Server Management Studio et connectez-vous à l’instance sur Node1, où est installée la base de données de disponibilité. Dans la fenêtre de requête, exécutez l'instruction suivante après avoir modifié les valeurs du nom de la base de données, de l'URL de stockage, des informations d'identification SQL et de la période de rétention selon vos besoins.  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     Pour plus d’informations sur la création d’un certificat pour le chiffrement, consultez la **créer un certificat de sauvegarde** l’étape [créer une sauvegarde chiffrée](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
7.  **Activer et configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour AGTestDB sur Node2 :** démarrez SQL Server Management Studio et connectez-vous à l’instance sur Node2, où est installée la base de données de disponibilité. Dans la fenêtre de requête, exécutez l'instruction suivante après avoir modifié les valeurs du nom de la base de données, de l'URL de stockage, des informations d'identification SQL et de la période de rétention selon vos besoins.  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est maintenant activée sur la base de données spécifiée. Un délai de 15 minutes au maximum peut être nécessaire pour le démarrage des opérations de sauvegarde sur la base de données. La sauvegarde aura lieu sur le réplica de sauvegarde par défaut.  
  
8.  **Configuration par défaut des événements étendus révision :** passez en revue la configuration des événements étendus en exécutant l’instruction transact-SQL suivante sur le réplica qui [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] utilise pour planifier les sauvegardes. Il s'agit généralement des paramètres du réplica de sauvegarde par défaut pour le groupe de disponibilité auquel appartient la base de données.  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     Les événements du canal d'administration, opérationnel et analytique doivent être activés par défaut et ne doivent pas pouvoir être désactivés. Cela est en principe suffisant pour surveiller les événements qui nécessitent une intervention manuelle.  Vous pouvez activer les événements de débogage, mais ces canaux comprennent des événements d'information et de débogage que la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] utilise pour détecter et résoudre les problèmes. Pour plus d’informations, consultez [Moniteur SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
9. **Activez et configurez les notifications d’état d’intégrité :** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] fournit une procédure stockée qui crée un travail de l’agent pour envoyer des notifications par courrier électronique des erreurs ou avertissements qui peuvent nécessiter une attention particulière.  Pour recevoir ces notifications, vous devez activer l'exécution de la procédure stockée qui crée un travail SQL Server Agent. Les étapes suivantes décrivent la procédure d'activation et de configuration des notifications par courrier électronique :  
  
    1.  Configurez la messagerie de base de données si elle n'est pas déjà activée sur l'instance. Pour plus d'informations, consultez [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
    2.  Configurez la notification SQL Server Agent afin qu'elle utilise la messagerie de base de données. Pour plus d'informations, consultez [Configure SQL Server Agent Mail to Use Database Mail](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Activez les notifications par courrier électronique afin de recevoir les erreurs de sauvegarde et les avertissements :** dans la fenêtre de requête, exécutez les instructions Transact-SQL suivantes :  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email>'  
  
        ```  
  
         Pour plus d’informations et un exemple de script complet, consultez [Moniteur SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
10. **Afficher les fichiers de sauvegarde dans le compte de stockage Windows Azure :** se connecter au compte de stockage à partir de SQL Server Management Studio ou le portail de gestion Azure. Vous verrez un conteneur pour l'instance de SQL Server qui héberge la base de données que vous avez configurée pour utiliser la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Vous pourrez voir aussi une base de données et une sauvegarde de journal 15 minutes après l'activation de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour la base de données.  
  
11. **Surveillez l’état d’intégrité :**  vous pouvez le surveiller au moyen des notifications par courrier électronique configurées précédemment, ou en surveillant activement les événements enregistrés. Voici quelques exemples d'instructions Transact SQL utilisées pour afficher les événements :  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event varchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 Les étapes de cette section sont propres à la configuration initiale de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur la base de données. Vous pouvez modifier les configurations existantes à l’aide de la même procédure stockée système **smart_admin.sp_set_db_backup** et indiquer de nouvelles valeurs. Pour plus d’informations, consultez [SQL Server Managed Backup dans Windows Azure - paramètres de rétention et stockage](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
### <a name="considerations-when-removing-a-database-from-alwayson-availability-group-configuration"></a>Éléments à prendre en considération lors de la suppression d'une base de données de la configuration d'un groupe de disponibilité AlwaysOn  
 Si une base de données est supprimée de la configuration du groupe de disponibilité AlwaysOn et est désormais une base de données autonome, nous vous recommandons d’effectuer la sauvegarde à l’aide [smart_admin.sp_backup_on_demand &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql). Lorsque vous créez une sauvegarde de base de données de cette façon, une nouvelle chaîne de sauvegarde et le fichier sont placés dans le conteneur associé à l'instance au lieu du conteneur de disponibilité où les sauvegardes ont été enregistrées lorsque la base de données faisait partie d'un groupe de disponibilité.  
  
> [!WARNING]  
>  Dans ce scénario, la récupérabilité de la base de données à partir de sauvegardes antérieures à la modification de l'état du groupe de disponibilité n'est pas garantie.  
  
  
