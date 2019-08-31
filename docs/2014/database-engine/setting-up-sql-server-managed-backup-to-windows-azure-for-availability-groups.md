---
title: Configuration de la SQL Server la gestion de sauvegarde sur Azure pour les groupes de disponibilité | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 0c4553cd-d8e4-4691-963a-4e414cc0f1ba
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aa2cbce81827c9085f87112b366d532077915f58
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176098"
---
# <a name="setting-up-sql-server-managed-backup-to-azure-for-availability-groups"></a>Configuration de la SQL Server la gestion de sauvegarde sur Azure pour les groupes de disponibilité
  Cette rubrique est un didacticiel sur la configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour les bases de données participant à des groupes de disponibilité AlwaysOn.  
  
## <a name="availability-group-configurations"></a>Configurations de groupe de disponibilité  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]est pris en charge pour les bases de données de groupe de disponibilité, que les réplicas soient configurés localement ou entièrement sur Azure, ou qu’il s’agisse d’une implémentation hybride entre un ordinateur local et un ou plusieurs ordinateurs virtuels Azure. Cependant, tenez compte des éléments suivants pour une ou plusieurs implémentations :  
  
-   Fréquence de sauvegarde du journal : La fréquence de la sauvegarde du journal correspond à la croissance du temps et du journal. Par exemple, la sauvegarde de fichier journal est effectuée une fois toutes les 2 heures sauf si l'espace de journal utilisé pendant la période de 2 heures est de 5 Mo ou plus. Ceci s'applique à toutes les implémentations, locales, dans le cloud, ou hybrides.  
  
-   Bande passante réseau: Cela s’applique aux implémentations où les réplicas se trouvent dans des emplacements physiques différents, comme dans un Cloud hybride, ou dans des régions Azure différentes dans une configuration Cloud uniquement. La bande passante réseau peut affecter la latence des serveurs secondaires, et si les serveurs secondaires sont configurés avec la réplication synchrone, cela peut entraîner une croissance du journal sur le serveur principal. Si les serveurs secondaires utilisent la réplication synchrone, il est possible qu'ils n'arrivent pas à garder le pas en raison du temps de réponse du réseau, ce qui peut entraîner une perte de données en cas de basculement vers le réplica secondaire.  
  
### <a name="configuring-includess_smartbackupincludesss-smartbackup-mdmd-for-availability-databases"></a>Configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour les bases de données de disponibilité  
 **Autorisations :**  
  
-   Requiert l’appartenance au rôle de base de données **db_backupoperator** , avec les autorisations `EXECUTE` **ALTER ANY CREDENTIAL** et les autorisations sur la procédure stockée **sp_delete_backuphistory**.  
  
-   Requiert des autorisations **Select** sur la fonction **smart_admin. fn_get_current_xevent_settings**.  
  
-   Requiert `EXECUTE` des autorisations sur la procédure stockée **smart_admin. sp_get_backup_diagnostics** . En outre, nécessite les autorisations `VIEW SERVER STATE`, car elle appelle en interne d'autres objets système qui nécessitent cette autorisation.  
  
-   Requiert `EXECUTE` des autorisations sur `smart_admin.sp_set_instance_backup` les `smart_admin.sp_backup_master_switch` procédures stockées et.  
  
 Les étapes de base de configuration d'un groupe de disponibilité AlwaysOn avec la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sont les suivantes. Un didacticiel pas à pas détaillé est décrit plus loin dans cette rubrique.  
  
1.  Une fois que vous avez créé le groupe de disponibilité, configurez le réplica de sauvegarde par défaut. Ce paramètre du groupe de disponibilité est également utilisé par la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour déterminer quel réplica utiliser pour la sauvegarde. Pour obtenir des instructions pas à pas sur la configuration de la préférence de sauvegarde, consultez [configurer la sauvegarde sur &#40;les&#41;réplicas de disponibilité SQL Server](availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  Si vous créez un groupe de disponibilité AlwaysOn, consultez [prise en main avec &#40;groupes de disponibilité AlwaysOn&#41;SQL Server](availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md).  
  
2.  Configurez l'accès à la connexion en lecture seule sur les réplicas secondaires. Pour obtenir des instructions pas à pas sur la configuration de l’accès en lecture seule, consultez [configurer l’accès en lecture &#40;seule&#41; sur un réplica de disponibilité SQL Server](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
3.  Spécifiez le réplica de sauvegarde. Le paramètre du réplica de sauvegarde par défaut est utilisé par la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour déterminer quelle base de données utiliser pour planifier les sauvegardes.  Pour déterminer si le réplica actuel est le réplica de sauvegarde par défaut, utilisez la fonction [Transact- &#40;SQL&#41; sys. fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) .  
  
4.  À chaque réplication [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] , exécutez la configuration de la base de données à l’aide de la procédure stockée **Smart-admin. sp_set_db_backup** .  
  
     comportement après un basculement: **[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] continue à fonctionner et à gérer les copies de sauvegarde et la capacité de récupération après un événement de basculement. Aucune action spécifique n'est requise après un basculement.  
  
#### <a name="considerations-and-requirements"></a>Conditions requises et éléments à prendre en compte :  
 La configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour des bases de données participant à un groupe de disponibilité AlwaysOn nécessite des conditions spécifiques. Voici la liste des éléments à prendre en considération et des conditions requises :  
  
-   Les paramètres de configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] doivent être identiques pour toutes les bases de données sur tous les nœuds de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui participent au même groupe de disponibilité. Vous pouvez obtenir cela en utilisant la même configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour le réplica principal et tous les réplicas secondaires, ou en utilisant les mêmes paramètres de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] par défaut sur tous les nœuds qui participent aux groupes de disponibilité. Nous recommandons de configurer la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur la base de données, car en configurant la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de la base de données, vous pouvez isoler les paramètres sur la base de données. De plus, les paramètres par défaut modifiés sont appliqués à toutes les autres bases de données sur l'instance.  
  
-   Spécifiez le réplica de sauvegarde. Le paramètre du réplica de sauvegarde par défaut est utilisé par la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour planifier les sauvegardes. Pour déterminer si le réplica actuel est le réplica de sauvegarde par défaut, utilisez la fonction [Transact- &#40;SQL&#41; sys. fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) .  
  
-   Si le réplica secondaire est configuré comme réplica par défaut, il doit avoir au moins un accès à la connexion en lecture seule. Les groupes de disponibilité qui n'ont pas d'accès à la connexion sur les bases de données secondaires ne sont pas pris en charge.  Pour plus d’informations, consultez [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
-   Si vous configurez la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] après avoir configuré le groupe de disponibilité, la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] tentera de copier toutes les sauvegardes existantes sur le conteneur de stockage.  Si la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] n'arrive pas à trouver ou à accéder aux sauvegardes existantes, elle planifiera une sauvegarde de bases de données complète. Cela vise précisément à optimiser les opérations de sauvegarde pour les bases de données d'un groupe de disponibilité.  
  
-   Vous pouvez envisager de désactiver les paramètres au niveau de l’instance si vous créez une nouvelle base de données de disponibilité et que vous n’envisagez pas d’appliquer les paramètres au niveau de l’instance à la base de données.  
  
-   Lorsque vous utilisez le chiffrement, utilisez le même certificat sur tous les réplicas. Cela permet des opérations de sauvegarde continues et ininterrompues en cas de basculement ou de restauration sur un réplica différent.  
  
#### <a name="enable-and-configure-includess_smartbackupincludesss-smartbackup-mdmd-for-an-availability-database"></a>Activer et configurer la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données de disponibilité  
 Ce didacticiel décrit les étapes d'activation et de configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données (AGTestDB) sur les ordinateurs Node1 et Node2, puis les étapes d'activation de la surveillance de l'état d'intégrité de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
1.  **Créez un compte de stockage Azure :** Les sauvegardes sont stockées dans le service de stockage d’objets BLOB Azure. Vous devez d’abord créer un compte de stockage Azure, si vous n’en avez pas déjà un. Pour plus d’informations, consultez [création d’un compte de stockage Azure](http://www.windowsazure.com/manage/services/storage/how-to-create-a-storage-account/). Notez le nom du compte de stockage, les clés d'accès et l'URL du compte de stockage. Le nom du compte de stockage et les informations de clé d'accès sont utilisés pour créer un objet contenant les informations d'identification SQL. La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] se sert des informations d'identification SQL pour authentifier le compte de stockage pendant les opérations de sauvegarde.  
  
2.  **Créer des informations d’identification SQL:** Créez des informations d’identification SQL en utilisant le nom du compte de stockage comme identité et la clé d’accès de stockage comme mot de passe.  
  
3.  **Vérifiez que le service SQL Server Agent est démarré et exécuté :** Démarrez SQL Server Agent s’il n’est pas exécuté actuellement. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] nécessite l'exécution de SQL Server Agent sur l'instance pour effectuer les opérations de sauvegarde.  Vous pouvez configurer l'exécution automatique de l'Agent SQL, pour vous assurer que les opérations de sauvegarde se déroulent régulièrement.  
  
4.  **Déterminez la période de rétention :** Déterminez la période de rétention souhaitée pour les fichiers de sauvegarde. La période de rétention est spécifiée en jours, sur une plage de 1 à 30. Elle détermine le délai de récupérabilité de la base de données.  
  
5.  **Créez un certificat ou une clé asymétrique à utiliser pour le chiffrement lors de la sauvegarde:** Créez le certificat sur le premier nœud Node1, puis exportez-le vers un fichier à l’aide du [certificat &#40;de sauvegarde Transact-&#41;SQL](/sql/t-sql/statements/backup-certificate-transact-sql).. Sur le nœud 2, créez un certificat en utilisant le fichier exporté du nœud 1. Pour plus d’informations sur la création d’un certificat à partir d’un fichier, consultez l’exemple dans [Create Certificate &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).  
  
6.  **Activer et configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour AGTestDB sur Node1:** Démarrez SQL Server Management Studio et connectez-vous à l’instance sur Node1 où la base de données de disponibilité est installée. Dans la fenêtre de requête, exécutez l'instruction suivante après avoir modifié les valeurs du nom de la base de données, de l'URL de stockage, des informations d'identification SQL et de la période de rétention selon vos besoins.  
  
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
  
     Pour plus d’informations sur la création d’un certificat pour le chiffrement, consultez l’étape **créer un certificat de sauvegarde** dans [créer une sauvegarde chiffrée](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
7.  **Activer et configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour AGTestDB sur Node2:** Démarrez SQL Server Management Studio et connectez-vous à l’instance sur Node2, où la base de données de disponibilité est installée. Dans la fenêtre de requête, exécutez l'instruction suivante après avoir modifié les valeurs du nom de la base de données, de l'URL de stockage, des informations d'identification SQL et de la période de rétention selon vos besoins.  
  
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
  
8.  **Passez en revue la configuration par défaut des événements étendus :**  Passez en revue la configuration des événements étendus en exécutant l’instruction Transact-SQL suivante [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur le réplica qui utilise pour planifier les sauvegardes à partir de. Il s'agit généralement des paramètres du réplica de sauvegarde par défaut pour le groupe de disponibilité auquel appartient la base de données.  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     Les événements du canal d'administration, opérationnel et analytique doivent être activés par défaut et ne doivent pas pouvoir être désactivés. Cela est en principe suffisant pour surveiller les événements qui nécessitent une intervention manuelle.  Vous pouvez activer les événements de débogage, mais ces canaux comprennent des événements d'information et de débogage que la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] utilise pour détecter et résoudre les problèmes. Pour plus d’informations, consultez [Monitor SQL Server Managed Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
9. **Activez et configurez les notifications de l’état d’intégrité :** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] fournit une procédure stockée qui crée un travail d’agent pour envoyer des notifications par courrier électronique des erreurs ou des avertissements susceptibles de nécessiter une intervention.  Pour recevoir ces notifications, vous devez activer l'exécution de la procédure stockée qui crée un travail SQL Server Agent. Les étapes suivantes décrivent la procédure d'activation et de configuration des notifications par courrier électronique :  
  
    1.  Configurez la messagerie de base de données si elle n'est pas déjà activée sur l'instance. Pour plus d'informations, consultez [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
    2.  Configurez la notification SQL Server Agent afin qu'elle utilise la messagerie de base de données. Pour plus d’informations, consultez [Configurer la messagerie de SQL Server Agent en vue de l’utilisation de la messagerie de base de données](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Activez les notifications par e-mail afin de recevoir les erreurs de sauvegarde et les avertissements :** Dans la fenêtre de requête, exécutez les instructions Transact-SQL suivantes :  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email>'  
  
        ```  
  
         Pour plus d’informations et pour obtenir un exemple de script complet, consultez [Monitor SQL Server Managed Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
10. **Affichez les fichiers de sauvegarde dans le compte de stockage Azure:** Connectez-vous au compte de stockage à partir de SQL Server Management Studio ou du portail de gestion Azure. Vous verrez un conteneur pour l'instance de SQL Server qui héberge la base de données que vous avez configurée pour utiliser la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Vous pourrez voir aussi une base de données et une sauvegarde de journal 15 minutes après l'activation de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour la base de données.  
  
11. **Supervisez l’état d’intégrité :**  Vous pouvez le superviser au moyen des notifications par e-mail configurées précédemment, ou en supervisant activement les événements enregistrés. Voici quelques exemples d'instructions Transact SQL utilisées pour afficher les événements :  
  
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
  
 Les étapes de cette section sont propres à la configuration initiale de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur la base de données. Vous pouvez modifier les configurations existantes à l’aide de la même procédure stockée système **smart_admin. sp_set_db_backup** et fournir les nouvelles valeurs. Pour plus d’informations, consultez [SQL Server gestion de la sauvegarde vers Azure-paramètres](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)de rétention et de stockage.  
  
### <a name="considerations-when-removing-a-database-from-alwayson-availability-group-configuration"></a>Éléments à prendre en considération lors de la suppression d'une base de données de la configuration d'un groupe de disponibilité AlwaysOn  
 Si une base de données est supprimée de la configuration du groupe de disponibilité AlwaysOn et est désormais une base de données autonome, nous vous recommandons de procéder à une sauvegarde à l’aide de [smart_admin. sp_backup_on_demand &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql). Lorsque vous créez une sauvegarde de base de données de cette façon, une nouvelle chaîne de sauvegarde et le fichier sont placés dans le conteneur associé à l'instance au lieu du conteneur de disponibilité où les sauvegardes ont été enregistrées lorsque la base de données faisait partie d'un groupe de disponibilité.  
  
> [!WARNING]  
>  Dans ce scénario, la récupérabilité de la base de données à partir de sauvegardes antérieures à la modification de l'état du groupe de disponibilité n'est pas garantie.  
  
  
