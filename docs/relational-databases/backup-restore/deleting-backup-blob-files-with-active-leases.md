---
title: Suppression de fichiers de sauvegarde d’objets blob avec des baux actifs | Microsoft Docs
ms.custom: ''
ms.date: 08/17/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cdc58884e65fb243bbb75f257e19ccef3faa2b9f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "72908936"
---
# <a name="delete-backup-blob-files-with-active-leases"></a>Supprimer des fichiers blob de sauvegarde avec des baux actifs

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

En cas de sauvegarde vers ou de restauration à partir du stockage Microsoft Azure, SQL Server acquiert un bail infini pour verrouiller l’accès exclusif à l’objet blob. Lorsque le processus de sauvegarde ou de restauration est terminé, le bail est libéré. Si une sauvegarde ou une restauration échoue, le processus de sauvegarde tente de nettoyer tout objet blob non valide. Toutefois, si la sauvegarde échoue en raison d'un problème de connectivité du réseau prolongé, le processus de sauvegarde peut ne pas être à nouveau en mesure d'accéder à l'objet blob et celui-ci peut rester orphelin. Par conséquent, l’objet blob ne peut pas être écrit ou supprimé tant que le bail n’a pas été libéré. Cette rubrique explique comment libérer (résilier) le bail et supprimer l’objet blob.
  
Pour plus d’informations sur les types de baux, consultez cet [article](https://go.microsoft.com/fwlink/?LinkId=275664).  
  
Si l’opération de sauvegarde échoue, elle peut générer un fichier de sauvegarde non valide. Le fichier de sauvegarde d'objet blob peut également avoir un bail actif, ce qui empêche sa suppression ou son remplacement. Pour supprimer ou remplacer ces objets blob, le bail doit d’abord être libéré (résilié). En cas d’échec de sauvegarde, nous vous recommandons de nettoyer les baux et de supprimer les objets blob. Vous pouvez également périodiquement nettoyer les baux et supprimer les objets blob dans le cadre de vos tâches de gestion du stockage.  
  
En cas d’échec d’une restauration, les restaurations suivantes ne sont pas bloquées. Par conséquent, le bail actif ne pose pas problème. La résiliation du bail est uniquement nécessaire lorsque vous devez remplacer ou supprimer l'objet blob.  
  
## <a name="manage-orphaned-blobs"></a>Gérer les objets blob orphelins

Les étapes suivantes décrivent la procédure de nettoyage après l'échec d'une activité de sauvegarde ou de restauration. Vous pouvez effectuer toutes les étapes à l’aide de scripts PowerShell. La section suivante contient un exemple de script PowerShell :  
  
1. **Identifier des objets blob avec baux :** si vous avez un script ou un processus qui exécute les processus de sauvegarde, vous pouvez capturer l’erreur dans le script ou le processus, et l’utiliser pour nettoyer les objets blob.  Vous pouvez également utiliser les propriétés LeaseStats et LeastState pour identifier les objets blob associés à des baux. Une fois que vous avez identifié les objets blob, consultez la liste et vérifiez la validité du fichier de sauvegarde avant de supprimer l’objet blob.  
  
1. **Résiliation du bail :** une demande autorisée peut résilier le bail sans fournir d’ID de bail. Pour plus d’informations, consultez [cet article](https://go.microsoft.com/fwlink/?LinkID=275664) .  
  
    > [!TIP]  
    > SQL Server génère un ID de bail pour établir un accès exclusif pendant l'opération de restauration. L'ID de bail de la restauration est BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2.  
  
1. **Supprimer l’objet blob :** Pour supprimer un objet blob avec un bail actif, vous devez d’abord résilier le bail.  

###  <a name="powershell-script-example"></a><a name="Code_Example"></a> Exemple de script PowerShell  
  
> [!IMPORTANT]
> Si vous exécutez PowerShell 2.0, vous pouvez rencontrer des problèmes lors du chargement de l'assembly Microsoft WindowsAzure.Storage.dll. Nous vous recommandons de mettre à niveau [Powershell](https://docs.microsoft.com/powershell/) pour résoudre le problème. Vous pouvez également utiliser la solution de contournement suivante afin de créer ou modifier le fichier powershell.exe.config pour charger les assemblies .NET 2.0 et .NET 4.0 au moment de l’exécution avec les informations suivantes :  
>
> ```xml
> <?xml version="1.0"?>
>     <configuration>
>         <startup useLegacyV2RuntimeActivationPolicy="true">
>             <supportedRuntime version="v4.0.30319"/>
>             <supportedRuntime version="v2.0.50727"/>
>         </startup>
>     </configuration>  
> ```  
  
 L’exemple de script suivant identifie les objets blob avec des baux actifs, puis résilie ces baux. Il montre également comment filtrer les identificateurs de bail de la version.  
  
#### <a name="tips-on-running-this-script"></a>Conseils pour l'exécution de ce script
  
> [!WARNING]  
> Si une sauvegarde dans le service Stockage Blob Azure s’exécute en même temps que ce script, elle peut échouer, car ce script résilie le bail que la sauvegarde essaie d’acquérir au même moment. Exécutez ce script au cours d’une fenêtre de maintenance ou quand aucune sauvegarde n’est en cours d’exécution ou prévue.  
  
- Avant d’exécuter ce script, vous devez ajouter des valeurs pour le compte de stockage, la clé de stockage, le conteneur ainsi que les paramètres de nom et de chemin de l’assembly de stockage Azure. Le chemin d'accès de l'assembly de stockage est le répertoire d'installation de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le nom de fichier de l'assembly de stockage est Microsoft.WindowsAzure.Storage.dll.
  
- Si aucun objet blob n’a de bail verrouillé, vous devez voir le message suivant : `There are no blobs with locked lease status`
  
- S’il existe des objets blob avec des baux verrouillés, vous devez voir les messages suivants : `Breaking Leases`, `The lease on <URL of the Blob> is a restore lease: You will see this message only if you have a blob with a restore lease that is still active.` et `The lease on <URL of the Blob> is not a restore lease Breaking lease on <URL of the Bob>.`
  
```powershell
$storageAccount = "<myStorageAccount>"
$storageKey = "<myStorageKey>"
$blobContainer = "<myBlobContainer>"
$storageAssemblyPathName = "<myStorageAssemblyPathName>"
  
# well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
$container = $client.GetContainerReference($blobContainer)  
  
# list all the blobs  
$blobs = $container.ListBlobs($null,$true)
  
# filter blobs that are have Lease Status as "locked"
$lockedBlobs = @()  
foreach($blob in $blobs)  
{  
    $blobProperties = $blob.Properties
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
    }  
}  

if($lockedBlobs.Count -gt 0)  
{  
    Write-Host "Breaking leases..."
    foreach($blob in $lockedBlobs )
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease."  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease."  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)."  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
} else { Write-Host " There are no blobs with locked lease status." }
```  
  
## <a name="see-also"></a>Voir aussi

[Bonnes pratiques et résolution des problèmes liés à la sauvegarde SQL Server vers une URL](../../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
