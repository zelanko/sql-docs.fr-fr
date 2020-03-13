---
title: Sauvegarde SQL Server vers une URL | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 11be89e9-ff2a-4a94-ab5d-27d8edf9167d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 04f8eaf855d33faf0d2eab8fde718c92f9a24906
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289227"
---
# <a name="sql-server-backup-to-url"></a>Sauvegarde SQL Server vers une URL
  Cette rubrique présente les concepts, la configuration requise et les composants nécessaires à l’utilisation du service de stockage d’objets BLOB Azure en tant que destination de sauvegarde. Les fonctionnalités de sauvegarde et de restauration sont identiques ou similaires à l'utilisation de l'option DISK ou TAPE, à quelques différences près. Les différences, les exceptions notables et des exemples de code sont inclus dans cette rubrique.  
  
## <a name="requirements-components-and-concepts"></a>Configuration requise, composants et concepts  
 **Dans cette section :**  
  
-   [Sécurité](#security)  
  
-   [Présentation des principaux éléments et concepts](#intorkeyconcepts)  
  
-   [Service de stockage d’objets BLOB Azure](#Blob)  
  
-   [Composants SQL Server](#sqlserver)  
  
-   [Limitations](#limitations)  
  
-   [Prise en charge des instructions de sauvegarde/restauration](#Support)  
  
-   [Utilisation de la tâche de sauvegarde dans SQL Server Management Studio](sql-server-backup-to-url.md#BackupTaskSSMS)  
  
-   [Sauvegarde SQL Server vers une URL à l'aide de l'Assistant Plan de maintenance](sql-server-backup-to-url.md#MaintenanceWiz)  
  
-   [Restauration à partir du stockage Azure à l’aide de SQL Server Management Studio](sql-server-backup-to-url.md#RestoreSSMS)  
  
###  <a name="security"></a> Sécurité  
 Voici les considérations relatives à la sécurité et la configuration requise pour la sauvegarde ou la restauration à partir des services de stockage d’objets BLOB Azure.  
  
-   Lorsque vous créez un conteneur pour le service de stockage d’objets BLOB Azure, nous vous recommandons de définir l’accès sur **privé**. La définition d’un accès privé limite l’accès aux seuls utilisateurs ou comptes capables de fournir les informations nécessaires pour s’authentifier auprès du compte Azure.  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]requiert que le nom du compte Azure et l’authentification de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clé d’accès soient stockés dans les informations d’identification. Ces informations sont utilisées pour l’authentification auprès du compte Azure lorsqu’il effectue des opérations de sauvegarde ou de restauration.  
  
-   Le compte d’utilisateur utilisé pour émettre les commandes BACKUP (sauvegarder) ou RESTORE (restaurer) doit figurer dans le rôle de base de données **db_backup operator** avec les autorisations **Modifier des informations d’identification** .  
  
###  <a name="intorkeyconcepts"></a> Présentation des principaux éléments et concepts  
 Les deux sections suivantes présentent le service de stockage d’objets BLOB Azure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ainsi que les composants utilisés lors de la sauvegarde ou de la restauration à partir du service de stockage d’objets BLOB Azure. Il est important de comprendre les composants et leur interaction pour effectuer une sauvegarde ou une restauration à partir du service de stockage d’objets BLOB Azure.  
  
 La création d’un compte Azure est la première étape de ce processus. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]utilise le **nom du compte de stockage Azure** et ses valeurs de **clé d’accès** pour authentifier et écrire et lire les objets BLOB dans le service de stockage. Les informations d'identification de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stockent ces informations et sont utilisées lors des opérations de sauvegarde ou de restauration. Pour une procédure pas à pas complète de création d’un compte de stockage et d’exécution d’une restauration simple, consultez [didacticiel utilisation du service de stockage Azure pour la sauvegarde et la restauration de SQL Server](https://go.microsoft.com/fwlink/?LinkId=271615).  
  
 ![mappage de la compte de stockage à l'information d'identification](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "mappage de la compte de stockage à l'information d'identification")  
  
###  <a name="Blob"></a>Service de stockage d’objets BLOB Azure  
 **Compte de stockage :** Le compte de stockage constitue le point de départ de tous les services de stockage. Pour accéder au service de stockage d’objets BLOB Azure, commencez par créer un compte de stockage Azure. Le **nom du compte de stockage** et ses propriétés de **clé d’accès** sont requis pour l’authentification auprès du service de stockage d’objets BLOB Azure et de ses composants.  
  
 **Conteneur :** Un conteneur permet de regrouper un ensemble d’objets BLOB et peut stocker un nombre illimité d’objets BLOB. Pour écrire une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sauvegarde dans le service d’objets BLOB Azure, vous devez avoir au moins le conteneur racine créé.  
  
 **Objet blob :** Fichier de tout type et de toute taille. Il existe deux types d’objets BLOB qui peuvent être stockés dans le service de stockage d’objets BLOB Azure : les objets BLOB de blocs et de pages. La sauvegarde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des objets blob de pages en tant que type d'objet blob. Les objets BLOB sont adressables à l’aide du format\<d’URL suivant : compte\<de stockage https://\<>. blob.Core.Windows.NET/conteneur>/BLOB>  
  
 ![Stockage Blob Azure](../../database-engine/media/backuptocloud-blobarchitecture.gif "Stockage Blob Azure")  
  
 Pour plus d’informations sur le service de stockage d’objets BLOB Azure, consultez la page [utilisation du service de stockage d’objets BLOB Azure](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)  
  
 Pour plus d’informations sur les blobs, consultez [Présentation des objets blob de blocs et des objets blob de pages](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx)  
  
###  <a name="sqlserver"></a> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Composants  
 **URL :** Une URL spécifie un URI (Uniform Resource Identifier) pour un fichier de sauvegarde unique. L'URL est utilisée pour indiquer l'emplacement et le nom du fichier de sauvegarde de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Dans cette implémentation, la seule URL valide est celle qui pointe vers un objet blob de pages dans un compte de stockage Azure. L'URL doit pointer vers un objet blob réel et pas un simple conteneur. Si l'objet blob n'existe pas, il est créé. Si un objet BLOB existant est spécifié, la sauvegarde échoue, sauf si l’option « WITH FORMAT » est spécifiée.  
  
> [!WARNING]  
>  Si vous choisissez de copier et de charger un fichier de sauvegarde dans le service de stockage d’objets BLOB Azure, utilisez l’objet blob de pages comme option de stockage. Les restaurations à partir d'objets blob de blocs ne sont pas prises en charge. Une restauration à partir d'un type d'objet blob de blocs échoue avec une erreur.  
  
 Voici un exemple de valeur d’URL : http [s] :\<//ACCOUNTNAME.Blob.core.windows.net/Container>\</filename. bak>. HTTPS n'est pas obligatoire, mais est recommandé.  
  
 **Informations d’identification :** Les informations d'identification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont des objets utilisés pour stocker les informations d'authentification requises pour la connexion à une ressource en dehors de SQL Server.  Ici, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les processus de sauvegarde et de restauration utilisent les informations d’identification pour s’authentifier auprès du service de stockage d’objets BLOB Azure. Les informations d'identification contiennent le nom du compte de stockage et ses valeurs de **clé d'accès** . Une fois les informations d'identification créées, vous devez les spécifier dans l'option WITH CREDENTIAL lorsque vous publiez des instructions BACKUP/RESTORE. Pour plus d'informations sur l'affichage, la copie ou la régénération des **access keys**de compte de stockage, consultez [Afficher, copier et régénérer les clés d'accès d'un compte de stockage Windows Azure](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Pour obtenir des instructions détaillées sur la création d'informations d'identification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez l'exemple [Create a Credential](#credential) plus loin dans cette rubrique.  
  
 Pour plus d’informations sur les informations d’identification en général, consultez [Informations d’identification](../security/authentication-access/credentials-database-engine.md).  
  
 Pour plus d’informations sur d’autres exemples d’utilisation des informations d’identification, consultez [créer un Proxy SQL Server Agent](../../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
###  <a name="limitations"></a> Limitations  
  
-   La sauvegarde dans le stockage Premium n’est pas prise en charge.  
  
-   La taille de sauvegarde maximale prise en charge est de 1 To.  
  
-   Publiez des instructions de sauvegarde ou de restauration à l'aide de TSQL, de SMO ou d'applets de commande PowerShell. Une sauvegarde ou une restauration à partir du service de stockage d’objets BLOB Azure à l’aide de SQL Server Management Studio Assistant de sauvegarde ou de restauration n’est pas activée actuellement.  
  
-   La création d'un nom d'unité logique n'est pas prise en charge. Par conséquent, l'ajout d'une URL comme unité de sauvegarde à l'aide de sp_dumpdevice ou de SQL Server Management Studio n'est pas pris en charge.  
  
-   L'ajout d'objets blob de sauvegarde existants n'est pas pris en charge. Les sauvegardes vers un objet blob existant peuvent uniquement être remplacées à l'aide de l'option WITH FORMAT.  
  
-   La sauvegarde vers plusieurs objets blob dans le cadre d'une opération de sauvegarde n'est pas prise en charge. Par exemple, le code suivant retourne une erreur :  
  
    ```sql
    BACKUP DATABASE AdventureWorks2012
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_1.bak'
       URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_2.bak'
          WITH CREDENTIAL = 'mycredential'
         ,STATS = 5;  
    GO
    ```  
  
-   La spécification d'une taille de bloc avec `BACKUP` n'est pas prise en charge.  
  
-   La spécification de `MAXTRANSFERSIZE` n'est pas prise en charge.  
  
-   La spécification des options backupset `RETAINDAYS` et `EXPIREDATE` n'est pas prise en charge.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est soumis à une limite de 259 caractères pour le nom d'une unité de sauvegarde. BACKUP TO URL utilise 36 caractères pour les éléments requis utilisés pour spécifier l’URL « https://.blob.core.windows.net//.bak  », ce qui laisse 223 caractères pour les noms de compte, de conteneur et d’objet blob réunis.  
  
###  <a name="Support"></a> Prise en charge des instructions de sauvegarde/restauration  
  
|||||  
|-|-|-|-|  
|Instruction de sauvegarde/restauration|Prise en charge|Exceptions|Commentaires|  
|BACKUP|&#x2713;|BLOCKSIZE et MAXTRANSFERSIZE ne sont pas prises en charge.|Requiert la spécification de WITH CREDENTIAL|  
|RESTORE|&#x2713;||Requiert la spécification de WITH CREDENTIAL|  
|RESTORE FILELISTONLY|&#x2713;||Requiert la spécification de WITH CREDENTIAL|  
|RESTORE HEADERONLY|&#x2713;||Requiert la spécification de WITH CREDENTIAL|  
|RESTORE LABELONLY|&#x2713;||Requiert la spécification de WITH CREDENTIAL|  
|RESTORE VERIFYONLY|&#x2713;||Requiert la spécification de WITH CREDENTIAL|  
|RESTORE REWINDONLY|&#x2713;|||  
  
 Pour plus d’informations sur la syntaxe et les instructions de sauvegarde, consultez [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
 Pour plus d’informations sur la syntaxe et les instructions de restauration, consultez [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).  
  
### <a name="support-for-backup-arguments"></a>Prise en charge des arguments de sauvegarde  
  
|||||  
|-|-|-|-|  
|Argument|Prise en charge|Exception|Commentaires|  
|DATABASE|&#x2713;|||  
|LOG|&#x2713;|||  
||  
|TO (URL)|&#x2713;|Contrairement à DISK et TAPE, URL ne prend pas en charge la spécification ou la création d'un nom logique.|Cet argument est utilisé pour spécifier le chemin d'accès de l'URL du fichier de sauvegarde.|  
|MIRROR TO|&#x2713;|||  
|**WITH OPTIONS :**||||  
|CREDENTIAL|&#x2713;||WITH CREDENTIAL est pris en charge uniquement lors de l’utilisation de l’option BACKUP TO URL pour sauvegarder dans le service de stockage d’objets BLOB Azure.|  
|DIFFERENTIAL|&#x2713;|||  
|COPY_ONLY|&#x2713;|||  
|COMPRESSION&#124;NO_COMPRESSION|&#x2713;|||  
|Description|&#x2713;|||  
|NAME|&#x2713;|||  
|EXPIREDATE &#124; RETAINDAYS|&#x2713;|||  
|NOINIT &#124; INIT|&#x2713;||Cette option est ignorée si elle est utilisée.<br /><br /> L'ajout aux objets blob n'est pas possible. Pour remplacer une sauvegarde, utilisez l'argument FORMAT.|  
|NOSKIP &#124; SKIP|&#x2713;|||  
|NOFORMAT &#124; FORMAT|&#x2713;||Cette option est ignorée si elle est utilisée.<br /><br /> Une sauvegarde effectuée sur un objet blob existant échoue à moins que WITH FORMAT ne soit spécifié. L'objet blob existant est remplacé lorsque WITH FORMAT est spécifié.|  
|MEDIADESCRIPTION|&#x2713;|||  
|MEDIANAME|&#x2713;|||  
|BLOCKSIZE|&#x2713;|||  
|BUFFERCOUNT|&#x2713;|||  
|MAXTRANSFERSIZE|&#x2713;|||  
|NO_CHECKSUM &#124; CHECKSUM|&#x2713;|||  
|STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR|&#x2713;|||  
|STATS|&#x2713;|||  
|REWIND &#124; NOREWIND|&#x2713;|||  
|UNLOAD &#124; NOUNLOAD|&#x2713;|||  
|NORECOVERY &#124; STANDBY|&#x2713;|||  
|NO_TRUNCATE|&#x2713;|||  
  
 Pour plus d’informations sur les arguments de Backup, consultez [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
### <a name="support-for-restore-arguments"></a>Prise en charge des arguments de restauration  
  
|||||  
|-|-|-|-|  
|Argument|Prise en charge|Exceptions|Commentaires|  
|DATABASE|&#x2713;|||  
|LOG|&#x2713;|||  
|FROM (URL)|&#x2713;||L'argument FROM URL est utilisé pour spécifier le chemin d'accès de l'URL du fichier de sauvegarde.|  
|**WITH Options:**||||  
|CREDENTIAL|&#x2713;||WITH CREDENTIAL est pris en charge uniquement lors de l’utilisation de l’option Restore FROM URL pour restaurer à partir du service de stockage d’objets BLOB Azure.|  
|PARTIAL|&#x2713;|||  
|RECOVERY &#124; NORECOVERY &#124; STANDBY|&#x2713;|||  
|LOADHISTORY|&#x2713;|||  
|MOVE|&#x2713;|||  
|REPLACE|&#x2713;|||  
|RESTART|&#x2713;|||  
|RESTRICTED_USER|&#x2713;|||  
|FILE|&#x2713;|||  
|PASSWORD|&#x2713;|||  
|MEDIANAME|&#x2713;|||  
|MEDIAPASSWORD|&#x2713;|||  
|BLOCKSIZE|&#x2713;|||  
|BUFFERCOUNT|&#x2713;|||  
|MAXTRANSFERSIZE|&#x2713;|||  
|CHECKSUM &#124; NO_CHECKSUM|&#x2713;|||  
|STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR|&#x2713;|||  
|FILESTREAM|&#x2713;|||  
|STATS|&#x2713;|||  
|REWIND &#124; NOREWIND|&#x2713;|||  
|UNLOAD &#124; NOUNLOAD|&#x2713;|||  
|KEEP_REPLICATION|&#x2713;|||  
|KEEP_CDC|&#x2713;|||  
|ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER|&#x2713;|||  
|STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK|&#x2713;|||  
  
 Pour plus d’informations sur les arguments de Restore, consultez [Arguments RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
##  <a name="BackupTaskSSMS"></a>Utilisation de la tâche de sauvegarde dans SQL Server Management Studio  
 La tâche de sauvegarde de SQL Server Management Studio a été améliorée de façon à inclure l’URL comme l’une des options de destination, ainsi que d’autres objets de prise en charge nécessaires à la sauvegarde dans le stockage Azure, comme les informations d’identification SQL.  
  
 Les étapes suivantes décrivent les modifications apportées à la tâche sauvegarder la base de données pour permettre la sauvegarde vers le stockage Azure :  
  
1.  Démarrez SQL Server Management Studio et connectez-vous à une instance SQL Server.  Sélectionnez une base de données que vous souhaitez sauvegarder, cliquez avec le bouton droit sur **tâches**, puis sélectionnez **sauvegarder..**. La boîte de dialogue sauvegarder la base de données s’ouvre.  
  
2.  Sur la page général, l’option **URL** permet de créer une sauvegarde dans le stockage Azure. Lorsque vous sélectionnez cette option, les autres options activées sur cette page s'affichent :  
  
    1.  **Nom du fichier :** Nom du fichier de sauvegarde.  
  
    2.  **Informations d’identification SQL :** Vous pouvez spécifier un SQL Server d’informations d’identification existant ou en créer un en cliquant sur le bouton **créer** en regard de la zone informations d’identification SQL.  
  
        > [!IMPORTANT]  
        >  La boîte de dialogue qui s'ouvre lorsque vous cliquez sur **Créer** requiert un certificat de gestion ou le profil de publication de l'abonnement. SQL Server prend actuellement en charge la version 2.0 du profil de publication. Pour télécharger la version prise en charge du profil de publication, consultez [Télécharger le profil de publication 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
        >   
        >  Si vous n'avez pas accès au certificat de gestion ou au profil de publication, vous pouvez créer des informations d'identification SQL en spécifiant le nom du compte de stockage et les informations de clé d'accès à l'aide de Transact-SQL ou de SQL Server Management Studio. Consultez l'exemple de code dans la section [Créer des informations d'identification](#credential) pour créer des informations d'identification à l'aide de Transact-SQL. Vous pouvez également utiliser SQL Server Management Studio, depuis l'instance du moteur de base de données, et cliquer avec le bouton droit sur **Sécurité**, puis sélectionner **Nouveau**, puis **Informations d'identification**. Spécifiez le nom du compte de stockage pour **Identité** et la clé d'accès dans le champ **Mot de passe** .  
  
    3.  **Conteneur de stockage Azure :** Nom du conteneur de stockage Azure dans lequel stocker les fichiers de sauvegarde.  
  
    4.  **Préfixe d’URL :** Elle est générée automatiquement à l’aide des informations spécifiées dans les champs décrits dans les étapes précédentes. Si vous modifiez manuellement cette valeur, assurez-vous qu'elle correspond aux autres informations spécifiées précédemment. Par exemple, si vous modifiez l'URL de stockage, vérifiez que les informations d'identification SQL sont définies pour l'authentification auprès du même compte de stockage.  
  
 Quand vous sélectionnez URL comme destination, certaines options de la page **Options de support** sont désactivées.  Les rubriques suivantes contiennent d'autres informations sur la boîte de dialogue Sauvegarder la base de données :  
  
 [Sauvegarder la base de données &#40;page Général&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
 [Sauvegarder la base de données &#40;page Options de support&#41;](back-up-database-media-options-page.md)  
  
 [Sauvegarder la base de données &#40;page Options de sauvegarde&#41;](back-up-database-backup-options-page.md)  
  
 [Créer des informations d’identification - Authentification Azure Storage](create-credential-authenticate-to-azure-storage.md)  
  
##  <a name="MaintenanceWiz"></a> Sauvegarde SQL Server vers une URL à l'aide de l'Assistant Plan de maintenance  
 Comme pour la tâche de sauvegarde décrite précédemment, l’Assistant Plan de maintenance de SQL Server Management Studio a été amélioré pour inclure l' **URL** comme l’une des options de destination, ainsi que d’autres objets de prise en charge nécessaires à la sauvegarde dans le stockage Azure, comme les informations d’identification SQL. Pour plus d'informations, consultez la section **Définir les tâches de sauvegarde** dans [Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure).  
  
##  <a name="RestoreSSMS"></a>Restauration à partir d’Azure Storage à l’aide de SQL Server Management Studio  
 Si vous restaurez une base de données, l'option **URL** est incluse en tant qu'unité à partir de laquelle la restauration doit être effectuée. Les étapes suivantes décrivent les modifications apportées à la tâche de restauration pour autoriser la restauration à partir du stockage Azure :  
  
1.  Lorsque vous sélectionnez **Périphériques** dans la page **Général** de la tâche de restauration dans SQL Server Management Studio, la boîte de dialogue **Sélectionner les unités de sauvegarde** s'ouvre et comprend l'option **URL** comme type de support de sauvegarde.  
  
2.  Lorsque vous sélectionnez **URL** et cliquez sur **Ajouter**, la boîte de dialogue **Se connecter au stockage Windows Azure** s'ouvre. Spécifiez les informations d’identification SQL pour l’authentification auprès du stockage Azure.  
  
3.  SQL Server se connecte ensuite au stockage Azure à l’aide des informations d’identification SQL que vous avez fournies et ouvre la boîte **de dialogue localiser le fichier de sauvegarde dans Azure** . Les fichiers de sauvegarde résidant dans le stockage s'affichent sur cette page. Sélectionnez le fichier à utiliser pour la restauration, puis cliquez sur **OK**. Vous revenez dans la boîte de dialogue **Sélectionner les unités de sauvegarde**, et lorsque vous cliquez sur **OK**, vous revenez dans la boîte de dialogue principale **Restaurer** où vous pourrez effectuer la restauration.  Pour plus d'informations, consultez les rubriques ci-dessous :  
  
     [Restaurer la base de données &#40;page Général&#41;](restore-database-general-page.md)  
  
     [Restaurer la base de données &#40;page Fichiers&#41;](restore-database-files-page.md)  
  
     [Restaurer la base de données &#40;page Options&#41;](restore-database-options-page.md)  
  
##  <a name="Examples"></a> Exemples de code  
 Cette section contient les exemples suivants :  
  
-   [Créer des informations d'identification](#credential)  
  
-   [Sauvegarde d'une base de données complète](#complete)  
  
-   [Sauvegarde de la base de données et du journal](#databaselog)  
  
-   [Création d'une sauvegarde complète du groupe de fichiers principal](#filebackup)  
  
-   [Création d'une sauvegarde différentielle du groupe de fichiers principal](#differential)  
  
-   [Restauration d’une base de données et déplacement des fichiers](#restoredbwithmove)  
  
-   [Restauration jusqu'à une date et heure en utilisant STOPAT](#PITR)  
  
###  <a name="credential"></a> Créer des informations d'identification  
 L’exemple suivant crée des informations d’identification qui stockent les informations d’authentification Azure Storage.  

   ```sql
   IF NOT EXISTS  
   (SELECT * FROM sys.credentials   
   WHERE credential_identity = 'mycredential')  
   CREATE CREDENTIAL mycredential WITH IDENTITY = 'mystorageaccount'  
   ,SECRET = '<storage access key>' ;  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
   string secret = "<storage access key>";  
  
   // Create a Credential  
   string credentialName = "mycredential";  
   Credential credential = new Credential(server, credentialName);  
   credential.Create(identity, secret);  
   ```  
  
   ```powershell
   # create variables  
   $storageAccount = "mystorageaccount"  
   $storageKey = "<storage access key>"  
   $secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
   $credentialName = "mycredential"  
  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # Create a credential  
   New-SqlCredential -Name $credentialName -Path $srvpath -Identity $storageAccount -Secret $secureString
   ```  
  
###  <a name="complete"></a>Sauvegarde d’une base de données complète  
 L’exemple suivant sauvegarde la base de données AdventureWorks2012 dans le service de stockage d’objets BLOB Azure.
  
   ```sql
   BACKUP DATABASE AdventureWorks2012   
   TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
         WITH CREDENTIAL = 'mycredential'   
         ,COMPRESSION  
         ,STATS = 5;  
   GO
   ```  
  
   ```csharp
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
  
   ```powershell
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
  
###  <a name="databaselog"></a>Sauvegarde de la base de données et du journal  
 L'exemple suivant sauvegarde l'exemple de base de données AdventureWorks2012 qui utilise par défaut le mode de récupération simple. Pour prendre en charge les sauvegardes de fichier journal, la base de données AdventureWorks2012 est modifiée pour utiliser le mode de récupération complète. L’exemple crée ensuite une sauvegarde complète de base de données dans l’objet BLOB Azure et, après une période d’activité de mise à jour, sauvegarde le journal. Cet exemple crée un nom de fichier de sauvegarde avec un tampon d'horodateur.  
  
   ```sql
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
  
   ```csharp
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

   ```powershell
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
  
###  <a name="filebackup"></a>Création d’une sauvegarde complète du groupe de fichiers primaire  
 L'exemple suivant crée une sauvegarde complète du groupe de fichiers principal.
  
   ```sql
   --Back up the files in Primary:  
   BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012files.bck'  
       WITH CREDENTIAL = 'mycredential'  
       ,COMPRESSION;  
   GO  
   ```
  
   ```csharp
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
  
   ```powershell
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
  
###  <a name="differential"></a>Création d’une sauvegarde différentielle du groupe de fichiers primaire  
 L'exemple suivant crée une sauvegarde différentielle du groupe de fichiers principal.  
  
   ```sql
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
  
   ```csharp
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

   ```powershell
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
  
###  <a name="restoredbwithmove"></a>Restaurer une base de données et déplacer des fichiers  
 L'exemple suivant restaure une sauvegarde complète de la base de données et déplace la base de données restaurée vers le répertoire C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data.
  
   ```sql
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
  
   ```csharp
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

   ```powershell
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
  
   ```sql
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
  
   ```csharp
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
  
   ```powershell
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
 [Sauvegarde et restauration des bases de données système &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
