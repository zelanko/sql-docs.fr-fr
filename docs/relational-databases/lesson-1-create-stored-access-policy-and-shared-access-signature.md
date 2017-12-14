---
title: "Leçon 1 : Créer une stratégie d’accès stockée et une signature d’accès partagé | Microsoft Docs"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
caps.latest.revision: "22"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b9b0560be6980577dcedbe147ff856a18b032f03
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-1-create-stored-access-policy-and-shared-access-signature"></a>Leçon 1 : Créer une stratégie d’accès stockée et une signature d’accès partagé
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Dans cette leçon, vous allez utiliser un script [Azure PowerShell](https://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/) pour créer une signature d’accès partagé sur un conteneur d’objets blob Azure à l’aide d’une stratégie d’accès stockée.  
  
> [!NOTE]  
> Ce script est écrit à l’aide d’Azure PowerShell 5.0.10586.  
  
Une signature d’accès partagé est un URI qui octroie des droits d’accès restreints aux conteneurs, aux objets blob, aux files d’attente ou aux tables. Une stratégie d’accès stockée fournit un niveau de contrôle supplémentaire sur des signatures d’accès partagé côté serveur, notamment en matière de révocation, d’expiration ou d’extension d’un accès. Si vous utilisez cette nouvelle amélioration, vous devez créer une stratégie sur un conteneur avec au minimum des droits en lecture, en écriture et en création de liste.  
  
Vous pouvez créer une stratégie d’accès stockée et une signature d’accès partagé à l’aide d’Azure PowerShell, du SDK Stockage Azure, de l’API REST Azure ou d’un utilitaire tiers. Ce didacticiel montre comment utiliser un script Azure PowerShell pour effectuer cette tâche. Le script utilise le modèle de déploiement Resource Manager et crée les ressources suivantes :  
  
-   Groupe de ressources  
  
-   Compte de stockage  
  
-   Conteneur d’objets blob Azure  
  
-   Stratégie SAP  
  
Ce script commence par déclarer plusieurs variables pour spécifier les noms des ressources ci-dessus et les noms des valeurs d’entrée requises suivantes :  
  
-   Un nom de préfixe utilisé pour nommer les autres objets de ressource  
  
-   Nom d’abonnement  
  
-   Emplacement du centre de données  
  
> [!NOTE]  
> Ce script vous permet d’utiliser des ressources de modèle de déploiement ARM ou classiques existantes.  
  
Le script se termine par la génération de l’instruction CREATE CREDENTIAL appropriée, que vous utiliserez dans la [Leçon 2 : Créer des informations d’identification SQL Server à l’aide d’une signature d’accès partagé](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md). Cette instruction est automatiquement copiée dans le Presse-papiers et apparaît dans la console.  
  
Pour créer une stratégie sur le conteneur et générer une clé de signature d’accès partagé (SAP), procédez comme suit :  
  
1.  Ouvrez Windows PowerShell ou Windows PowerShell ISE (voir plus haut la version requise).  
  
2.  Modifiez, puis exécutez le script suivant.  
  
    ```  
    \<#   
    This script uses the Azure Resource model and creates a new ARM storage account.  
    Modify this script to use an existing ARM or classic storage account   
    using the instructions in comments within this script  
    #>  
    # Define global variables for the script  
    $prefixName = '<a prefix name>'  # used as the prefix for the name for various objects  
    $subscriptionName='<your subscription name>'   # the name  of subscription name you will use  
    $locationName = '<a data center location>'  # the data center region you will use  
    $storageAccountName= $prefixName + 'storage' # the storage account name you will create or use  
    $containerName= $prefixName + 'container'  # the storage container name to which you will attach the SAS policy with its SAS token  
    $policyName = $prefixName + 'policy' # the name of the SAS policy  
  
    \<#   
    Using Azure Resource Manager deployment model  
    Comment out this entire section and use the classic storage account name to use an existing classic storage account  
    #>  
  
    # Set a variable for the name of the resource group you will create or use  
    $resourceGroupName=$prefixName + 'rg'   
  
    # adds an authenticated Azure account for use in the session   
    Login-AzureRmAccount    
  
    # set the tenant, subscription and environment for use in the rest of   
    Set-AzureRmContext -SubscriptionName $subscriptionName   
  
    # create a new resource group - comment out this line to use an existing resource group  
    New-AzureRmResourceGroup -Name $resourceGroupName -Location $locationName   
  
    # Create a new ARM storage account - comment out this line to use an existing ARM storage account  
    New-AzureRmStorageAccount -Name $storageAccountName -ResourceGroupName $resourceGroupName -Type Standard_RAGRS -Location $locationName   
  
    # Get the access keys for the ARM storage account  
    $accountKeys = Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $storageAccountName  
  
    # Create a new storage account context using an ARM storage account  
    $storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $accountKeys[0].Value 
  
    \<#  
    Using the Classic deployment model  
    Use the following four lines to use an existing classic storage account  
    #>  
    #Classic storage account name  
    #Add-AzureAccount  
    #Select-AzureSubscription -SubscriptionName $subscriptionName #provide an existing classic storage account  
    #$accountKeys = Get-AzureStorageKey -StorageAccountName $storageAccountName  
    #$storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $accountKeys.Primary  
  
    # The remainder of this script works with either the ARM or classic sections of code above  
  
    # Creates a new container in blob storage  
    $container = New-AzureStorageContainer -Context $storageContext -Name $containerName  
    $cbc = $container.CloudBlobContainer  
  
    # Sets up a Stored Access Policy and a Shared Access Signature for the new container  
    $permissions = $cbc.GetPermissions();  
    $policyName = $policyName  
    $policy = new-object 'Microsoft.WindowsAzure.Storage.Blob.SharedAccessBlobPolicy'  
    $policy.SharedAccessStartTime = $(Get-Date).ToUniversalTime().AddMinutes(-5)  
    $policy.SharedAccessExpiryTime = $(Get-Date).ToUniversalTime().AddYears(10)  
    $policy.Permissions = "Read,Write,List,Delete"  
    $permissions.SharedAccessPolicies.Add($policyName, $policy)  
    $cbc.SetPermissions($permissions);  
  
    # Gets the Shared Access Signature for the policy  
    $policy = new-object 'Microsoft.WindowsAzure.Storage.Blob.SharedAccessBlobPolicy'  
    $sas = $cbc.GetSharedAccessSignature($policy, $policyName)  
    Write-Host 'Shared Access Signature= '$($sas.Substring(1))''  
  
    # Outputs the Transact SQL to the clipboard and to the screen to create the credential using the Shared Access Signature  
    Write-Host 'Credential T-SQL'  
    $tSql = "CREATE CREDENTIAL [{0}] WITH IDENTITY='Shared Access Signature', SECRET='{1}'" -f $cbc.Uri,$sas.Substring(1)   
    $tSql | clip  
    Write-Host $tSql  
  
    ```  
  
3.  Une fois le script terminé, l’instruction CREATE CREDENTIAL se trouve dans le Presse-papiers pour une utilisation dans la leçon suivante.  
  
**Leçon suivante :**  
  
[Leçon 2 : Créer des informations d’identification SQL Server à l’aide d’une signature d’accès partagé](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="see-also"></a>Voir aussi  
[Signatures d’accès partagé, partie 1 : présentation du modèle SAP](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/)  
[Create Container](https://msdn.microsoft.com/library/azure/dd179468.aspx)  
[Set Container ACL](https://msdn.microsoft.com/library/azure/dd179391.aspx)  
[Get Container ACL](https://msdn.microsoft.com/library/azure/dd179469.aspx)  
  
  
  

