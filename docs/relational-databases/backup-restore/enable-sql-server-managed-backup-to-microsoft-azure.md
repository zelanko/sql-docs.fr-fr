---
title: Utiliser la gestion de sauvegarde sur Azure
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.description: Enable SQL Server managed backup to Azure
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 07bb9cf8f0fc697e1d31a80e22a72cd5a0ea484a
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75257955"
---
# <a name="enable-sql-server-managed-backup-to-azure"></a>Activer la gestion de sauvegarde de SQL Server sur Azure

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique décrit comment activer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] avec les paramètres par défaut au niveau base de données et instance. Elle décrit également comment activer les notifications par courrier électronique et surveiller l'activité de sauvegarde.  
  
 Ce tutoriel utilise Azure PowerShell. Avant de commencer ce didacticiel, [téléchargez et installez Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).  
  
> [!IMPORTANT]  
>  Si vous souhaitez également activer des options avancées ou utiliser une planification personnalisée, configurez ces paramètres avant d’activer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Pour plus d’informations, consultez [Configurer les options avancées pour la gestion de sauvegarde de SQL Server sur Microsoft Azure](../../relational-databases/backup-restore/configure-advanced-options-for-sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="create-the-azure-blob-container"></a>Création du conteneur Azure Blob

Le processus requiert un compte Azure. Si vous avez déjà un compte, passez à l’étape suivante. Sinon, vous pouvez commencer avec une [version d’évaluation gratuite](https://azure.microsoft.com/pricing/free-trial/) ou explorer les [options d’achat](https://azure.microsoft.com/pricing/purchase-options/).

Pour plus d'informations sur les comptes de stockage, consultez [À propos des comptes de stockage Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/). 

#### <a name="azure-clitabazure-cli"></a>[Azure CLI](#tab/azure-cli)

1. Connectez-vous à votre compte Azure.

    ```azurecli-interactive
    az login
    ```
  
1. Créez un compte de stockage Azure. Si vous avez déjà un compte de stockage, passez à l’étape suivante. La commande suivante crée un compte de stockage nommé `<backupStorage>` dans la région USA Est.  
  
    ```azurecli-interactive
    az storage account create -n <backupStorage> -l "eastus" --resource-group <resourceGroup>
    ```  
    
1. Créez un conteneur d’objets blob nommé `<backupContainer>` pour les fichiers de sauvegarde.
  
    ```azurecli-interactive
    $keys = az storage account keys list --account-name <backupStorage> --resource-group <resourceGroup> | ConvertFrom-Json
    az storage container create --name <backupContainer> --account-name <backupStorage> --account-key $keys[0].value 
    ```  
  
1. Générez une signature d’accès partagé (SAP) pour accéder au conteneur. La commande suivante crée un jeton SAP pour le conteneur d’objets blob `<backupContainer>` qui expire dans un an.  
  
    ```azurecli-interactive 
    az storage container generate-sas --name <backupContainer> --account-name <backupStorage> --account-key $keys[0].value
    ```

#### <a name="powershelltabazure-powershell"></a>[PowerShell](#tab/azure-powershell)

1. La commande suivante permet de se connecter à votre compte Azure.

    ```azurepowershell-interactive
    Connect-AzAccount
    Set-AzContext -SubscriptionId "<subscriptionId>"
    ```
  
1. Créez un compte de stockage Azure. Si vous avez déjà un compte de stockage, passez à l’étape suivante. La commande suivante crée un compte de stockage nommé `<backupStorage>` dans la région USA Est.  
  
    ```azurepowershell-interactive
    New-AzStorageAccount -StorageAccountName <backupStorage> -Location "EAST US" -ResourceGroupName <resourceGroup> -SkuName Standard_GRS
    ```   
  
1. Créez un conteneur d’objets blob nommé `<backupContainer>` pour les fichiers de sauvegarde.  
  
    ```azurepowershell-interactive
    $context = New-AzStorageContext -StorageAccountName <backupStorage> -StorageAccountKey (Get-AzStorageAccountKey -Name <backupStorage> -ResourceGroupName <resourceGroup>).Value[0]  
    New-AzStorageContainer -Name <backupContainer> -Context $context  
    ```  
  
1. Générez une signature d’accès partagé (SAP) pour accéder au conteneur. La commande suivante crée un jeton SAP pour le conteneur d’objets blob `<backupContainer>` qui expire dans un an.
  
    ```azurepowershell-interactive 
    New-AzStorageContainerSASToken -Name <backupContainer> -Permission rwdl -ExpiryTime (Get-Date).AddYears(1) -FullUri -Context $context 
    ```

* * *

> [!NOTE]
> Ces étapes peuvent également être effectuées à l’aide du [portail Azure](https://portal.azure.com/).

La sortie contient l’URL du conteneur et/ou le jeton SAP. Par exemple :  
  
  `https://managedbackupstorage.blob.core.windows.net/backupcontainer?sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl`
  
Si l’URL est incluse, séparez-la du jeton SAP au niveau du point d’interrogation (n’incluez pas le point d’interrogation). Par exemple, la sortie précédente produirait les deux valeurs suivantes.  
  
|||  
|-|-|  
|**URL du conteneur**|https://managedbackupstorage.blob.core.windows.net/backupcontainer|  
|**Jeton SAP**|sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl|  
|||
  
Enregistrez l’URL du conteneur et le SAS pour les utiliser lors de la création d’informations d’identification SQL. Pour plus d’informations sur les signatures d’accès partagé, consultez l’article [Signatures d’accès partagé, partie 1 : Présentation du modèle SAP](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/).  
  
## <a name="enable-managed-backup-to-azure"></a>Activer la gestion de sauvegarde sur Azure
  
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
    USE msdb;  
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
  
    ```sql
    SELECT * FROM msdb.managed_backup.fn_get_current_xevent_settings()  
    ```  
  
     Les événements du canal d'administration, opérationnel et analytique doivent être activés par défaut et ne doivent pas pouvoir être désactivés. Cela est en principe suffisant pour surveiller les événements qui nécessitent une intervention manuelle.  Vous pouvez activer les événements de débogage, mais les canaux de débogage comprennent des événements d'information et de débogage que la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] utilise pour détecter et résoudre les problèmes.  
  
6.  **Activez et configurez les notifications de l’état d’intégrité :** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] fournit une procédure stockée qui crée un travail d’agent pour envoyer des notifications par e-mail des erreurs ou des avertissements susceptibles de nécessiter une intervention. Les étapes suivantes décrivent la procédure d'activation et de configuration des notifications par courrier électronique :  
  
    1.  Configurez la messagerie de base de données si elle n'est pas déjà activée sur l'instance. Pour plus d'informations, consultez [Configure Database Mail](../../relational-databases/database-mail/configure-database-mail.md).  
  
    2.  Configurez la notification SQL Server Agent afin qu'elle utilise la messagerie de base de données. Pour plus d’informations, consultez [Configurer la messagerie de SQL Server Agent en vue de l’utilisation de la messagerie de base de données](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Activez les notifications par e-mail afin de recevoir les erreurs de sauvegarde et les avertissements :** Dans la fenêtre de requête, exécutez les instructions Transact-SQL suivantes :  
  
        ```sql
        EXEC msdb.managed_backup.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
        ```  
  
7.  **Affichez les fichiers de sauvegarde dans le compte de stockage Azure :** connectez-vous au compte de stockage à partir de SQL Server Management Studio ou du portail Azure. Vous verrez les fichiers de sauvegarde dans le conteneur que vous avez spécifié. Notez que vous pourrez voir aussi une base de données et une sauvegarde de journal 5 minutes après l’activation de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour la base de données.  
  
8.  **Supervisez l’état d’intégrité :**  Vous pouvez le superviser au moyen des notifications par e-mail configurées précédemment, ou en supervisant activement les événements enregistrés. Voici quelques exemples d'instructions Transact SQL utilisées pour afficher les événements :  
  
    ```sql  
    --  view all admin events  
    USE msdb;  
    GO  
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
    USE msdb;  
    GO  
    EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
    ```  
  
    ```sql  
    --  View all events in the current week  
    USE msdb;  
    GO  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC managed_backup.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
    ```
  
Les étapes de cette section sont propres à la configuration initiale de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sur la base de données. Vous pouvez modifier les configurations existantes à l'aide des mêmes procédures stockées système et indiquer de nouvelles valeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de sauvegarde de SQL Server sur Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
