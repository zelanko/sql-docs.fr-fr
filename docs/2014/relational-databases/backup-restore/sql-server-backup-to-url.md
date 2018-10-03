---
title: Sauvegarde SQL Server vers une URL | Microsoft Docs
ms.custom: ''
ms.date: 01/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 11be89e9-ff2a-4a94-ab5d-27d8edf9167d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8f91a410e5c1c6e16a6fc3e1da26f89893ac261b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48065119"
---
# <a name="sql-server-backup-to-url"></a>Sauvegarde SQL Server vers une URL
  Cette rubrique présente les concepts, la configuration requise et les composants nécessaires pour utiliser le service de stockage d'objets blob Windows Azure comme destination de sauvegarde. Les fonctionnalités de sauvegarde et de restauration sont identiques ou similaires à l'utilisation de l'option DISK ou TAPE, à quelques différences près. Les différences, les exceptions notables et des exemples de code sont inclus dans cette rubrique.  
  
## <a name="requirements-components-and-concepts"></a>Configuration requise, composants et concepts  
 **Dans cette section :**  
  
-   [Sécurité](#security)  
  
-   [Présentation des principaux éléments et concepts](#intorkeyconcepts)  
  
-   [Service de stockage Windows Azure Blob](#Blob)  
  
-   [Composants SQL Server](#sqlserver)  
  
-   [Limitations](#limitations)  
  
-   [Prise en charge des instructions de sauvegarde/restauration](#Support)  
  
-   [Utilisation de la tâche de sauvegarde dans SQL Server Management Studio](sql-server-backup-to-url.md#BackupTaskSSMS)  
  
-   [Sauvegarde SQL Server vers une URL à l'aide de l'Assistant Plan de maintenance](sql-server-backup-to-url.md#MaintenanceWiz)  
  
-   [Restauration à partir du stockage Windows Azure à l'aide de SQL Server Management Studio](sql-server-backup-to-url.md#RestoreSSMS)  
  
###  <a name="security"></a> Sécurité  
 Vous trouverez ci-dessous les considérations de sécurité et la configuration requise pour la sauvegarde vers ou la restauration depuis les services de stockage d'objets blob Windows Azure.  
  
-   Lorsque vous créez un conteneur pour le service de stockage d'objets blob Windows Azure, nous vous recommandons de définir l'accès sur **Privé**. La définition d'un accès privé limite l'accès aux seuls utilisateurs ou comptes capables de fournir les informations nécessaires pour s'authentifier auprès du compte Windows Azure.  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert que le nom de compte Windows Azure et l'authentification par clé d'accès soient stockés dans les informations d'identification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces informations sont utilisées pour l'authentification auprès d'un compte Windows Azure lors des opérations de sauvegarde ou de restauration.  
  
-   Le compte d’utilisateur utilisé pour émettre les commandes BACKUP (sauvegarder) ou RESTORE (restaurer) doit figurer dans le rôle de base de données **db_backup operator** avec les autorisations **Modifier des informations d’identification** .  
  
###  <a name="intorkeyconcepts"></a> Présentation des principaux éléments et concepts  
 Les deux sections suivantes présentent le service de stockage Blob Windows Azure et le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composants utilisés lors de la sauvegarde ou de restauration à partir du service de stockage d’objets Blob Windows Azure. Il est important de comprendre les composants et leur interaction pour effectuer une sauvegarde ou une restauration vers ou depuis le service de stockage d'objets blob Windows Azure.  
  
 La création d'un compte Windows Azure est la première étape de ce processus. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise le **nom de compte de stockage Windows Azure** et son **clé d’accès** valeurs pour authentifier et écrire et lire les objets BLOB pour le service de stockage. Les informations d'identification de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stockent ces informations et sont utilisées lors des opérations de sauvegarde ou de restauration. Pour connaître la procédure détaillée de création d'un compte de stockage et la procédure de restauration de base, consultez le [Didacticiel sur l'utilisation du service de stockage Windows Azure pour la sauvegarde et la restauration de SQL Server](http://go.microsoft.com/fwlink/?LinkId=271615).  
  
 ![mappage de compte de stockage des informations d’identification sql](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "mappage du compte de stockage des informations d’identification sql")  
  
###  <a name="Blob"></a> Service de stockage Windows Azure Blob  
 **Compte de stockage :** le compte de stockage constitue le point de départ de tous les services de stockage. Pour accéder au service de stockage d'objets blob Windows Azure, commencez par créer un compte de stockage Windows Azure. Le **storage account name** et ses propriétés de **access key** sont requis pour s'authentifier auprès du service de stockage d'objets blob Windows Azure et de ses composants.  
  
 **Conteneur :** un conteneur regroupe un ensemble d'objets blob et peut stocker un nombre illimité d'objets blob. Pour écrire une sauvegarde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le service d'objets blob Windows Azure, vous devez avoir créé au moins le conteneur racine.  
  
 **Objet blob :** fichier de tout type et de toute taille. Il existe deux types d'objets blob qui peuvent être enregistrés dans le service de stockage d'objets blob Windows Azure : les objets blob de blocs et les objets blob de pages. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la sauvegarde utilise des objets BLOB de pages en tant que type d’objet Blob. Objets BLOB est adressables en utilisant le format d’URL suivant : https://\<compte de stockage >.blob.core.windows.net/\<conteneur > /\<blob >  
  
 ![Stockage Blob Azure](../../database-engine/media/backuptocloud-blobarchitecture.gif "Stockage Blob Azure")  
  
 Pour plus d'informations sur le service de stockage d'objets blob Windows Azure, consultez [Procédure d'utilisation du service de stockage d'objets blob Windows Azure](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).  
  
 Pour plus d'informations sur les objets blob de pages, consultez [Objets blob de blocs et objets blob de pages](http://msdn.microsoft.com/library/windowsazure/ee691964.aspx).  
  
###  <a name="sqlserver"></a> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components  
 **URL :** une URL spécifie un URI (Uniform Resource Identifier) vers un fichier de sauvegarde unique. L'URL est utilisée pour indiquer l'emplacement et le nom du fichier de sauvegarde de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Dans cette implémentation, la seule URL valide est celle qui pointe vers un objet blob de pages dans un compte de stockage Windows Azure. L'URL doit pointer vers un objet blob réel et pas un simple conteneur. Si l'objet blob n'existe pas, il est créé. Si un objet blob existant est spécifié, l'instruction BACKUP échoue, à moins que l'option « WITH FORMAT » ne soit spécifiée.  
  
> [!WARNING]  
>  Si vous choisissez de copier et télécharger un fichier de sauvegarde dans le service de stockage d'objets blob Windows Azure, utilisez un objet blob de pages comme option de stockage. Les restaurations à partir d'objets blob de blocs ne sont pas prises en charge. Une restauration à partir d'un type d'objet blob de blocs échoue avec une erreur.  
  
 Voici un exemple de valeur d’URL : http[s]://ACCOUNTNAME.Blob.Core.Windows.NET/\<conteneur > /\<nomfichier.bak >. HTTPS n'est pas obligatoire, mais est recommandé.  
  
 **Informations d'identification :** les informations d'identification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont des objets utilisés pour stocker les informations d'authentification requises pour la connexion à une ressource en dehors de SQL Server.  Ici, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processus de sauvegarde et restauration utilisent les informations d’identification pour s’authentifier sur le service de stockage d’objets Blob Windows Azure. Les informations d'identification contiennent le nom du compte de stockage et ses valeurs de **clé d'accès** . Une fois les informations d'identification créées, vous devez les spécifier dans l'option WITH CREDENTIAL lorsque vous publiez des instructions BACKUP/RESTORE. Pour plus d'informations sur l'affichage, la copie ou la régénération des **access keys**de compte de stockage, consultez [Afficher, copier et régénérer les clés d'accès d'un compte de stockage Windows Azure](http://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Pour obtenir des instructions étape par étape sur la création d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informations d’identification, consultez [créer une information d’identification](#credential) exemple plus loin dans cette rubrique.  
  
 Pour plus d’informations sur les informations d’identification en général, consultez [Informations d’identification](../security/authentication-access/credentials-database-engine.md).  
  
 Pour plus d’informations sur d’autres exemples où les informations d’identification sont utilisées, consultez [créer un Proxy de l’Agent SQL Server](../../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
###  <a name="limitations"></a> Limitations  
  
-   La sauvegarde dans le stockage Premium n’est pas prise en charge.  
  
-   La taille de sauvegarde maximale prise en charge est de 1 To.  
  
-   Publiez des instructions de sauvegarde ou de restauration à l'aide de TSQL, de SMO ou d'applets de commande PowerShell. La sauvegarde vers ou la restauration depuis le service de stockage d'objets blob Windows Azure à l'aide de l'Assistant de sauvegarde ou de restauration SQL Server Management Studio ne sont pas disponibles actuellement.  
  
-   La création d'un nom d'unité logique n'est pas prise en charge. Par conséquent, l'ajout d'une URL comme unité de sauvegarde à l'aide de sp_dumpdevice ou de SQL Server Management Studio n'est pas pris en charge.  
  
-   L'ajout d'objets blob de sauvegarde existants n'est pas pris en charge. Les sauvegardes vers un objet blob existant peuvent uniquement être remplacées à l'aide de l'option WITH FORMAT.  
  
-   La sauvegarde vers plusieurs objets blob dans le cadre d'une opération de sauvegarde n'est pas prise en charge. Par exemple, le code suivant retourne une erreur :  
  
    ```  
    BACKUP DATABASE AdventureWorks2012   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_1.bak'   
       URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_2.bak'   
          WITH CREDENTIAL = 'mycredential'   
         ,STATS = 5;  
    GO  
  
    ```  
  
-   Spécification d’une taille de bloc avec `BACKUP` n’est pas pris en charge.  
  
-   La spécification de `MAXTRANSFERSIZE` n'est pas prise en charge.  
  
-   La spécification des options backupset `RETAINDAYS` et `EXPIREDATE` n'est pas prise en charge.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est soumis à une limite de 259 caractères pour le nom d'une unité de sauvegarde. BACKUP TO URL utilise 36 caractères pour les éléments requis utilisés pour spécifier l’URL « https://.blob.core.windows.net//.bak », ce qui laisse 223 caractères pour les noms de compte, de conteneur et d’objet blob réunis.  
  
###  <a name="Support"></a> Prise en charge des instructions de sauvegarde/restauration  
  
|||||  
|-|-|-|-|  
|Instruction de sauvegarde/restauration|Pris en charge|Exceptions|Commentaires|  
|BACKUP|√|BLOCKSIZE et MAXTRANSFERSIZE ne sont pas prises en charge.|Requiert la spécification de WITH CREDENTIAL|  
|RESTORE|√||Requiert la spécification de WITH CREDENTIAL|  
|RESTORE FILELISTONLY|√||Requiert la spécification de WITH CREDENTIAL|  
|RESTORE HEADERONLY|√||Requiert la spécification de WITH CREDENTIAL|  
|RESTORE LABELONLY|√||Requiert la spécification de WITH CREDENTIAL|  
|RESTORE VERIFYONLY|√||Requiert la spécification de WITH CREDENTIAL|  
|RESTORE REWINDONLY|−|||  
  
 Pour plus d’informations sur la syntaxe et les instructions de sauvegarde, consultez [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
 Pour plus d’informations sur la syntaxe et les instructions de restauration, consultez [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).  
  
### <a name="support-for-backup-arguments"></a>Prise en charge des arguments de sauvegarde  
  
|||||  
|-|-|-|-|  
|Argument|Pris en charge|Exception|Commentaires|  
|DATABASE|√|||  
|LOG|√|||  
||  
|TO (URL)|√|Contrairement à DISK et TAPE, URL ne prend pas en charge la spécification ou la création d'un nom logique.|Cet argument est utilisé pour spécifier le chemin d'accès de l'URL du fichier de sauvegarde.|  
|MIRROR TO|−|||  
|**WITH OPTIONS :**||||  
|CREDENTIAL|√||WITH CREDENTIAL est pris en charge uniquement en cas d'utilisation de l'option BACKUP TO URL pour une sauvegarde dans le service de stockage d'objets blob Windows Azure.|  
|DIFFERENTIAL|√|||  
|COPY_ONLY|√|||  
|COMPRESSION&#124;NO_COMPRESSION|√|||  
|DESCRIPTION|√|||  
|NAME|√|||  
|EXPIREDATE &#124; RETAINDAYS|−|||  
|NOINIT &#124; INIT|−||Cette option est ignorée si elle est utilisée.<br /><br /> L'ajout aux objets blob n'est pas possible. Pour remplacer une sauvegarde, utilisez l'argument FORMAT.|  
|NOSKIP &#124; SKIP|−|||  
|NOFORMAT &#124; FORMAT|√||Cette option est ignorée si elle est utilisée.<br /><br /> Une sauvegarde effectuée sur un objet blob existant échoue à moins que WITH FORMAT ne soit spécifié. L'objet blob existant est remplacé lorsque WITH FORMAT est spécifié.|  
|MEDIADESCRIPTION|√|||  
|MEDIANAME|√|||  
|BLOCKSIZE|−|||  
|BUFFERCOUNT|√|||  
|MAXTRANSFERSIZE|−|||  
|NO_CHECKSUM &#124; CHECKSUM|√|||  
|STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR|√|||  
|STATS|√|||  
|REWIND &#124; NOREWIND|−|||  
|UNLOAD &#124; NOUNLOAD|−|||  
|NORECOVERY &#124; STANDBY|√|||  
|NO_TRUNCATE|√|||  
  
 Pour plus d’informations sur les arguments de Backup, consultez [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
### <a name="support-for-restore-arguments"></a>Prise en charge des arguments de restauration  
  
|||||  
|-|-|-|-|  
|Argument|Pris en charge|Exceptions|Commentaires|  
|DATABASE|√|||  
|LOG|√|||  
|FROM (URL)|√||L'argument FROM URL est utilisé pour spécifier le chemin d'accès de l'URL du fichier de sauvegarde.|  
|**WITH Options:**||||  
|CREDENTIAL|√||WITH CREDENTIAL est pris en charge uniquement en cas d'utilisation de l'option RESTORE FROM URL pour une restauration depuis le service de stockage d'objets blob Windows Azure.|  
|PARTIAL|√|||  
|RECOVERY &#124; NORECOVERY &#124; STANDBY|√|||  
|LOADHISTORY|√|||  
|MOVE|√|||  
|REPLACE|√|||  
|RESTART|√|||  
|RESTRICTED_USER|√|||  
|FILE|−|||  
|PASSWORD|√|||  
|MEDIANAME|√|||  
|MEDIAPASSWORD|√|||  
|BLOCKSIZE|√|||  
|BUFFERCOUNT|−|||  
|MAXTRANSFERSIZE|−|||  
|CHECKSUM &#124; NO_CHECKSUM|√|||  
|STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR|√|||  
|FILESTREAM|√|||  
|STATS|√|||  
|REWIND &#124; NOREWIND|−|||  
|UNLOAD &#124; NOUNLOAD|−|||  
|KEEP_REPLICATION|√|||  
|KEEP_CDC|√|||  
|ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER|√|||  
|STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK|√|||  
  
 Pour plus d’informations sur les arguments de Restore, consultez [Arguments RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
##  <a name="BackupTaskSSMS"></a> À l’aide de la tâche de sauvegarde dans SQL Server Management Studio  
 La tâche de sauvegarde dans SQL Server Management Studio a été améliorée avec l'ajout de l'option URL aux options de destination, et d'autres objets de prise en charge nécessaires pour la sauvegarde dans le stockage Windows Azure, comme les informations d'identification SQL.  
  
 Les étapes suivantes décrivent les modifications apportées à la tâche Sauvegarder la base de données pour autoriser la sauvegarde dans le stockage Windows Azure :  
  
1.  Démarrez SQL Server Management Studio et connectez-vous à une instance SQL Server.  Sélectionnez une base de données que vous souhaitez sauvegarder, puis avec le bouton droit sur **tâches**, puis sélectionnez **sauvegarder...** . La boîte de dialogue Sauvegarder la base de données s'ouvre.  
  
2.  Sur la page Général, l'option **URL** permet de créer une sauvegarde dans le stockage Windows Azure. Lorsque vous sélectionnez cette option, les autres options activées sur cette page s'affichent :  
  
    1.  **Nom du fichier :** nom du fichier de sauvegarde.  
  
    2.  **Informations d'identification SQL :** spécifiez des informations d'identification SQL Server existantes, ou pour en créer des nouvelles, cliquez sur **Créer** à côté de la zone Informations d'identification SQL.  
  
        > [!IMPORTANT]  
        >  La boîte de dialogue qui s'ouvre lorsque vous cliquez sur **Créer** requiert un certificat de gestion ou le profil de publication de l'abonnement. SQL Server prend actuellement en charge la version 2.0 du profil de publication. Pour télécharger la version prise en charge du profil de publication, consultez [Télécharger le profil de publication 2.0](http://go.microsoft.com/fwlink/?LinkId=396421).  
        >   
        >  Si vous n'avez pas accès au certificat de gestion ou au profil de publication, vous pouvez créer des informations d'identification SQL en spécifiant le nom du compte de stockage et les informations de clé d'accès à l'aide de Transact-SQL ou de SQL Server Management Studio. Consultez l'exemple de code dans la section [Créer des informations d'identification](#credential) pour créer des informations d'identification à l'aide de Transact-SQL. Vous pouvez également utiliser SQL Server Management Studio, depuis l'instance du moteur de base de données, et cliquer avec le bouton droit sur **Sécurité**, puis sélectionner **Nouveau**, puis **Informations d'identification**. Spécifiez le nom du compte de stockage pour **Identité** et la clé d'accès dans le champ **Mot de passe** .  
  
    3.  **Conteneur de stockage Windows Azure :** nom du conteneur de stockage Windows Azure pour stocker les fichiers de sauvegarde.  
  
    4.  **Préfixe d'URL :** ce préfixe est généré automatiquement en utilisant les informations spécifiées dans les champs décrits dans les étapes précédentes. Si vous modifiez manuellement cette valeur, assurez-vous qu'elle correspond aux autres informations spécifiées précédemment. Par exemple, si vous modifiez l'URL de stockage, vérifiez que les informations d'identification SQL sont définies pour l'authentification auprès du même compte de stockage.  
  
 Lorsque vous sélectionnez l'URL comme destination, certaines options de la page **Options de support** sont désactivées.  Les rubriques suivantes contiennent d'autres informations sur la boîte de dialogue Sauvegarder la base de données :  
  
 [Sauvegarder la base de données &#40;page Général&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
 [Sauvegarder la base de données &#40;page Options de support&#41;](back-up-database-media-options-page.md)  
  
 [Sauvegarder la base de données &#40;page Options de sauvegarde&#41;](back-up-database-backup-options-page.md)  
  
 [Créer des informations d'identification - Authentification dans le stockage Azure](create-credential-authenticate-to-azure-storage.md)  
  
##  <a name="MaintenanceWiz"></a> Sauvegarde SQL Server vers une URL à l'aide de l'Assistant Plan de maintenance  
 Comme pour la tâche de sauvegarde décrite précédemment, l'Assistant Plan de maintenance dans SQL Server Management Studio a été amélioré avec l'ajout de l'option **URL** aux options de destination, et d'autres objets de prise en charge nécessaires pour la sauvegarde dans le stockage Windows Azure, comme les informations d'identification SQL. Pour plus d’informations, consultez le **définir les tâches de sauvegarde** section [Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure).  
  
##  <a name="RestoreSSMS"></a> Restauration à partir de stockage Windows Azure en utilisant SQL Server Management Studio  
 Si vous restaurez une base de données, l'option **URL** est incluse en tant qu'unité à partir de laquelle la restauration doit être effectuée. Les étapes suivantes décrivent des modifications de la tâche de restauration pour autoriser la restauration à partir du stockage Windows Azure :  
  
1.  Lorsque vous sélectionnez **Périphériques** dans la page **Général** de la tâche de restauration dans SQL Server Management Studio, la boîte de dialogue **Sélectionner les unités de sauvegarde** s'ouvre et comprend l'option **URL** comme type de support de sauvegarde.  
  
2.  Lorsque vous sélectionnez **URL** et cliquez sur **Ajouter**, la boîte de dialogue **Se connecter au stockage Windows Azure** s'ouvre. Spécifiez les informations d'identification SQL utilisées pour l'authentification dans le stockage Windows Azure.  
  
3.  SQL Server se connecte ensuite au stockage Windows Azure en utilisant les informations d'identification SQL spécifiées et ouvre la boîte de dialogue **Localiser le fichier de sauvegarde dans Windows Azure** . Les fichiers de sauvegarde résidant dans le stockage s'affichent sur cette page. Sélectionnez le fichier à utiliser pour la restauration, puis cliquez sur **OK**. Vous revenez dans la boîte de dialogue **Sélectionner les unités de sauvegarde** , et lorsque vous cliquez sur **OK** , vous revenez dans la boîte de dialogue principale **Restaurer** où vous pourrez effectuer la restauration.  Pour plus d'informations, consultez les rubriques ci-dessous :  
  
     [Restaurer la base de données &#40;page Général&#41;](restore-database-general-page.md)  
  
     [Restaurer la base de données &#40;page Fichiers&#41;](restore-database-files-page.md)  
  
     [Restaurer la base de données &#40;page Options&#41;](restore-database-options-page.md)  
  
##  <a name="Examples"></a> Exemples de code  
 Cette section contient les exemples suivants :  
  
-   [Créer des informations d'identification](#credential)  
  
-   [Sauvegarde d'une base de données complète](#complete)  
  
-   [Sauvegarde de la base de données et du journal](#databaselog)  
  
-   [Création d’une sauvegarde de fichier complet du groupe de fichiers principal](#filebackup)  
  
-   [Création d’une sauvegarde de fichiers différentielle des groupes de fichiers principal](#differential)  
  
-   [Restauration d’une base de données et déplacement des fichiers](#restoredbwithmove)  
  
-   [Restauration jusqu'à une date et heure en utilisant STOPAT](#PITR)  
  
###  <a name="credential"></a> Créer des informations d'identification  
 L'exemple suivant crée des informations d'identification qui stockent les informations d'identification du stockage Windows Azure.  
  
1.  **TSQL**  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL mycredential WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key>' ;  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
    string secret = "<storage access key>";  
  
    // Create a Credential  
    string credentialName = "mycredential";  
    Credential credential = new Credential(server, credentialName);  
    credential.Create(identity, secret);  
    ```  
  
3.  **PowerShell**  
  
    ```  
    # create variables  
    $storageAccount = "mystorageaccount"  
    $storageKey = "<storage access key>"  
    $secureString = convertto-securestring $storageKey  -asplaintext -force  
    $credentialName = "mycredential"  
  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # Create a credential  
     New-SqlCredential -Name $credentialName -Path $srvpath -Identity $storageAccount -Secret $secureString  
  
    ```  
  
###  <a name="complete"></a> Sauvegarde d’une base de données complète  
 L'exemple suivant sauvegarde la base de données AdventureWorks2012 dans le service de stockage d'objets blob Windows Azure.  
  
1.  **TSQL**  
  
    ```  
    BACKUP DATABASE AdventureWorks2012   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
          WITH CREDENTIAL = 'mycredential'   
         ,COMPRESSION  
         ,STATS = 5;  
    GO  
  
    ```  
  
1.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
    ```  
  
2.  **PowerShell**  
  
    ```  
    # create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"   
    # for default instance, the $srvpath varilable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance  
    CD $srvPath   
    $backupFile = $backupUrlContainer + "AdventureWorks2012" +  ".bak"  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On  
  
    ```  
  
###  <a name="databaselog"></a> Sauvegarde de la base de données et du journal  
 L'exemple suivant sauvegarde l'exemple de base de données AdventureWorks2012 qui utilise par défaut le mode de récupération simple. Pour prendre en charge les sauvegardes de fichier journal, la base de données AdventureWorks2012 est modifiée pour utiliser le mode de récupération complète. Enfin, l'exemple crée une sauvegarde complète de la base de données dans l'objet blob Windows Azure, et après la mise à jour, sauvegarde le journal. Cet exemple crée un nom de fichier de sauvegarde avec un tampon d'horodateur.  
  
1.  **TSQL**  
  
    ```  
    -- To permit log backups, before the full database backup, modify the database   
    -- to use the full recovery model.  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012  
       SET RECOVERY FULL;  
    GO  
  
    -- Back up the full AdventureWorks2012 database.  
           -- First create a file name for the backup file with DateTime stamp  
  
    DECLARE @Full_Filename AS VARCHAR (300);  
    SET @Full_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Full_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.bak';   
    --Back up Adventureworks2012 database  
  
    BACKUP DATABASE AdventureWorks2012  
    TO URL =  @Full_Filename  
    WITH CREDENTIAL = 'mycredential';  
    ,COMPRESSION  
    GO  
    -- Back up the AdventureWorks2012 log.  
    DECLARE @Log_Filename AS VARCHAR (300);  
    SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
    BACKUP LOG AdventureWorks2012  
     TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,COMPRESSION;  
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url for data backup  
    string urlDataBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Data-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Database to Url  
    Backup backupData = new Backup();  
    backupData.CredentialName = credentialName;  
    backupData.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backupData.Devices.AddDevice(urlDataBackup, DeviceType.Url);  
    backupData.SqlBackup(server);  
  
    // Generate Unique Url for data backup  
    string urlLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Log-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Database Log to Url  
    Backup backupLog = new Backup();  
    backupLog.CredentialName = credentialName;  
    backupLog.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backupLog.Devices.AddDevice(urlLogBackup, DeviceType.Url);  
    backupLog.Action = BackupActionType.Log;  
    backupLog.SqlBackup(server);  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to theSQL Server Instance  
  
    CD $srvPath   
    #Create a unique file name for the full database backup  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    #Backup Database to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Database    
  
    #Create a unique file name for log backup  
  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup Log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Log  
  
    ```  
  
###  <a name="filebackup"></a> Création d’une sauvegarde de fichier complet du groupe de fichiers principal  
 L'exemple suivant crée une sauvegarde complète du groupe de fichiers principal.  
  
1.  **TSQL**  
  
    ```  
    --Back up the files in Primary:  
    BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012files.bck'  
       WITH CREDENTIAL = 'mycredential'  
       ,COMPRESSION;  
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bck",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Action = BackupActionType.Files;  
    backup.DatabaseFileGroups.Add("PRIMARY");  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to the SQL Server Instance  
  
    CD $srvPath   
    #Create a unique file name for the file backup  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bck"  
  
    #Backup Primary File Group to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary  
  
    ```  
  
###  <a name="differential"></a> Création d’une sauvegarde différentielle de fichiers du groupe de fichiers principal  
 L'exemple suivant crée une sauvegarde différentielle du groupe de fichiers principal.  
  
1.  **TSQL**  
  
    ```  
    --Back up the files in Primary:  
    BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012filesdiff.bck'  
       WITH   
          CREDENTIAL = 'mycredential'  
          ,COMPRESSION  
      ,DIFFERENTIAL;  
    GO  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Action = BackupActionType.Files;  
    backup.DatabaseFileGroups.Add("PRIMARY");  
    backup.Incremental = true;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance  
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    #Create a differential backup of the primary filegroup  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary -Incremental  
  
    ```  
  
###  <a name="restoredbwithmove"></a> Restaurer une base de données et déplacement des fichiers  
 L'exemple suivant restaure une sauvegarde complète de la base de données et déplace la base de données restaurée vers le répertoire C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data.  
  
1.  **TSQL**  
  
    ```  
    -- Backup the tail of the log first  
  
    DECLARE @Log_Filename AS VARCHAR (300);  
    SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
    BACKUP LOG AdventureWorks2012  
     TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,NORECOVERY;  
    GO  
  
    RESTORE DATABASE AdventureWorks2012 FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'  
    WITH CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,MOVE 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,STATS = 5  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    // Generate Unique Url for tail log backup  
    string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Tail Log to Url  
    Backup backupTailLog = new Backup();  
    backupTailLog.CredentialName = credentialName;  
    backupTailLog.Database = dbName;  
    backupTailLog.Action = BackupActionType.Log;  
    backupTailLog.NoRecovery = true;  
    backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
    backupTailLog.SqlBackup(server);  
  
    // Restore a database and move files  
    string newDataFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
    string newLogFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
    Restore restore = new Restore();  
    restore.CredentialName = credentialName;  
    restore.Database = dbName;  
    restore.ReplaceDatabase = true;  
    restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
    restore.RelocateFiles.Add(new RelocateFile(dbName+ "_Log", newLogFilePath));  
    restore.SqlRestore(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTNACENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance   
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    # Full database backup to URL  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On      
  
    #Create a unique file name for the tail log backup  
    $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup tail log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery    
  
    # Restore Database and move files  
  
    $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
    $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath)  
  
    ```  
  
###  <a name="PITR"></a> Restauration jusqu'à une date et heure en utilisant STOPAT  
 L'exemple suivant restaure une base de données dans l'état où elle se trouvait à un moment donné et montre une opération de restauration.  
  
1.  **TSQL**  
  
    ```  
    RESTORE DATABASE AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
    WITH   
     CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,Move 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,NORECOVERY  
    --,REPLACE  
    ,STATS = 5;  
    GO   
  
    RESTORE LOG AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.trn'   
    WITH CREDENTIAL = 'mycredential'  
    ,RECOVERY   
    ,STOPAT = 'Oct 23, 2012 5:00 PM'   
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    // Generate Unique Url for Tail Log backup  
    string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Tail Log to Url  
    Backup backupTailLog = new Backup();  
    backupTailLog.CredentialName = credentialName;  
    backupTailLog.Database = dbName;  
    backupTailLog.Action = BackupActionType.Log;  
    backupTailLog.NoRecovery = true;  
    backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
    backupTailLog.SqlBackup(server);  
  
    // Restore a database and move files  
    string newDataFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
    string newLogFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
    Restore restore = new Restore();  
    restore.CredentialName = credentialName;  
    restore.Database = dbName;  
    restore.ReplaceDatabase = true;  
    restore.NoRecovery = true;  
    restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
    restore.RelocateFiles.Add(new RelocateFile(dbName + "_Log", newLogFilePath));  
    restore.SqlRestore(server);  
  
    // Restore transaction Log with stop at   
    Restore restoreLog = new Restore();  
    restoreLog.CredentialName = credentialName;  
    restoreLog.Database = dbName;  
    restoreLog.Action = RestoreActionType.Log;  
    restoreLog.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restoreLog.ToPointInTime = DateTime.Now.ToString();   
    restoreLog.SqlRestore(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # Navigate to SQL Server Instance Directory  
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    # Full database backup to URL  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On     
  
    #Create a unique file name for the tail log backup  
    $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup tail log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery     
  
    # Restore Database and move files  
  
    $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
    $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath) -NoRecovery    
  
    # Restore Transaction log with Stop At:  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backuplogFile  -ToPointInTime (Get-Date).ToString()  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Meilleures pratiques et dépannage de sauvegarde SQL Server vers une URL](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Sauvegarder et restaurer des bases de données système &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [Didacticiel : Sauvegarde et restauration SQL Server dans le service de stockage d'objets blob Windows Azure](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
  
