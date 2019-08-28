---
title: Activer la sauvegarde managée SQL Server sur Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 281f1144fc9698fcb39d974167d02ce36602b4fd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089820"
---
# <a name="enable-sql-server-managed-backup-to-microsoft-azure"></a>Activer la sauvegarde managée SQL Server sur Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique décrit comment activer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] avec les paramètres par défaut au niveau base de données et instance. Elle décrit également comment activer les notifications par courrier électronique et surveiller l'activité de sauvegarde.  
  
 Ce didacticiel utilise Azure PowerShell. Avant de commencer ce didacticiel, [téléchargez et installez Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).  
  
> [!IMPORTANT]  
>  Si vous souhaitez également activer des options avancées ou utiliser une planification personnalisée, configurez ces paramètres avant d’activer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Pour plus d'informations, consultez [Configure Advanced Options for SQL Server Managed Backup to Microsoft Azure](../../relational-databases/backup-restore/configure-advanced-options-for-sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="enable-and-configure-includess_smartbackupincludesss-smartbackup-mdmd-with-default-settings"></a>Activer et configurer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] avec les paramètres par défaut  
  
#### <a name="create-the-azure-blob-container"></a>Création du conteneur Azure Blob  
  
1.  **Inscrivez-vous à Azure :** Si vous avez déjà un abonnement Azure, passez à l’étape suivante. Sinon, vous pouvez commencer avec une [version d’évaluation gratuite](https://azure.microsoft.com/pricing/free-trial/) ou explorer les [options d’achat](https://azure.microsoft.com/pricing/purchase-options/).  
  
2.  **Créez un compte de stockage Azure :** Si vous avez déjà un compte de stockage, passez à l’étape suivante. Sinon, vous pouvez utiliser le [Portail de gestion Azure](https://manage.windowsazure.com/) ou Azure PowerShell pour créer le compte de stockage. La commande `New-AzureStorageAccount` suivante crée un compte de stockage nommé `managedbackupstorage` dans la région USA Est.  
  
    ```powershell  
    New-AzureStorageAccount -StorageAccountName "managedbackupstorage" -Location "EAST US"  
    ```  
  
     Pour plus d'informations sur les comptes de stockage, consultez [À propos des comptes de stockage Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).  
  
3.  **Créez un conteneur d’objets blob pour les fichiers de sauvegarde :** Vous pouvez créer un conteneur d’objets blob dans le portail de gestion Azure ou avec Azure PowerShell. La commande `New-AzureStorageContainer` suivante crée un conteneur d’objets blob nommé `backupcontainer` dans le compte de stockage `managedbackupstorage` .  
  
    ```powershell  
    $context = New-AzureStorageContext -StorageAccountName managedbackupstorage -StorageAccountKey (Get-AzureStorageKey -StorageAccountName managedbackupstorage).Primary  
    New-AzureStorageContainer -Name backupcontainer -Context $context  
    ```  
  
4.  **Générez une signature d’accès partagé (SAP) :** Pour accéder au conteneur, vous devez créer une SAP. Cela peut être effectué dans certains outils, par code et dans Azure PowerShell. La commande `New-AzureStorageContainerSASToken` suivante crée le jeton SAP pour le conteneur d’objets blob `backupcontainer` qui expire dans un an.  
  
  ```powershell  
  $context = New-AzureStorageContext -StorageAccountName managedbackupstorage -StorageAccountKey (Get-AzureStorageKey -StorageAccountName managedbackupstorage).Primary   
  New-AzureStorageContainerSASToken -Name backupcontainer -Permission rwdl -ExpiryTime (Get-Date).AddYears(1) -FullUri -Context $context  
  ```  

Pour Azure, utilisez la commande suivante :
  ```powershell
  Connect-AzAccount
  Set-AzContext -SubscriptionId "YOURSUBSCRIPTIONID"
  $StorageAccountKey = (Get-AzStorageAccountKey -ResourceGroupName YOURRESOURCEGROUPFORTHESTORAGE -Name managedbackupstorage)[0].Value
  $context = New-AzureStorageContext -StorageAccountName managedbackupstorage -StorageAccountKey $StorageAccountKey 
  New-AzureStorageContainerSASToken -Name backupcontainer -Permission rwdl -ExpiryTime (Get-Date).AddYears(1) -FullUri -Context $context
  ```  
  
La sortie de cette commande contient l'URL du conteneur et le jeton SAP. Par exemple :  
  
  `https://managedbackupstorage.blob.core.windows.net/backupcontainer?sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl`
  
Dans l'exemple précédent, séparez l'URL du conteneur du jeton SAS avec le point d'interrogation (n'incluez pas le point d'interrogation). Par exemple, la sortie précédente produirait les deux valeurs suivantes.  
  
|||  
|-|-|  
|**URL du conteneur :**|https://managedbackupstorage.blob.core.windows.net/backupcontainer|  
|**Jeton SAS :**|sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl|  
|||
  
Enregistrez l’URL du conteneur et le SAS pour les utiliser lors de la création d’informations d’identification SQL. Pour plus d’informations sur SAP, consultez [Signatures d’accès partagé, partie 1 : présentation du modèle SAP](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/).  
  
#### <a name="enable-includess_smartbackupincludesss-smartbackup-mdmd"></a>Activer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
1.  **Créez des informations d’identification SQL pour l’URL SAP :** Utilisez le jeton SAP pour créer des informations d’identification SQL pour l’URL du conteneur d’objets blob. Dans SQL Server Management Studio, utilisez la requête Transact-SQL suivante pour créer les informations d'identification pour l'URL de votre conteneur d'objets blob sur la base de l'exemple suivant :  
  
    ```sql  
    CREATE CREDENTIAL [https://managedbackupstorage.blob.core.windows.net/backupcontainer]   
    WITH IDENTITY = 'Shared Access Signature',  
    SECRET = 'sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl'  
    ```  
  
2.  **Vérifiez que le service SQL Server Agent est démarré et exécuté :** Démarrez SQL Server Agent s’il n’est pas exécuté actuellement.  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] nécessite l'exécution de SQL Server Agent sur l'instance pour effectuer les opérations de sauvegarde.  Vous pouvez configurer l'exécution automatique de SQL Server Agent, pour vous assurer que les opérations de sauvegarde se déroulent régulièrement.  
  
3.  **Déterminez la période de rétention :** Déterminez la période de conservation des fichiers de sauvegarde. La période de rétention est spécifiée en jours, sur une plage de 1 à 30.  
  
4.  **Activez et configurez la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Démarrez SQL Server Management Studio et connectez-vous à l’instance SQL Server cible. Dans la fenêtre de requête, exécutez l'instruction suivante après avoir modifié les valeurs du nom de la base de données, de l’URL du conteneur et de la période de rétention selon vos besoins.  
  
    > [!IMPORTANT]  
    >  Pour activer la gestion de sauvegarde au niveau de l’instance, spécifiez `NULL` pour le paramètre `database_name` .  
  
    ```sql  
    Use msdb;  
    GO  
    EXEC msdb.managed_backup.sp_backup_config_basic   
     @enable_backup = 1,   
     @database_name = 'yourdatabasename',  
     @container_url = 'https://managedbackupstorage.blob.core.windows.net/backupcontainer',   
     @retention_days = 30  
    GO  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est maintenant activée sur la base de données spécifiée. Un délai de 15 minutes au maximum peut être nécessaire pour le démarrage des opérations de sauvegarde sur la base de données.  
  
5.  **Passez en revue la configuration par défaut des événements étendus :** Vérifiez les paramètres des événements étendus en exécutant l’instruction Transact-SQL suivante.  
  
    ```  
    SELECT * FROM msdb.managed_backup.fn_get_current_xevent_settings()  
    ```  
  
     Les événements du canal d'administration, opérationnel et analytique doivent être activés par défaut et ne doivent pas pouvoir être désactivés. Cela est en principe suffisant pour surveiller les événements qui nécessitent une intervention manuelle.  Vous pouvez activer les événements de débogage, mais les canaux de débogage comprennent des événements d'information et de débogage que la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] utilise pour détecter et résoudre les problèmes.  
  
6.  **Activez et configurez les notifications de l’état d’intégrité :** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] fournit une procédure stockée qui crée un travail d’agent pour envoyer des notifications par courrier électronique des erreurs ou des avertissements susceptibles de nécessiter une intervention. Les étapes suivantes décrivent la procédure d'activation et de configuration des notifications par courrier électronique :  
  
    1.  Configurez la messagerie de base de données si elle n'est pas déjà activée sur l'instance. Pour plus d'informations, consultez [Configure Database Mail](../../relational-databases/database-mail/configure-database-mail.md).  
  
    2.  Configurez la notification SQL Server Agent afin qu'elle utilise la messagerie de base de données. Pour plus d’informations, consultez [Configurer la messagerie de SQL Server Agent en vue de l’utilisation de la messagerie de base de données](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Activez les notifications par e-mail afin de recevoir les erreurs de sauvegarde et les avertissements :** Dans la fenêtre de requête, exécutez les instructions Transact-SQL suivantes :  
  
        ```  
        EXEC msdb.managed_backup.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
7.  **Affichez les fichiers de sauvegarde dans le compte de stockage Microsoft Azure :** Connectez-vous au compte de stockage à partir de SQL Server Management Studio ou du portail de gestion Azure. Vous verrez les fichiers de sauvegarde dans le conteneur que vous avez spécifié. Notez que vous pourrez voir aussi une base de données et une sauvegarde de journal 5 minutes après l’activation de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour la base de données.  
  
8.  **Supervisez l’état d’intégrité :**  Vous pouvez le superviser au moyen des notifications par e-mail configurées précédemment, ou en supervisant activement les événements enregistrés. Voici quelques exemples d'instructions Transact SQL utilisées pour afficher les événements :  
  
    ```sql  
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
  
    EXEC managed_backup.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```sql  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```sql  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC managed_backup.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
    ```
  
 Les étapes de cette section sont propres à la configuration initiale de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sur la base de données. Vous pouvez modifier les configurations existantes à l'aide des mêmes procédures stockées système et indiquer de nouvelles valeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde managée SQL Server sur Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  