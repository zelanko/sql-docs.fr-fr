---
title: "Bonnes pratiques en matière de sauvegarde SQL Server vers une URL et résolution des problèmes associés | Microsoft Docs"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 06e3118f67db6f01dad0344b42024534081433fb
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a>Meilleures pratiques et dépannage de sauvegarde SQL Server vers une URL
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique présente les pratiques recommandées et des conseils de dépannage pour la sauvegarde et la restauration SQL Server dans le service d'objets blob Windows Azure.  
  
 Pour plus d'informations sur l'utilisation du service de stockage d'objets blob Windows Azure pour les opérations de sauvegarde et de restauration SQL Server, consultez :  
  
-   [Sauvegarde et restauration SQL Server avec le service de stockage d’objets blob Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [Didacticiel : Sauvegarde et restauration SQL Server dans le service de stockage d’objets blob Windows Azure](~/relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a>Gestion des sauvegardes  
 La liste suivante comprend des recommandations générales sur la gestion des sauvegardes :  
  
-   Nous vous recommandons d'utiliser un nom de fichier unique pour chaque sauvegarde afin d'éviter tout remplacement accidentel des objets blob.  
  
-   Lors de la création d'un conteneur, nous vous recommandons de configurer le niveau d'accès sur **Privé**, afin que seuls les utilisateurs ou comptes qui peuvent fournir les informations d'identification requises puissent lire ou écrire les objets blob dans le conteneur.  
  
-   Pour les bases de données SQL Server situées sur une instance de SQL Server s'exécutant sur un ordinateur virtuel Windows Azure, utilisez un compte de stockage situé dans la même région que l'ordinateur virtuel afin d'éviter les coûts de transfert de données entre les régions. L'utilisation de la même région garantit également des performances optimales pour les opérations de sauvegarde et de restauration.  
  
-   L'échec d'une activité de sauvegarde peut générer un fichier de sauvegarde non valide. Nous vous recommandons d'identifier périodiquement les sauvegardes en échec et de supprimer les fichiers d'objets blob. Pour plus d'informations, consultez [Deleting Backup Blob Files with Active Leases](../../relational-databases/backup-restore/deleting-backup-blob-files-with-active-leases.md)  
  
-   L'utilisation de **WITH COMPRESSION** pendant la sauvegarde peut réduire les coûts du stockage et des transactions de stockage. Elle peut également réduire le temps nécessaire pour terminer le processus de sauvegarde.  
  
## <a name="handling-large-files"></a>Gestion des fichiers volumineux  
  
-   L'opération de sauvegarde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise plusieurs threads pour optimiser le transfert de données vers les services de stockage d'objets blob Windows Azure.  Toutefois, les performances dépendent de divers facteurs, tels que la bande passante de l'éditeur de logiciels et la taille de la base de données. Si vous envisagez de sauvegarder des bases de données ou groupes de fichiers volumineux à partir d'une base de données SQL Server locale, nous vous recommandons de commencer par tester le débit. Le [SLA pour Storage](http://azure.microsoft.com/support/legal/sla/storage/v1_0/) de Microsoft Azure impose des temps de traitement maximum pour les objets blob dont vous devez tenir compte.  
  
-   L'utilisation de l'option **WITH COMPRESSION** , comme recommandé dans la section **Gestion de la sauvegarde** , est très importante lors de la sauvegarde de fichiers volumineux.  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a>Dépannage des problèmes de sauvegarde vers une URL ou de restauration depuis une URL  
 Voici quelques méthodes rapides qui vous aideront à résoudre les erreurs survenant lors de la sauvegarde ou de la restauration vers/depuis le service de stockage d'objets blob Windows Azure.  
  
 Pour éviter les erreurs attribuables à des limitations ou à des options non prises en charge, consultez la liste des limitations, ainsi que l’aide sur les commandes BACKUP et RESTORE dans l’article [Sauvegarde et restauration SQL Server avec le service Microsoft Azure Blob Storage](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) .  
  
 **Erreurs d'authentification :**  
  
-   WITH CREDENTIAL est une nouvelle option requise pour la sauvegarde ou la restauration vers/depuis le service de stockage d'objets blob Windows Azure. Les défaillances liées aux informations d'identification peuvent être les suivantes :  
  
     Les informations d'identification spécifiées dans la commande **BACKUP** ou **RESTORE** n'existent pas. Pour éviter ce problème, vous pouvez inclure des instructions T-SQL afin de créer les informations d'identification si elles n'existent pas dans l'instruction de sauvegarde. Voici un exemple que vous pouvez utiliser :  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   Les informations d'identification existent, mais le compte de connexion utilisé pour exécuter la commande de sauvegarde ne dispose pas des autorisations appropriées pour accéder aux informations d'identification. Utilisez un compte de connexion dans le rôle **db_backupoperator** avec des autorisations **Modifier des informations d’identification** .  
  
-   Vérifiez le nom du compte de stockage et la valeur des clés. Les informations stockées dans les informations d'identification doivent correspondre aux valeurs de propriétés du compte de stockage Windows Azure utilisé lors des opérations de sauvegarde et de restauration.  
  
 **Erreurs/Échecs de sauvegarde :**  
  
-   Les sauvegardes parallèles dans un même objet blob provoquent l'échec d'une des sauvegardes avec l'erreur **Échec de l’initialisation** .  
  
-   Utilisez les journaux d'erreurs suivants pour vous aider à résoudre les erreurs de sauvegarde :  
  
    -   Définissez l'indicateur de trace 3051 pour activer la journalisation dans un journal des erreurs spécifique au format suivant :  
  
         BackupToUrl\<nom_instance>-\<nom_bd>-action-\<PID>.log Où \<action> a l’une des valeurs suivantes :  
  
        -   **BdD**  
  
        -   **FILELISTONLY**  
  
        -   **LABELONLY**  
  
        -   **HEADERONLY**  
  
        -   **VERIFYONLY**  
  
    -   Vous pouvez également trouver des informations en examinant le journal des événements Windows nommé « SQLBackupToUrl » sous Journaux d'application.  
  
-   En cas de restauration d'une sauvegarde compressée, vous pouvez rencontrer l'erreur suivante :  
  
    -   **Une exception SqlException 3284 s’est produite. Gravité : 16 État : 5**  
        **Message : La marque de fichier du périphérique « https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak » n’est pas alignée. Réexécutez l’instruction Restore avec la même taille de bloc que celle utilisée pour créer le jeu de sauvegarde : « 65536 » semble une valeur possible.**  
  
         Pour résoudre cette erreur, réexécutez l’instruction **BACKUP** en spécifiant **BLOCKSIZE = 65536** .  
  
-   Erreur lors de la sauvegarde en raison d'objets blob avec un bail actif : l'activité de sauvegarde en échec peut générer des objets blob avec des baux actifs.  
  
     Si une instruction de sauvegarde est retentée, l'opération de sauvegarde échoue avec une erreur semblable à celle qui suit :  
  
     **La sauvegarde vers l'URL a reçu une exception du point de terminaison distant. Message d’exception : Le serveur distant a retourné une erreur : (412) Il y a actuellement un bail sur l’objet blob et aucun ID de bail n’a été spécifié dans la requête**.  
  
     Si une instruction de restauration est tentée sur un fichier de sauvegarde d'objet blob dont le bail est actif, l'opération de restauration échoue avec une erreur semblable à celle qui suit :  
  
     **Message d'exception : Le serveur distant a retourné une erreur : (409) Conflit.**  
  
     Lorsqu'une telle erreur se produit, les fichiers d'objets blob doivent être supprimés. Pour plus d'informations sur ce scénario et la résolution du problème, consultez [Deleting Backup Blob Files with Active Leases](../../relational-databases/backup-restore/deleting-backup-blob-files-with-active-leases.md)  
  
## <a name="proxy-errors"></a>Erreurs de proxy  
 Si vous utilisez des serveurs proxy pour l'accès à Internet, les erreurs suivantes peuvent survenir :  
  
 **Limitation de la connexion par les serveurs proxy :**  
  
 Les serveurs proxy peuvent avoir des paramètres qui limitent le nombre de connexions par minute. Le processus de sauvegarde vers l'URL est un processus multithread et, par conséquent, il peut dépasser cette limite. Si cela se produit, le serveur proxy supprime la connexion. Pour résoudre ce problème, modifiez les paramètres du proxy afin que SQL Server n'utilise pas le proxy.   Voici quelques exemples des types d'erreur ou des messages qui peuvent s'afficher dans le journal des erreurs :  
  
-   Échec de l’opération d’écriture sur « http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak » : la sauvegarde vers l’URL a reçu une exception du point de terminaison distant. Message d'exception : impossible de lire les données de la connexion de transport : la connexion a été fermée.  
  
-   Une erreur d’E/S non récupérable s’est produite dans le fichier « http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak » : l’erreur n’a pas pu être collectée à partir du point de terminaison distant.  
  
     Msg 3013, Niveau 16, État 1, Ligne 2  
  
     La sauvegarde de base de données s'est terminée anormalement.  
  
-   BackupIoRequest::ReportIoError : échec d’écriture sur l’unité de sauvegarde http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak. Erreur de système d'exploitation. La sauvegarde vers l'URL a reçu une exception du point de terminaison distant. Message d'exception : impossible de lire les données de la connexion de transport : la connexion a été fermée.  
  
 Si vous activez la journalisation détaillée à l'aide de l'indicateur de trace 3051, vous pouvez également voir le message suivant dans les journaux :  
  
 Code d'état HTTP 502, message d'état HTTP, erreur de proxy (le nombre de requêtes HTTP par minute a dépassé la limite configurée. Contactez votre administrateur ISA Server.  )  
  
 **Les paramètres du proxy par défaut ne sont pas sélectionnés :**  
  
 Parfois, les paramètres par défaut ne sont pas sélectionnés et provoquent des erreurs d'authentification du proxy telles que celle affichée ci-dessous :*Une erreur d'E/S non récupérable s'est produite dans le fichier « http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak : ». La sauvegarde vers l'URL a reçu une exception du point de terminaison distant. Message d’exception : Le serveur distant a retourné une erreur : (407)* **Authentification du proxy nécessaire**.  
  
 Pour résoudre ce problème, créez un fichier de configuration qui permet au processus de sauvegarde vers l'URL d'utiliser les paramètres du proxy par défaut à l'aide des étapes suivantes :  
  
1.  Créez un fichier de configuration nommé BackuptoURL.exe.config avec le code xml suivant :  
  
    ```  
    \<?xml version ="1.0"?>  
    <configuration>   
                    \<system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    \</system.net>  
    </configuration>  
  
    ```  
  
2.  Placez le fichier de configuration dans le dossier Binn de l'instance de SQL Server. Par exemple, si mon instance de SQL Server est installée sur le lecteur C de l’ordinateur, placez le fichier de configuration ici : *C:\Program Files\Microsoft SQL Server\MSSQL13.\<nom_instance>\MSSQL\Binn*.  
  
## <a name="see-also"></a>Voir aussi  
 [Restauration à partir de sauvegardes stockées dans Windows Azure](../../relational-databases/backup-restore/restoring-from-backups-stored-in-microsoft-azure.md)  
[BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)  
[RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)
  

