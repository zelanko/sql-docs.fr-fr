---
title: Suppression de fichiers de sauvegarde d’objets blob avec des baux actifs | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3066700945d2d6dad33f04c6bc905720daab61c3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876169"
---
# <a name="deleting-backup-blob-files-with-active-leases"></a>Suppression de fichiers de sauvegarde d'objets blob avec des baux actifs
  En cas de sauvegarde vers ou de restauration depuis le stockage Windows Azure, SQL Server acquiert un bail infini pour verrouiller l'accès exclusif à l'objet blob. Lorsque le processus de sauvegarde ou de restauration est terminé, le bail est libéré. Si une sauvegarde ou une restauration échoue, le processus de sauvegarde tente de nettoyer tout objet blob non valide. Toutefois, si la sauvegarde échoue en raison d'un problème de connectivité du réseau prolongé, le processus de sauvegarde peut ne pas être à nouveau en mesure d'accéder à l'objet blob et celui-ci peut rester orphelin. Par conséquent, l'objet blob ne peut pas être écrit ou supprimé tant que le bail n'a pas été libéré. Cette rubrique explique comment libérer le bail et supprimer l'objet blob.  
  
 Pour plus d’informations sur les types de baux, consultez cet [article](https://go.microsoft.com/fwlink/?LinkId=275664).  
  
 Si l'opération de sauvegarde échoue, elle peut générer un fichier de sauvegarde non valide.  Le fichier de sauvegarde d'objet blob peut également avoir un bail actif, ce qui empêche sa suppression ou son remplacement.  Pour pouvoir supprimer ou remplacer des objets blob de ce type, le bail doit d'abord être résilié. En cas d'échec de la sauvegarde, nous vous recommandons de nettoyer les baux et de supprimer les objets blob. Vous pouvez également définir un nettoyage périodique dans le cadre des tâches de gestion du stockage.  
  
 En cas d'échec d'une restauration, les restaurations suivantes ne sont pas bloquées. Par conséquent, le bail actif ne pose pas problème. La résiliation du bail est uniquement nécessaire lorsque vous devez remplacer ou supprimer l'objet blob.  
  
## <a name="managing-orphaned-blobs"></a>Gestion des objets blob orphelins  
 Les étapes suivantes décrivent la procédure de nettoyage après l'échec d'une activité de sauvegarde ou de restauration. Toutes les opérations peuvent être effectuées à l'aide de scripts PowerShell. Un exemple de code est fourni dans la section suivante :  
  
1.  **Identifier les objets BLOB avec baux :** si vous avez un script ou un processus qui exécute les processus de sauvegarde, vous pouvez capturer l’erreur dans le script ou le processus, et l’utiliser pour nettoyer les objets blob.   Vous pouvez également utiliser les propriétés LeaseStats et LeastState pour identifier les objets blob auxquels des baux sont associés. Une fois que vous avez identifié les objets blob, nous vous recommandons de consulter la liste et de vérifier la validité du fichier de sauvegarde avant de supprimer l'objet blob.  
  
2.  **Résiliation du bail :** une demande autorisée peut résilier le bail sans fournir d’ID de bail. Pour plus d’informations, consultez [cet article](https://go.microsoft.com/fwlink/?LinkID=275664) .  
  
    > [!TIP]  
    >  SQL Server génère un ID de bail pour établir un accès exclusif pendant l'opération de restauration. L'ID de bail de la restauration est BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2.  
  
3.  **Suppression de l’objet Blob :** Pour supprimer un objet blob dont le bail est actif, vous devez d'abord résilier le bail.  
  
###  <a name="Code_Example"></a> Exemple de script PowerShell  
 **\*\* Important \* \***  si vous exécutez PowerShell 2.0, peut avoir des difficultés pour charger l’assembly Microsoft WindowsAzure.Storage.dll. Nous vous recommandons d'effectuer une mise à niveau vers Powershell 3.0 pour résoudre le problème. Vous pouvez également utiliser la solution de contournement suivante pour PowerShell 2.0 :  
  
-   Créez ou modifiez le fichier powershell.exe.config pour charger les assemblies .NET 2.0 et .NET 4.0 au moment de l'exécution avec les informations suivantes :  
  
    ```  
    <?xml version="1.0"?>   
    <configuration>   
        <startup useLegacyV2RuntimeActivationPolicy="true">   
            <supportedRuntime version="v4.0.30319"/>   
            <supportedRuntime version="v2.0.50727"/>   
        </startup>   
    </configuration>  
  
    ```  
  
 L'exemple suivant montre comment identifier les objets blob qui ont des baux actifs, puis résilier ces derniers. Il montre également comment filtrer les identificateurs de bail de la version.  
  
 Conseils pour l'exécution de ce script  
  
> [!WARNING]  
>  Si une sauvegarde dans le service de stockage d'objets blob Windows Azure s'exécute en même temps que ce script, elle peut échouer étant donné que ce script résilie le bail que la sauvegarde essaie d'acquérir au même moment. Nous recommandons d'exécuter ce script au cours d'une fenêtre de maintenance ou lorsqu'aucune sauvegarde n'est prévue.  
  
1.  Lorsque vous exécutez ce script, vous êtes invité à fournir des valeurs pour le compte de stockage, la clé de stockage, le conteneur, le chemin d'accès du stockage Windows Azure et les paramètres de nom. Le chemin d'accès de l'assembly de stockage est le répertoire d'installation de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le nom de fichier de l'assembly de stockage est Microsoft.WindowsAzure.Storage.dll. Voici un exemple des commandes et valeurs entrées :  
  
    ```  
    cmdlet  at command pipeline position 1  
    Supply values for the following parameters:  
    storageAccount: mycloudstorageaccount  
    storageKey: 0BopKY7eEha3gBnistYk+904nf  
    blobContainer: mycontainer   
    storageAssemblyPath: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Microsoft.WindowsAzure.Storage.dll  
    ```  
  
2.  Si aucun objet blob ne dispose d'un bail verrouillé, vous devez voir le message suivant :  
  
     **Il n'existe aucun objet blob à l'état bail verrouillé**  
  
     S'il existe des objets blob avec des baux verrouillés, vous devez voir les messages suivants :  
  
     **Résiliation de baux**  
  
     **Le bail sur \<URL de l’objet blob> est un bail de restauration : vous verrez ce message seulement si vous avez un objet blob avec un bail de restauration toujours actif.**  
  
     **Le bail sur \<URL de l’objet blob> n’est pas un bail de restauration. Résiliation du bail sur \<URL de l’objet blob.**  
  
```  
param(  
       [Parameter(Mandatory=$true)]  
       [string]$storageAccount,  
       [Parameter(Mandatory=$true)]  
       [string]$storageKey,  
       [Parameter(Mandatory=$true)]  
       [string]$blobContainer,  
       [Parameter(Mandatory=$true)]  
       [string]$storageAssemblyPath  
)  
  
# Well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# Load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
  
$container = $client.GetContainerReference($blobContainer)  
  
#list all the blobs  
$allBlobs = $container.ListBlobs()   
  
$lockedBlobs = @()  
# filter blobs that are have Lease Status as "locked"  
foreach($blob in $allBlobs)  
{  
    $blobProperties = $blob.Properties   
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
  
    }  
}  
  
if ($lockedBlobs.Count -eq 0)  
    {   
        Write-Host " There are no blobs with locked lease status"  
    }  
if($lockedBlobs.Count -gt 0)  
{  
    write-host "Breaking leases"  
    foreach($blob in $lockedBlobs )   
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease"  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease"  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)"  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Meilleures pratiques et dépannage de sauvegarde SQL Server vers une URL](sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
