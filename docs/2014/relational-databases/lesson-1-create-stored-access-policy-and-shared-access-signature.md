---
title: Leçon 2. Créer une stratégie sur le conteneur et générer une clé de Signature d’accès partagé (SAP) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7ddcef5d5e0695041742784151103c358a973d55
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124079"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a>Leçon 2. Créer une stratégie sur le conteneur et générer une clé de signature d'accès partagé
  Dans cette leçon, vous allez apprendre comment créer une stratégie sur le conteneur d'objets blob et générer une clé SAS.  
  
 Une stratégie d'accès stockée fournit un niveau de contrôle supplémentaire sur des signatures d'accès partagé côté serveur. Une signature d'accès partagé est un URI qui octroie des droits d'accès restreints aux conteneurs, aux objets blob, aux files d'attente et aux tables. Si vous utilisez cette nouvelle amélioration, vous devez créer une stratégie sur un conteneur avec des droits en lecture, en écriture et en création de liste.  
  
 Créez une stratégie et une signature d'accès partagé en utilisant une des méthodes suivantes :  
  
-   Opérations d’API REST Windows Azure : [créer un conteneur](https://msdn.microsoft.com/library/azure/dd179468.aspx), [définir des ACL de conteneur](https://msdn.microsoft.com/library/azure/dd179391.aspx), et [obtenir les ACL de conteneur](https://msdn.microsoft.com/library/azure/dd179469.aspx).  
  
-   [Méthode CloudBlobContainer.GetSharedAccessSignature](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.storageclient.cloudblobcontainer.getsharedaccesssignature.aspx) dans Windows Azure SDK.  
  
    ```  
  
       string signature = blob.GetSharedAccessSignature(new SharedAccessPolicy()   
        {   
            // Specify the expiration time for the signature.   
            SharedAccessExpiryTime = DateTime.Now.Years(1),   
            // Specify the permissions granted by the signature.    
            Permissions = SharedAccessPermissions.Write | SharedAccessPermissions.Read   
        });  
  
    ```  
  
-   Outil d’une exploration de Windows Azure tiers, tel que [Azure Storage Explorer](http://azurestorageexplorer.codeplex.com/).  
  
 **Leçon suivante :**  
  
 [Leçon 3 : Créer des informations d’identification SQL Server](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
  
