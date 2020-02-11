---
title: Bonnes pratiques en matière de sauvegarde SQL Server vers une URL et résolution des problèmes associés | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ac34c95e7ee4dc6f57ef7d8806a7db1bb981a944
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70175965"
---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a>Meilleures pratiques et dépannage de sauvegarde SQL Server vers une URL
  Cette rubrique présente des bonnes pratiques et des conseils de dépannage pour la sauvegarde et la restauration SQL Server dans le service Blob Azure.  
  
 Pour plus d’informations sur l’utilisation du service de stockage Blob Azure pour les opérations de sauvegarde et de restauration SQL Server, consultez :  
  
-   [Sauvegarde et restauration SQL Server avec le service Stockage Blob Azure](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [Didacticiel : Sauvegarde et restauration SQL Server dans le service Stockage Blob Azure](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a>Gestion des sauvegardes  
 La liste suivante comprend des recommandations générales sur la gestion des sauvegardes :  
  
-   Nous vous recommandons d'utiliser un nom de fichier unique pour chaque sauvegarde afin d'éviter tout remplacement accidentel des objets blob.  
  
-   Lors de la création d'un conteneur, nous vous recommandons de configurer le niveau d'accès sur **Privé**, afin que seuls les utilisateurs ou comptes qui peuvent fournir les informations d'identification requises puissent lire ou écrire les objets blob dans le conteneur.  
  
-   Pour SQL Server bases de données sur une instance de SQL Server s’exécutant sur une machine virtuelle Azure, utilisez un compte de stockage dans la même région que la machine virtuelle afin d’éviter les coûts de transfert de données entre les régions. L'utilisation de la même région garantit également des performances optimales pour les opérations de sauvegarde et de restauration.  
  
-   L'échec d'une activité de sauvegarde peut générer un fichier de sauvegarde non valide. Nous vous recommandons d'identifier périodiquement les sauvegardes en échec et de supprimer les fichiers d'objets blob. Pour plus d'informations, consultez [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)  
  
-   L'utilisation de `WITH COMPRESSION` pendant la sauvegarde peut réduire les coûts du stockage et des transactions de stockage. Elle peut également réduire le temps nécessaire pour terminer le processus de sauvegarde.  
  
## <a name="handling-large-files"></a>Gestion des fichiers volumineux  
  
-   L’opération de sauvegarde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise plusieurs threads pour optimiser le transfert de données vers les services de stockage Blob Azure.  Toutefois, les performances dépendent de divers facteurs, tels que la bande passante de l'éditeur de logiciels et la taille de la base de données. Si vous envisagez de sauvegarder des bases de données ou groupes de fichiers volumineux à partir d'une base de données SQL Server locale, nous vous recommandons de commencer par tester le débit. Les [contrats SLA de stockage Azure](https://go.microsoft.com/fwlink/?LinkId=271619) ont des durées de traitement maximales pour les objets BLOB que vous pouvez prendre en compte.  
  
-   L'utilisation de l'option `WITH COMPRESSION`, comme recommandé dans la section **Gestion de la sauvegarde**, est très importante lors de la sauvegarde de fichiers volumineux.  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a>Dépannage des problèmes de sauvegarde vers une URL ou de restauration depuis une URL  
 Voici quelques méthodes rapides qui vous aideront à résoudre les erreurs survenant lors de la sauvegarde ou de la restauration vers/depuis le service de stockage Blob Azure.  
  
 Pour éviter les erreurs dues à des options ou des limitations non prises en charge, consultez la liste des limitations et la prise en charge des commandes BACKUP et Restore dans l’article [SQL Server la sauvegarde et la restauration avec le service de stockage d’objets BLOB Azure](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) .  
  
 **Erreurs d’authentification :**  
  
-   WITH CREDENTIAL est une nouvelle option requise pour la sauvegarde ou la restauration à partir du service de stockage d’objets BLOB Azure. Les défaillances liées aux informations d'identification peuvent être les suivantes :  
  
     Les informations d'identification spécifiées dans la commande `BACKUP` ou `RESTORE` n'existent pas. Pour éviter ce problème, vous pouvez inclure des instructions T-SQL afin de créer les informations d'identification si elles n'existent pas dans l'instruction de sauvegarde. Voici un exemple que vous pouvez utiliser :  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   Les informations d'identification existent, mais le compte de connexion utilisé pour exécuter la commande de sauvegarde ne dispose pas des autorisations appropriées pour accéder aux informations d'identification. Utilisez un compte de connexion dans le rôle **db_backupoperator** avec des autorisations **Modifier des informations d’identification** .  
  
-   Vérifiez le nom du compte de stockage et la valeur des clés. Les informations stockées dans les informations d’identification doivent correspondre aux valeurs de propriétés du compte de stockage Azure utilisé lors des opérations de sauvegarde et de restauration.  
  
 **Erreurs/échecs de sauvegarde :**  
  
-   Les sauvegardes parallèles dans un même objet blob provoquent l'échec d'une des sauvegardes avec l'erreur **Échec de l’initialisation** .  
  
-   Utilisez les journaux d'erreurs suivants pour vous aider à résoudre les erreurs de sauvegarde :  
  
    -   Définissez l'indicateur de trace 3051 pour activer la journalisation dans un journal des erreurs spécifique au format suivant :  
  
         BackupToUrl\<nom_instance>-\<nom_bd>-action-\<PID>.log Où \<action> a l’une des valeurs suivantes :  
  
        -   `DB`  
  
        -   `FILELISTONLY`  
  
        -   `LABELONLY`  
  
        -   `HEADERONLY`  
  
        -   `VERIFYONLY`  
  
    -   Vous pouvez également trouver des informations en examinant le journal des événements Windows, sous les journaux des applications portant le nom « SQLBackupToUrl ».  
  
-   En cas de restauration d'une sauvegarde compressée, vous pouvez rencontrer l'erreur suivante :  
  
    -   **SqlException 3284 s’est produit. Gravité : 16 État : 5**  
        **La marque de message surhttps://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bakl’appareil' 'n’est pas alignée. Réexécutez l’instruction RESTORE avec la même taille de bloc que celle utilisée pour créer le jeu de sauvegarde : ' 65536 'ressemble à une valeur possible.**  
  
         Pour résoudre cette erreur, réexécutez l'instruction `BACKUP` en spécifiant `BLOCKSIZE = 65536`.  
  
-   Erreur lors de la sauvegarde en raison d'objets blob avec un bail actif : l'activité de sauvegarde en échec peut générer des objets blob avec des baux actifs.  
  
     Si une instruction de sauvegarde est retentée, l'opération de sauvegarde échoue avec une erreur semblable à celle qui suit :  
  
     **La sauvegarde vers l’URL a reçu une exception du point de terminaison distant. Message d’exception : le serveur distant a retourné une erreur : (412) il existe actuellement un bail sur l’objet BLOB et aucun ID de bail n’a été spécifié dans la demande**.  
  
     Si une instruction de restauration est tentée sur un fichier de sauvegarde d'objet blob dont le bail est actif, l'opération de restauration échoue avec une erreur semblable à celle qui suit :  
  
     **Message d’exception : le serveur distant a retourné une erreur : (409) conflit..**  
  
     Lorsqu'une telle erreur se produit, les fichiers d'objets blob doivent être supprimés. Pour plus d'informations sur ce scénario et la résolution du problème, consultez [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)  
  
## <a name="proxy-errors"></a>Erreurs de proxy  
 Si vous utilisez des serveurs proxy pour l'accès à Internet, les erreurs suivantes peuvent survenir :  
  
 **Limitation de la connexion par les serveurs proxy :**  
  
 Les serveurs proxy peuvent avoir des paramètres qui limitent le nombre de connexions par minute. Le processus de sauvegarde vers l'URL est un processus multithread et, par conséquent, il peut dépasser cette limite. Si cela se produit, le serveur proxy supprime la connexion. Pour résoudre ce problème, modifiez les paramètres du proxy afin que SQL Server n'utilise pas le proxy.   Voici quelques exemples des types d'erreur ou des messages qui peuvent s'afficher dans le journal des erreurs :  
  
-   Échec de l'http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bakécriture sur «» : la sauvegarde vers l’URL a reçu une exception du point de terminaison distant. Message d'exception : impossible de lire les données de la connexion de transport : la connexion a été fermée.  
  
-   Une erreur d’E/S non récupérable s’est produite sur le fichier « http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak: ». L’erreur n’a pas pu être collectée à partir du point de terminaison distant.  
  
     Msg 3013, Niveau 16, État 1, Ligne 2  
  
     La sauvegarde de base de données s'est terminée anormalement.  
  
-   BackupIoRequest :: ReportIoError : échec d’écriture sur l’unitéhttp://storageaccount.blob.core.windows.net/container/BackupAzurefile.bakde sauvegarde' '. Erreur de système d'exploitation. La sauvegarde vers l'URL a reçu une exception du point de terminaison distant. Message d'exception : impossible de lire les données de la connexion de transport : la connexion a été fermée.  
  
 Si vous activez la journalisation détaillée à l'aide de l'indicateur de trace 3051, vous pouvez également voir le message suivant dans les journaux :  
  
 Code d'état HTTP 502, message d'état HTTP, erreur de proxy (le nombre de requêtes HTTP par minute a dépassé la limite configurée. Contactez votre administrateur ISA Server.  )  
  
 **Paramètres de proxy par défaut non récupérés :**  
  
 Parfois, les paramètres par défaut ne sont pas sélectionnés et provoquent des erreurs d’authentification du proxy telles que celle illustrée ci-dessous :*une erreur d'http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:e/s non récupérable s’est produite dans le fichier «». la sauvegarde vers l’URL a reçu une exception du point de terminaison distant. Message d’exception : le serveur distant a retourné une erreur : (407)* **authentification proxy requise**.  
  
 Pour résoudre ce problème, créez un fichier de configuration qui permet au processus de sauvegarde vers l'URL d'utiliser les paramètres du proxy par défaut à l'aide des étapes suivantes :  
  
1.  Créez un fichier de configuration nommé BackuptoURL.exe.config avec le code xml suivant :  
  
    ```  
    <?xml version ="1.0"?>  
    <configuration>   
                    <system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    </system.net>  
    </configuration>  
  
    ```  
  
2.  Placez le fichier de configuration dans le dossier Binn de l'instance de SQL Server. Par exemple, si mon SQL Server est installé sur le lecteur C de l’ordinateur, placez le fichier de configuration ici : *C:\Program Files\Microsoft SQL\< Server\MSSQL12. Nom_instance> \MSSQL\Binn*.  
  
## <a name="troubleshooting-sql-server-managed-backup-to-azure"></a>Résolution des problèmes SQL Server la gestion de sauvegarde sur Azure  
 Étant donné que la sauvegarde managée de SQL Server est générée par dessus la sauvegarde vers l'URL, les conseils de dépannage décrits dans les premières sections s'appliquent aux bases de données ou aux instances qui utilisent la sauvegarde managée de SQL Server.  Pour plus d’informations sur la résolution des problèmes SQL Server la gestion de la sauvegarde sur Azure, voir [troubleshooting SQL Server Managed Backup to Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Restauration à partir des sauvegardes stockées dans Azure](restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
