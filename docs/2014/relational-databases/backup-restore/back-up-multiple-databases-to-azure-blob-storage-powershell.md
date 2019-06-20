---
title: Utiliser PowerShell pour sauvegarder plusieurs bases de données au Service de stockage d’objets Blob Azure Windows | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: f7008339-e69d-4e20-9265-d649da670460
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 03a747825c20b1183977b6c5b8e7f46ef2aa034f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62922573"
---
# <a name="use-powershell-to-backup-multiple-databases-to-windows-azure-blob-storage-service"></a>Utiliser PowerShell pour sauvegarder plusieurs bases de données dans le service de Stockage Blob Windows Azure
  Cette rubrique fournit des exemples de script pouvant être utilisés pour automatiser les sauvegardes dans le service Stockage Blob Microsoft Azure à l'aide d'applets de commande PowerShell.  
  
## <a name="overview-of-powershell-cmdlets-for-backup-and-restore"></a>Présentation des applets de commande PowerShell pour la sauvegarde et la restauration  
 `Backup-SqlDatabase` et `Restore-SqlDatabase` sont les deux principales applets de commande disponibles pour effectuer des opérations de sauvegarde et de restauration. En outre, d'autres applets de commande peuvent être nécessaires pour automatiser les sauvegardes dans le service de stockage d'objets blob Windows Azure, comme l'ensemble d'applets de commande **SqlCredential** . Voici une liste des applets de commande PowerShell disponibles dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , qui sont utilisées dans les opérations de sauvegarde et de restauration :  
  
 Backup-SqlDatabase  
 Cette applet de commande permet de créer une sauvegarde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Restore-SqlDatabase  
 Utilisée pour restaurer une base de données.  
  
 New-SqlCredential  
 Cette applet de commande permet de créer des informations d'identification SQL à utiliser pour la sauvegarde SQL Server dans le stockage Windows Azure. Pour plus d'informations sur les informations d'identification et leur utilisation dans Sauvegarde et restauration SQL Server, consultez [Sauvegarde et restauration SQL Server avec le service de stockage d'objets blob Windows Azure](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 Get-SqlCredential  
 Cette applet de commande est utilisée pour récupérer l'objet contenant les informations d'identification et ses propriétés.  
  
 Remove-SqlCredential  
 Supprime un objet contenant les informations d'identification SQL  
  
 Set-SqlCredential  
 Cette applet de commande est utilisée pour modifier ou définir les propriétés de l'objet contenant les informations d'identification SQL.  
  
> [!TIP]  
>  Les applets de commande Credential sont utilisées dans les scénarios de sauvegarde et de restauration dans le stockage d'objets blob Windows Azure.  
  
### <a name="powershell-for-multi-database-multi-instance-backup-operations"></a>PowerShell pour des opérations de sauvegarde de plusieurs bases de données, sur plusieurs instances  
 Les sections suivantes contiennent des scripts pour différentes opérations, notamment créer des informations d'identification SQL sur plusieurs instances de SQL Server, sauvegarder toutes les bases de données utilisateur dans une instance de SQL Server, etc. Utilisez ces scripts pour automatiser ou planifier des opérations de sauvegarde en fonction des spécifications de votre environnement. Les scripts fournis ici sont des exemples, et peuvent être modifiés ou étendus pour votre environnement.  
  
 Voici quelques observations concernant les exemples de script :  
  
1.  **Parcours des chemins SQL Server PowerShell :** Windows PowerShell implémente des applets de commande pour parcourir la structure de chemin d'accès qui représente la hiérarchie des objets pris en charge par un fournisseur PowerShell. Une fois que vous avez accédé à un nœud dans le chemin d'accès, vous pouvez utiliser d'autres applets de commande pour exécuter des opérations de base sur l'objet actif.  
  
2.  `Get-ChildItem` applet de commande : Les informations retournées par la `Get-ChildItem` dépend de l’emplacement dans un chemin d’accès PowerShell SQL Server. Par exemple, si l'emplacement est au niveau de l'ordinateur, cette applet de commande retourne toutes les instances du moteur de base de données SQL Server installées sur l'ordinateur. Si l'emplacement est au niveau de l'objet, tel que des bases de données, cette applet de commande retourne une liste d'objets de base de données.  Par défaut, l'applet de commande `Get-ChildItem` ne retourne pas d'objets système.  Pour afficher les objets système, utilisez le paramètre -Force.  
  
     Pour plus d’informations, consultez [Navigate SQL Server PowerShell Paths](../../powershell/navigate-sql-server-powershell-paths.md).  
  
3.  Bien que chaque exemple de code puisse être exécuté indépendamment en modifiant les valeurs de variable, vous devez créer un compte de stockage Windows Azure et des informations d'identification SQL pour toutes les opérations de sauvegarde et de restauration dans le service de stockage d'objets blob Windows Azure.  
  
### <a name="create-a-sql-credential-on-all-the-instances-of-sql-server"></a>Créer des informations d'identification SQL sur toutes les instances de SQL Server  
 Il y a deux exemples de script, et les deux créent les informations d’identification SQL « mybackupToURL » sur toutes les instances de SQL Server sur un ordinateur. Le premier exemple crée les informations d'identification et n'intercepte pas les exceptions.  Par exemple, s'il existe déjà des informations d'identification avec le même nom sur une des instances de l'ordinateur, le script échoue. Le deuxième exemple intercepte les erreurs et permet au script de continuer.  
  
```  
  
import-module sqlps  
  
# create variables  
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = convertto-securestring $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-childitem  
#pipe the instances to new-sqlcredentail cmdlet to create SQL credential  
$instances | new-sqlcredential -Name $credentialName  -Identity $storageAccount -Secret $secureString  
```  
  
```  
  
import-module sqlps  
  
# set the parameter values  
  
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = convertto-securestring $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-childitem  
#loop through instances and create a SQL credential, output any errors  
foreach ($instance in $instances)  
{  
    Try  
{  
     new-sqlcredential -Name $credentialName -path "SQLServer:\SQL\$($instance.name)" -Identity $storageAccount -Secret $secureString -ea Stop   
}  
Catch [Exception]  
    {  
  
            write-host "instance - $($instance.name): "$_.Exception.Message  
  
    }  
  
 }  
  
```  
  
### <a name="remove-a-sql-credential-from-all-the-instances-of-sql-server"></a>Supprimer des informations d'identification SQL de toutes les instances de SQL Server  
 Ce script permet de supprimer des informations d'identification spécifiques de toutes les instances de SQL Server installées sur l'ordinateur. Si l'objet Credential n'existe pas sur une instance spécifique, un message d'erreur s'affiche, et le script continue jusqu'à ce que toutes les instances aient été vérifiées.  
  
```  
  
import-module sqlps  
  
cd SQLServer:\SQL\COMPUTERNAME  
$credentialName = "mybackuptoURL"  
  
$instances = Get-childitem  
  
foreach ($instance in $instances)  
   {   
    try  
        {  
            $path = "SQLServer:\SQL\$($instance.name)\credentials\$credentialName"   
            Remove-sqlCredential -path $path -ea stop   
         }  
         catch [Exception]  
         {  
            write-host $_.Exception.Message  
  
        }  
  
    }  
```  
  
### <a name="full-database-backup-for-all-databases-including-system-databases"></a>Sauvegarde complète de base de données pour toutes les bases de données (y compris les bases de données système)  
 Le script suivant crée des sauvegardes de toutes les bases de données sur l'ordinateur. Cela inclut les bases de données utilisateur et la base de données système **msdb** . Le script exclut les bases de données système **tempdb** et **model** .  
  
```  
  
import-module sqlps  
# set the parameter values  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level  
  
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-childitem   
# loop through each instances and backup up all the  databases -filter out tempdb and model databases  
  
 foreach ($instance in $instances)  
 {  
   $path = "sqlserver:\sql\$($instance.name)\databases"  
   $alldatabases = get-childitem -Force -path $path |Where-object {$_.name -ne "tempdb" -and $_.name -ne "model"}   
  
   $alldatabases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On -script   
 }  
  
```  
  
### <a name="full-database-backup-for-all-user-databases"></a>Sauvegarde complète de base de données pour toutes les bases de données utilisateur  
 Le script suivant peut être utilisé pour la sauvegarde de toutes les bases de données utilisateur sur toutes les instances de SQL Server sur l'ordinateur.  
  
```  
  
import-module sqlps   
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level  
  
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-childitem   
# loop through each instances and backup up all the user databases  
 foreach ($instance in $instances)  
 {  
    $databases = dir "sqlserver:\sql\$($instance.name)\databases"  
   $databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On   
 }  
```  
  
### <a name="full-database-backup-for-master-and-msdb-system-databases-on-all-the-instances-of-sql-server"></a>Sauvegarde complète des bases de données MASTER et MSDB (bases de données système) sur toutes les instances de SQL Server  
 Le script suivant peut être utilisé pour la sauvegarde des bases de données **master** et **msdb** sur toutes les instances de SQL Server installées sur l’ordinateur.  
  
```  
  
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackupToUrl"  
$sysDbs = "master", "msdb"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
$instances = Get-childitem   
foreach ($instance in $instances)  
 {  
      foreach ($s in $sysdbs)  
     {  
Backup-SqlDatabase -Database $s -path "sqlserver:\sql\$($instance.name)" -BackupContainer  $backupUrlContainer -SqlCredential $credentialName -Compression On   
}    
 }  
  
```  
  
### <a name="full-database-backup-for-all-user-databases-on-an-instance-of-sql-server"></a>Sauvegarde complète de toutes les bases de données utilisateur sur une instance de SQL Server  
 Le script suivant est utilisé pour sauvegarder uniquement les bases de données utilisateur disponibles sur une instance nommée de SQL Server. Ce script peut être utilisé pour l'instance par défaut sur l'ordinateur en modifiant la valeur du paramètre $srvPath.  
  
```  
  
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME"  # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
  
#retrieves the database objects for a specific instance  
$databases = dir $srvPath\databases  
  
#backup all the user databases  
$databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
```  
  
### <a name="full-database-backup-for-only-system-databases-master-and-msdb-on-an-instance-of-sql-server"></a>Sauvegarde complète des bases de données système (MASTER et MSDB) sur une instance de SQL Server  
 Le script complet peut être utilisé pour la sauvegarde des bases de données **master** et **msdb** sur une instance nommée de SQL Server. Ce script peut être utilisé pour l'instance par défaut sur l'ordinateur en modifiant la valeur du paramètre $srvPath.  
  
```  
  
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME" # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#navigate to instance level  
cd $srvPath  
  
$sysDbs = "master", "msdb"  
foreach ($s in $sysDbs)   
{  
Backup-SqlDatabase -Database $s -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Service de stockage d'objets blob Windows Azure](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
 [Bonnes pratiques en matière de sauvegarde SQL Server vers une URL et résolution des problèmes associés](sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
