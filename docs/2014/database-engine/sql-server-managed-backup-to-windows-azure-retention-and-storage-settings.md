---
title: SQL Server la gestion de sauvegarde dans Azure-paramètres de rétention et de stockage | Microsoft Docs
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: c4aa26ea-5465-40cc-8b83-f50603cb9db1
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c9724055c2b386a451a293a0576994ba0ae6742
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251302"
---
# <a name="sql-server-managed-backup-to-azure---retention-and-storage-settings"></a>Sauvegarde managée SQL Server sur Azure : Paramètres de conservation et de stockage
  Cette rubrique décrit les étapes de base requises pour configurer la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données, et pour configurer les paramètres par défaut de l'instance. Elle décrit également les étapes nécessaires pour interrompre et reprendre les services de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour l'instance.  
  
 Pour une procédure pas à pas complète de la configuration de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], consultez la page Configuration de la [gestion de sauvegarde SQL Server sur Azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) et [configuration de SQL Server sauvegarde managée sur Azure pour les groupes de disponibilité](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   N'activez pas la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur les bases de données qui utilisent actuellement des plans de maintenance ou la copie des journaux de transactions. Pour plus d’informations sur l’interopérabilité et la coexistence avec d’autres fonctionnalités de SQL Server, consultez [SQL Server Managed Backup to Azure : Interopérabilité et coexistence @ no__t-0  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   SQL Server Agent ne doit pas être en cours d'exécution.  
  
    > [!WARNING]  
    >  Si SQL Server Agent est arrêté pendant une certaine période, puis est redémarré, vous pouvez constater une activité de sauvegarde accrue selon la période qui s'est écoulée entre l'arrêt et le démarrage. De plus, un journal des travaux en souffrance peut être généré, contenant les sauvegardes qui attendent d'être exécutées. Pensez à configurer SQL Server Agent afin qu'il soit lancé automatiquement au démarrage.  
  
-   Un compte de stockage Azure et des informations d’identification SQL qui stockent les informations d’authentification dans le compte de stockage doivent être créés avant la configuration de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Pour plus d’informations, consultez la section [Présentation des composants clés et des concepts](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) de la rubrique **SQL Server sauvegarde vers une URL** et [Lesson 2 : Créez un SQL Server informations d’identification @ no__t-0.  
  
    > [!IMPORTANT]  
    >  La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] crée les conteneurs nécessaires pour stocker les sauvegardes. Le nom du conteneur est créé à l’aide du format « nom de l’ordinateur-nom de l’instance ». Pour les groupes de disponibilité AlwaysOn, le conteneur est nommé en utilisant le GUID du groupe de disponibilité.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Pour exécuter les procédures stockées qui activent [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], vous devez être soit un `System Administrator`, soit un membre du rôle de base de données **db_backupoperator** avec les autorisations **ALTER ANY CREDENTIAL** et `EXECUTE` sur **sp_delete_backuphistory**, et `smart_admin.sp_backup_master_switch` procédures stockées.  Les procédures stockées et les fonctions utilisées pour passer en revue les paramètres existants nécessitent généralement des autorisations `Execute` sur la procédure stockée et `Select` sur la fonction, respectivement.  
  

  
###  <a name="Considerations"></a>Considérations relatives à l’activation de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour les bases de données et les instances  
 La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] peut être activée pour chaque base de données distincte ou pour la totalité de l'instance. Les choix dépendent des exigences de récupérabilité des bases de données sur l’instance, de la configuration requise pour la gestion de plusieurs bases de données et instances et de l’utilisation stratégique du stockage Azure.  
  
#### <a name="enabling-includess_smartbackupincludesss-smartbackup-mdmd-at-the-database-level"></a>Activation de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de la base de données  
 Si une base de données a des exigences de sauvegarde spécifiques et une période de rétention (SLA relatif à la récupérabilité) qui sont différentes des autres bases de données sur l'instance, configurez la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de la base de données pour cette base de données. Les paramètres de niveau base de données remplacent les paramètres de configuration de niveau instance. Cependant, ces deux possibilités peuvent être utilisées ensemble sur la même instance. Voici une liste des avantages et des éléments à prendre en considération lorsque vous activez la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de la base de données.  
  
-   Plus granulaire : Paramètres de configuration distincts pour chaque base de données. Peut prendre en charge différentes périodes de rétention pour chaque base de données.  
  
-   Remplace les paramètres au niveau de l'instance pour la base de données.  
  
-   Peut servir à réduire les coûts de stockage en sélectionnant des bases de données individuelles pour la sauvegarde.  
  
-   Nécessite la gestion de chaque base de données  
  
#### <a name="enabling-includess_smartbackupincludesss-smartbackup-mdmd-at-the-instance-level-with-default-settings"></a>Activation de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de l'instance avec des paramètres par défaut  
 Utilisez ces paramètres si la plupart des bases de données dans l'instance ont les mêmes exigences de sauvegarde et les mêmes stratégies de rétention, ou si vous souhaitez que les nouvelles instances de bases de données soient automatiquement sauvegardées à la création. Les bases de données qui font exception à la stratégie peuvent être configurées individuellement. Voici une liste des avantages et des éléments à prendre en considération lorsque vous activez la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de l'instance.  
  
-   Automatisation au niveau de l’instance : Les paramètres communs sont appliqués automatiquement aux nouvelles bases de données ajoutées par la suite.  
  
-   Les nouvelles bases de données sont automatiquement sauvegardées après leur création dans les instances  
  
-   Peut s'appliquer aux bases de données qui ont les mêmes périodes de rétention.  
  
-   Vous pouvez toujours configurer les bases de données qui nécessitent une période de rétention différente même si la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est activée au niveau de l'instance avec les paramètres par défaut. Vous pouvez également désactiver [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour les bases de données si vous n’envisagez pas d’utiliser le stockage Azure pour les sauvegardes.  
  
##  <a name="DatabaseConfigure"></a>Activer et configurer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données  
 La procédure stockée système `smart_admin.sp_set_db_backup` est utilisée pour activer la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données spécifique. Lorsque la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est activée pour la première fois sur la base de données, les informations suivantes doivent être spécifiées en plus de l'activation de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:  
  
-   Nom de la base de données.  
  
-   Période de rétention.  
  
-   Informations d’identification SQL utilisées pour l’authentification auprès du compte de stockage Azure.  
  
-   Spécifiez de ne pas chiffrer à l’aide de *\@encryption_algorithm* = **NO_ENCRYPTION** ou spécifiez un algorithme de chiffrement pris en charge. Pour plus d'informations sur le chiffrement, consultez [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une configuration au niveau de la base de données est prise en charge uniquement via Transact-SQL.  
  
 Une fois que la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est activée pour une base de données, cette information est conservée. Si vous modifiez la configuration, seuls le nom de la base de données et le paramètre que vous souhaitez modifier sont requis ; la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] conserve les valeurs existantes pour les autres paramètres en l'absence d'autre indication.  
  
> [!IMPORTANT]  
>  Avant de configurer la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur une base de données, il peut être utile de passer en revue la configuration existante, si elle existe. Les étapes pour revoir les paramètres de configuration d'une base de données sont abordées plus loin dans cette section.  
  
-   **Utilisation de Transact-SQL :**  
  
     Si vous activez [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour la première fois, les paramètres requis sont : *\@database_name*, *\@credential_name*, *\@encryption_algorithm*, *\@enable_backup* la *0storage_url* le paramètre est facultatif. Si vous ne fournissez pas de valeur pour le paramètre @storage_url, la valeur est dérivée à l’aide des informations de compte de stockage des informations d’identification SQL. Si vous spécifiez l'URL de stockage, vous ne devez spécifier que l'URL de la racine du compte de stockage, et vous devez faire correspondre les informations dans les informations d'identification SQL spécifiées.  
  
    1.  Connectez-vous au [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
    2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
    3.  Copiez et collez l’exemple suivant dans la fenêtre de requête, puis cliquez sur `Execute`. Cet exemple active [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour la base de données « TestDB ». La période de rétention est définie à 30 jours. Cet exemple utilise l'option de chiffrement spécifiant l'algorithme de chiffrement et les informations du chiffreur.  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@enable_backup=1  
                    ,@retention_days =30   
                    ,@credential_name ='MyCredential'  
                    ,@encryption_algorithm ='AES_256'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
    GO  
  
    ```  
  
    > [!IMPORTANT]  
    >  La période de rétention peut être définie sur n'importe quelle valeur de 1 à 30 jours.  
    >   
    >  Pour plus d'informations sur la création d'un certificat pour le chiffrement, consultez l'étape Créer un certificat de sauvegarde dans [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
     Pour plus d’informations sur cette procédure stockée, consultez [smart_admin. &#40;Set _DB_BACKUP Transact&#41; -SQL](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)  
  
     Pour passer en revue les paramètres de configuration d'une base de données, utilisez la requête suivante :  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('TestDB')  
    ```  
  
##  <a name="InstanceConfigure"></a>Activer et configurer les paramètres [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] par défaut pour l’instance  
 Vous pouvez activer et configurer les paramètres [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] par défaut au niveau de l’instance de deux manières :  À l’aide de la procédure stockée système `smart_admin.set_instance_backup` ou **SQL Server Management Studio**. Les deux méthodes sont expliquées ci-dessous :  
  
 **smart_admin. Set _instance_backup :** . En spécifiant la valeur **1** pour le paramètre *\@enable_backup* , vous pouvez activer la sauvegarde et définir les configurations par défaut. Une fois appliqués au niveau de l'instance, ces paramètres par défaut sont appliqués aux nouvelles bases de données ajoutées à cette instance.  Lorsque la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est activée pour la première, les informations suivantes doivent être spécifiées en plus de l'activation de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur l'instance :  
  
-   Période de rétention.  
  
-   Informations d’identification SQL utilisées pour l’authentification auprès du compte de stockage Azure.  
  
-   Option de chiffrement. Spécifiez de ne pas chiffrer à l’aide de *\@encryption_algorithm* = **NO_ENCRYPTION** ou spécifiez un algorithme de chiffrement pris en charge. Pour plus d'informations sur le chiffrement, consultez [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 Ces paramètres sont conservés après l'activation. Si vous modifiez la configuration, seuls le nom de la base de données et le paramètre à modifier sont requise. La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] conserve les valeurs existantes en l'absence d'autre indication.  
  
> [!IMPORTANT]  
>  Avant de configurer la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur une instance, il peut être utile de vérifier la configuration existante, si elle existe. Les étapes pour revoir les paramètres de configuration d'une base de données sont abordées plus loin dans cette section.  
  
 **SQL Server Management Studio :** Pour effectuer cette tâche dans SQL Server Management Studio, accédez à l’Explorateur d’objets, développez le nœud **gestion** , puis cliquez avec le bouton droit sur **sauvegarde managée**. Sélectionnez **Configurer**. La boîte de dialogue **Sauvegarde managée** s'ouvre. Utilisez cette boîte de dialogue pour spécifier la période de rétention, les informations d'identification SQL, l'URL de stockage et les paramètres de chiffrement. Pour obtenir de l’aide spécifique sur cette boîte de dialogue, consultez [configurer la sauvegarde &#40;managée SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md).  
  
#### <a name="using-transact-sql"></a>Utilisation de Transact-SQL  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l’exemple suivant dans la fenêtre de requête, puis cliquez sur `Execute`.  
  
```  
Use msdb;  
Go  
   EXEC smart_admin.sp_set_instance_backup  
                @retention_days=30   
                ,@credential_name='sqlbackuptoURL'  
                ,@encryption_algorithm ='AES_128'  
                ,@encryptor_type= 'Certificate'  
                ,@encryptor_name='MyBackupCert'  
                ,@enable_backup=1;  
GO  
  
```  
  
> [!IMPORTANT]  
>  La période de rétention peut être définie sur n'importe quelle valeur de 1 à 30 jours.  
>   
>  Pour plus d'informations sur la création d'un certificat pour le chiffrement, consultez l'étape Créer un certificat de sauvegarde dans [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
 Pour passer en revue les paramètres de configuration par défaut d'une instance, utilisez la requête suivante :  
  
```  
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
```  
  
#### <a name="using-powershell"></a>Utilisation de PowerShell  
  
1.  Démarrer une instance PowerShell  
  
2.  Exécutez le script suivant après l'avoir modifié en fonction de vos paramètres.  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    $encryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"  
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -BackupEnabled $True -BackupRetentionPeriodInDays 10 -EncryptionOption $encryptionOption  
    ```  
  
> [!IMPORTANT]  
>  Lorsque vous créez une nouvelle base de données après avoir configuré les paramètres par défaut, la configuration peut prendre jusqu'à 15 minutes. Cela s'applique également aux bases de données modifiées du modèle de récupération **Simple** au modèle **Full** ou **Bulk-Logged** .  
  
##  <a name="DatabaseDisable"></a> Désactiver la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données  
 Désactivez les paramètres de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] à l'aide de la procédure stockée système `sp_set_db_backup`. Le *\@enableparameter* est utilisé pour activer et désactiver les configurations [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données spécifique, où 1 active et 0 désactive les paramètres de configuration.  
  
#### <a name="to-disable-includess_smartbackupincludesss-smartbackup-mdmd-for-a-specific-database"></a>Pour désactiver la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données spécifique :  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l’exemple suivant dans la fenêtre de requête, puis cliquez sur `Execute`.  
  
```  
Use msdb;  
Go  
EXEC smart_admin.sp_set_db_backup   
                @database_name='TestDB'   
                ,@enable_backup=0;  
GO  
  
```  
  
##  <a name="DatabaseAllDisable"></a> Désactiver la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour toutes les bases de données sur l'instance  
 La procédure suivante désactive les paramètres de configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur toutes les bases de données où la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est actuellement activée sur l'instance.  Les paramètres de configuration tels que l'URL de stockage, la rétention, et les informations d'identification SQL, restent dans les métadonnées et peuvent être utilisés si la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est activée ultérieurement pour la base de données. Si vous souhaitez simplement interrompre le service de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] temporairement, vous pouvez utiliser le commutateur principal abordé dans les sections suivantes de cette rubrique.  
  
#### <a name="to-disable-includess_smartbackupincludesss-smartbackup-mdmdfor-all-the-databases"></a>Pour désactiver la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]pour toutes les bases de données :  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l’exemple suivant dans la fenêtre de requête, puis cliquez sur `Execute`. L'exemple suivant détermine si la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est configurée au niveau de l'instance et identifie toutes les bases de données activées pour la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur l'instance, puis exécute la procédure stockée système `sp_set_db_backup` pour désactiver la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
```  
-- Create a working table to store the database names  
Declare @DBNames TABLE  
  
       (  
             RowID int IDENTITY PRIMARY KEY  
             ,DBName varchar(500)  
  
       )  
-- Define the variables  
DECLARE @rowid int  
DECLARE @dbname varchar(500)  
DECLARE @SQL varchar(2000)  
-- Get the database names from the system function  
  
INSERT INTO @DBNames (DBName)  
  
SELECT db_name  
       FROM   
  
       smart_admin.fn_backup_db_config (NULL)  
       WHERE is_smart_backup_enabled = 1  
  
       --Select DBName from @DBNames  
  
       select @rowid = min(RowID)  
       FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin  
  
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC smart_admin.sp_set_db_backup    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END  
  
```  
  
 Pour passer en revue les paramètres de configuration de toutes les bases de données sur l'instance, utilisez la requête suivante :  
  
```  
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_db_config (NULL);  
GO  
  
```  
  
##  <a name="InstanceDisable"></a> Désactiver les paramètres de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] par défaut pour l'instance  
 Les paramètres par défaut au niveau de l'instance sont appliqués à toutes les nouvelles bases de données créées sur cette instance.  Si vous n'avez plus besoin des paramètres par défaut, vous pouvez désactiver cette configuration à l'aide de la procédure stockée système **smart_admin.sp_set_instance_backup** . La désactivation ne supprime pas les autres paramètres de configuration, comme l'URL de stockage, le paramètre de rétention ou le nom de l'objet contenant les informations d'identification SQL. Ces paramètres seront utilisés si la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est activée sur l'instance ultérieurement.  
  
#### <a name="to-disable-includess_smartbackupincludesss-smartbackup-mdmd-default-configuration-settings"></a>Pour désactiver les paramètres de configuration par défaut de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] :  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l’exemple suivant dans la fenêtre de requête, puis cliquez sur `Execute`.  
  
    ```  
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_instance_backup  
                    @enable_backup=0;  
    GO  
  
    ```  
  
#### <a name="using-powershell"></a>Utilisation de PowerShell  
  
1.  Démarrer une instance PowerShell  
  
2.  Exécutez le script suivant :  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Set-SqlSmartAdmin -BackupEnabled $False  
    ```  
  
##  <a name="InstancePause"></a> Interrompre la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de l'instance  
 Dans certains cas, vous pouvez souhaiter interrompre les services de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une courte période.  La procédure stockée système `smart_admin.sp_backup_master_switch` vous permet de désactiver le service de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] au niveau de l'instance.  La même procédure est utilisée pour reprendre la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Le paramètre @state est utilisé pour déterminer si la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] doit être désactivée ou activée.  
  
#### <a name="to-pause-includess_smartbackupincludesss-smartbackup-mdmd-services-using-transact-sql"></a>Pour interrompre les services de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] à l'aide de Transact-SQL :  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l’exemple suivant dans la fenêtre de requête, puis cliquez sur `Execute`  
  
```  
Use msdb;  
GO  
EXEC smart_admin.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### <a name="to-pause-includess_smartbackupincludesss-smartbackup-mdmd-using-powershell"></a>Pour interrompre la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] à l'aide de PowerShell  
  
1.  Démarrer une instance PowerShell  
  
2.  Exécutez le script suivant après l'avoir modifié en fonction de vos paramètres.  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $False  
    ```  
  
#### <a name="to-resume-includess_smartbackupincludesss-smartbackup-mdmd-using-transact-sql"></a>Pour reprendre la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] à l'aide de Transact-SQL  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l’exemple suivant dans la fenêtre de requête, puis cliquez sur `Execute`.  
  
```  
Use msdb;  
Go  
EXEC smart_admin. sp_backup_master_switch @new_state=1;  
GO  
  
```  
  
#### <a name="to-resume-includess_smartbackupincludesss-smartbackup-mdmd-using-powershell"></a>Pour reprendre la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] à l'aide de PowerShell  
  
1.  Démarrer une instance PowerShell  
  
2.  Exécutez le script suivant après l'avoir modifié en fonction de vos paramètres.  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $True  
    ```  
  
  
