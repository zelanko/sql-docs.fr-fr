---
title: "Gestion de l’exécution des Packages par programme | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- packages [Integration Services], managing
- running packages [Integration Services]
ms.assetid: 0e91f4ac-6f29-40d7-8c28-9b82e4802c35
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 34f2c773e89c0162df5d13a16d27f01eb5d8f4df
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="managing-running-packages-programmatically"></a>Gestion des packages en cours d'exécution par programme
  Lors de l'utilisation de packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] par programme, il peut être utile d'identifier les packages en cours d'exécution. La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit des méthodes et des classes pour répondre à ces impératifs.  
  
 Pour plus d’informations sur la surveillance des packages, consultez [gestion des packages &#40; Service SSIS &#41; ](../../integration-services/service/package-management-ssis-service.md).  
  
 Toutes les méthodes décrites dans cette rubrique requièrent une référence à la **Microsoft.SqlServer.ManagedDTS** assembly. Après avoir ajouté la référence d’un nouveau projet, importez le <xref:Microsoft.SqlServer.Dts.Runtime> espace de noms avec un **à l’aide de** ou **importations** instruction.  
  
> [!IMPORTANT]  
>  Les méthodes de la <xref:Microsoft.SqlServer.Dts.Runtime.Application> classe pour travailler avec le magasin de packages SSIS prennent uniquement en charge «. », localhost ou le nom du serveur local. Vous ne pouvez pas utiliser « (local) ».  
  
## <a name="determining-which-packages-are-currently-running"></a>Identification des packages en cours d'exécution  
 Pour identifier les packages en cours d'exécution sur le serveur spécifié, appelez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A>. Cette méthode retourne une collection <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> d'objets <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage>.  
  
> [!NOTE]  
>  Les administrateurs peuvent afficher tous les packages en cours d'exécution sur l'ordinateur ; alors que les autres utilisateurs ne voient que les packages qu'ils ont lancés.  
  
## <a name="working-with-running-packages"></a>Utilisation de packages en cours d'exécution  
 Après avoir identifié les packages en cours d'exécution, vous pouvez extraire des informations relatives aux packages et demander l'arrêt d'un package.  
  
### <a name="getting-information-about-a-running-package"></a>Obtention d'informations sur un package en cours d'exécution  
 Pendant que vous parcourez la collection <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages>, vous pouvez utiliser les propriétés de l'objet <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> pour rechercher un package ou obtenir des informations supplémentaires sur les packages en cours d'exécution :  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionDuration%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionStartTime%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.InstanceID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageDescription%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageName%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.UserName%2A>  
  
### <a name="stopping-a-running-package"></a>Arrêt d'un package en cours d'exécution  
 Vous pouvez appeler la méthode <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> d'un objet <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> pour demander l'arrêt du package. Il peut y avoir un délai entre le moment où l'arrêt est demandé et le moment où le package s'arrête réellement.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des packages &#40; Service SSIS &#41;](../../integration-services/service/package-management-ssis-service.md)   
 [Énumération des Packages disponibles par programme](../../integration-services/run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  

