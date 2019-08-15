---
title: Configuration de la SQL Server la sauvegarde managée sur Windows Azure | Microsoft Docs
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4b72fcf0a067838651d9c41205c3604750fecc6d
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028644"
---
# <a name="setting-up-sql-server-managed-backup-to-windows-azure"></a>Configuration de la sauvegarde managée SQL Server sur Windows Azure
  Cette rubrique contient deux didacticiels :  
  
 Configurer la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] au niveau de la base de données, activer les notifications par courrier électronique et surveiller l'activité de sauvegarde.  
  
 Configurer la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] au niveau de l'instance, activer les notifications par courrier électronique et surveiller l'activité de sauvegarde.  
  
 Pour obtenir un didacticiel sur la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configuration des groupes de disponibilité, consultez Configuration de la [SQL Server gestion de la sauvegarde sur Microsoft Azure pour les groupes de disponibilité](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
## <a name="setting-up-includess_smartbackupincludesss-smartbackup-mdmd"></a>Configuration de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
### <a name="enable-and-configure-includess_smartbackupincludesss-smartbackup-mdmd-for-a-database"></a>Activer et configurer la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour une base de données  
 Ce didacticiel décrit les étapes à suivre pour activer et configurer la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour une base de données (TestDB), puis pour activer la surveillance de l'état d'intégrité de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 **Autorisations :**  
  
-   Requiert l’appartenance au rôle de base de données **db_backupoperator** , avec les autorisations `EXECUTE` **ALTER ANY CREDENTIAL** et les autorisations sur la procédure stockée **sp_delete_backuphistory**.  
  
-   Requiert des autorisations **Select** sur la fonction **smart_admin. fn_get_current_xevent_settings**.  
  
-   Requiert `EXECUTE` des autorisations sur la procédure stockée **smart_admin. sp_get_backup_diagnostics** . En outre, nécessite les autorisations `VIEW SERVER STATE`, car elle appelle en interne d'autres objets système qui nécessitent cette autorisation.  
  
-   Requiert `EXECUTE` des autorisations sur `smart_admin.sp_set_instance_backup` les `smart_admin.sp_backup_master_switch` procédures stockées et.  


1.  **Créez un compte de stockage Microsoft Azure:** Les sauvegardes sont stockées dans le service de stockage Microsoft Azure. Vous devez d’abord créer un compte de stockage Microsoft Azure, si vous n’avez pas encore de compte.
    - SQL Server 2014 utilise des objets BLOB de pages, qui sont différents des objets BLOB de blocs et d’ajout. Par conséquent, vous devez créer un compte à usage général, et non un compte d’objet BLOB. Pour plus d’informations, consultez [à propos des comptes de stockage Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).
    - Notez le nom du compte de stockage et les clés d'accès. Le nom du compte de stockage et les informations de clé d'accès sont utilisés pour créer un objet contenant les informations d'identification SQL. Les informations d'identification SQL servent à authentifier le compte de stockage.  
 
2.  **Créer des informations d’identification SQL:** Créez des informations d’identification SQL en utilisant le nom du compte de stockage comme identité et la clé d’accès de stockage comme mot de passe.  
  
3.  **Vérifiez que le service SQL Server Agent est démarré et exécuté :**  Démarrez SQL Server Agent s’il n’est pas exécuté actuellement.  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] nécessite l'exécution de SQL Server Agent sur l'instance pour effectuer les opérations de sauvegarde.  Vous pouvez configurer l'exécution automatique de SQL Server Agent, pour vous assurer que les opérations de sauvegarde se déroulent régulièrement.  
  
4.  **Déterminez la période de rétention :** Déterminez la période de conservation des fichiers de sauvegarde. La période de rétention est spécifiée en jours, sur une plage de 1 à 30.  
  
5.  **Activez et configurez la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Démarrez SQL Server Management Studio et connectez-vous à l’instance où la base de données est installée. Dans la fenêtre de requête, exécutez l'instruction suivante après avoir modifié les valeurs du nom de la base de données, des informations d'identification SQL, de la période de rétention et des options de chiffrement selon vos besoins.  
  
     Pour plus d’informations sur la création d’un certificat pour le chiffrement, consultez l’étape **créer un certificat de sauvegarde** dans [créer une sauvegarde chiffrée](create-an-encrypted-backup.md).  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est maintenant activée sur la base de données spécifiée. Un délai de 15 minutes au maximum peut être nécessaire pour le démarrage des opérations de sauvegarde sur la base de données.  
  
6.  **Passez en revue la configuration par défaut des événements étendus :** Vérifiez les paramètres des événements étendus en exécutant l’instruction Transact-SQL suivante.  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     Les événements du canal d'administration, opérationnel et analytique doivent être activés par défaut et ne doivent pas pouvoir être désactivés. Cela est en principe suffisant pour surveiller les événements qui nécessitent une intervention manuelle.  Vous pouvez activer les événements de débogage, mais les canaux de débogage comprennent des événements d'information et de débogage que la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] utilise pour détecter et résoudre les problèmes. Pour plus d’informations, consultez [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
7.  **Activez et configurez les notifications de l’état d’intégrité :** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] fournit une procédure stockée qui crée un travail d’agent pour envoyer des notifications par courrier électronique des erreurs ou des avertissements susceptibles de nécessiter une intervention. Les étapes suivantes décrivent la procédure d'activation et de configuration des notifications par courrier électronique :  
  
    1.  Configurez la messagerie de base de données si elle n'est pas déjà activée sur l'instance. Pour plus d'informations, consultez [Configure Database Mail](../database-mail/configure-database-mail.md).  
  
    2.  Configurez la notification SQL Server Agent afin qu'elle utilise la messagerie de base de données. Pour plus d’informations, consultez [Configurer la messagerie de SQL Server Agent en vue de l’utilisation de la messagerie de base de données](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Activez les notifications par e-mail afin de recevoir les erreurs de sauvegarde et les avertissements :** Dans la fenêtre de requête, exécutez les instructions Transact-SQL suivantes :  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
         Pour plus d’informations et pour obtenir un exemple de script complet, consultez [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
8.  **Affichez les fichiers de sauvegarde dans le compte de stockage Microsoft Azure :** Connectez-vous au compte de stockage à partir de SQL Server Management Studio ou du portail de gestion Azure. Vous verrez un conteneur pour l'instance de SQL Server qui héberge la base de données que vous avez configurée pour utiliser la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Vous pourrez voir aussi une base de données et une sauvegarde de journal 15 minutes après l'activation de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour la base de données.  
  
9. **Supervisez l’état d’intégrité :**  Vous pouvez le superviser au moyen des notifications par e-mail configurées précédemment, ou en supervisant activement les événements enregistrés. Voici quelques exemples d'instructions Transact SQL utilisées pour afficher les événements :  
  
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
    event nvarchar (512),  
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
  
 Les étapes de cette section sont propres à la configuration initiale de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sur la base de données. Vous pouvez modifier les configurations existantes à l’aide de la même procédure stockée système **smart_admin. sp_set_db_backup** et fournir les nouvelles valeurs. Pour plus d’informations, consultez [SQL Server la sauvegarde managée vers Microsoft Azure paramètres](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)de rétention et de stockage.  
  
### <a name="enable-includess_smartbackupincludesss-smartbackup-mdmd-for-the-instance-with-default-settings"></a>Activer la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour l'instance avec des paramètres par défaut  
 Ce didacticiel décrit les étapes à suivre pour activer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] et configurer pour l’instance «MyInstance\\». Il inclut les étapes pour activer la surveillance de l'état d'intégrité de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 **Autorisations :**  
  
-   Requiert l’appartenance au rôle de base de données **db_backupoperator** , avec les autorisations `EXECUTE` **ALTER ANY CREDENTIAL** et les autorisations sur la procédure stockée **sp_delete_backuphistory**.  
  
-   Requiert des autorisations **Select** sur la fonction **smart_admin. fn_get_current_xevent_settings**.  
  
-   Requiert `EXECUTE` des autorisations sur la procédure stockée **smart_admin. sp_get_backup_diagnostics** . En outre, nécessite les autorisations `VIEW SERVER STATE`, car elle appelle en interne d'autres objets système qui nécessitent cette autorisation.  


1.  **Créez un compte de stockage Microsoft Azure:** Les sauvegardes sont stockées dans le service de stockage Microsoft Azure. Vous devez d’abord créer un compte de stockage Microsoft Azure, si vous n’avez pas encore de compte.
    - SQL Server 2014 utilise des objets BLOB de pages, qui sont différents des objets BLOB de blocs et d’ajout. Par conséquent, vous devez créer un compte à usage général, et non un compte d’objet BLOB. Pour plus d’informations, consultez [à propos des comptes de stockage Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).
    - Notez le nom du compte de stockage et les clés d'accès. Le nom du compte de stockage et les informations de clé d'accès sont utilisés pour créer un objet contenant les informations d'identification SQL. Les informations d'identification SQL servent à authentifier le compte de stockage.  
  
2.  **Créer des informations d’identification SQL:** Créez des informations d’identification SQL en utilisant le nom du compte de stockage comme identité et la clé d’accès de stockage comme mot de passe.  
  
3.  **Vérifiez que le service SQL Server Agent est démarré et exécuté :** Démarrez SQL Server Agent s’il n’est pas exécuté actuellement. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] nécessite l'exécution de SQL Server Agent sur l'instance pour effectuer les opérations de sauvegarde.  Vous pouvez configurer l'exécution automatique de SQL Server Agent, pour vous assurer que les opérations de sauvegarde se déroulent régulièrement.  
  
4.  **Déterminez la période de rétention :** Déterminez la période de conservation des fichiers de sauvegarde. La période de rétention est spécifiée en jours, sur une plage de 1 à 30. Après l'activation de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] au niveau de l'instance avec les paramètres par défaut, toutes les nouvelles bases de données créées héritent de ces paramètres. Seules les bases de données employant le mode de récupération complète ou le mode de récupération utilisant les journaux de transactions sont prises en charge et sont configurées automatiquement. Vous pouvez désactiver la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour une base de données spécifique à tout moment si vous ne souhaitez pas que la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] soit configurée. Vous pouvez également modifier la configuration d'une base de données spécifique en configurant la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] au niveau de la base de données.  
  
5.  **Activez et configurez la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Démarrez SQL Server Management Studio et connectez-vous à l’instance de SQL Server. Dans la fenêtre de requête, exécutez l'instruction suivante après avoir modifié les valeurs du nom de la base de données, des informations d'identification SQL, de la période de rétention et des options de chiffrement selon vos besoins.  
  
     Pour plus d’informations sur la création d’un certificat pour le chiffrement, consultez l’étape **créer un certificat de sauvegarde** dans [créer une sauvegarde chiffrée](create-an-encrypted-backup.md).  
  
    ```  
    Use msdb;  
    Go  
       EXEC smart_admin.sp_set_instance_backup  
                     @enable_backup=1  
                    ,@retention_days=30   
                    ,@credential_name='sqlbackuptoURL'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert';  
    GO  
  
    ```  
  
     La [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est maintenant activée sur l'instance.  
  
6.  Vérifiez les paramètres de configuration en exécutant l'instruction Transact-SQL suivante :  
  
    ```  
    Use msdb;  
    GO  
    SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
    ```  
  
7.  Créez une nouvelle base de données sur l'instance. Exécutez l'instruction Transact-SQL suivante pour afficher les paramètres de configuration de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour la base de données :  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('NewDB')  
    ```  
  
     Un délai de 15 minutes au maximum peut être nécessaire pour l'affichage des paramètres et le démarrage des opérations de sauvegarde sur la base de données.  
  
8.  **Activez et configurez les notifications de l’état d’intégrité :** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] fournit une procédure stockée qui crée un travail d’agent pour envoyer des notifications par courrier électronique des erreurs ou des avertissements susceptibles de nécessiter une intervention.  Pour recevoir ces notifications, vous devez activer l'exécution de la procédure stockée qui crée un travail SQL Server Agent. Les étapes suivantes décrivent la procédure d'activation et de configuration des notifications par courrier électronique :  
  
    1.  Configurez la messagerie de base de données si elle n'est pas déjà activée sur l'instance. Pour plus d'informations, consultez [Configure Database Mail](../database-mail/configure-database-mail.md).  
  
    2.  Configurez la notification SQL Server Agent afin qu'elle utilise la messagerie de base de données. Pour plus d’informations, consultez [Configurer la messagerie de SQL Server Agent en vue de l’utilisation de la messagerie de base de données](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Activez les notifications par e-mail afin de recevoir les erreurs de sauvegarde et les avertissements :** Dans la fenêtre de requête, exécutez les instructions Transact-SQL suivantes :  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email address>'  
  
        ```  
  
         Pour plus d’informations sur la façon de surveiller, et un exemple de script complet, consultez [monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
9. **Affichez les fichiers de sauvegarde dans le compte de stockage Microsoft Azure :** Connectez-vous au compte de stockage à partir de SQL Server Management Studio ou du portail de gestion Azure. Vous verrez un conteneur pour l'instance de SQL Server qui héberge la base de données que vous avez configurée pour utiliser la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Vous pourrez voir aussi une base de données et une sauvegarde de journal 15 minutes après la création de la base de données.  
  
10. **Supervisez l’état d’intégrité :**  Vous pouvez le superviser au moyen des notifications par e-mail configurées précédemment, ou en supervisant activement les événements enregistrés. Voici quelques exemples d'instructions Transact SQL utilisées pour afficher les événements :  
  
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
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    --  to enable debug events  
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
  
 Les paramètres par défaut de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] peuvent être remplacés pour une base de données spécifique en les configurant directement au niveau de cette base de données. Vous pouvez également interrompre et reprendre temporairement le service de [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Pour plus d’informations, consultez [SQL Server gestion de la sauvegarde vers Microsoft Azure paramètres](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md) de rétention et de stockage.  
  
  
