---
title: "La gestion par programmation des rôles de Package (Service SSIS) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: run-manage-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 7a7fb000389756caf0c2f2ea00cd0b80e75557d8
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="managing-package-roles-programmatically-ssis-service"></a>Gestion par programmation des rôles de package (service SSIS)
  Lorsque vous utilisez des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] par programme, vous pouvez identifier les rôles disponibles pouvant être appliqués aux packages, ou identifier ou définir les rôles appliqués à un package spécifique. La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit différentes méthodes pour répondre à ces impératifs.  
  
 Les rôles s’appliquent uniquement aux packages stockés dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** base de données. Pour plus d’informations sur les rôles de package, consultez [rôles Integration Services &#40; Service SSIS &#41; ](../../integration-services/security/integration-services-roles-ssis-service.md).  
  
 Toutes les méthodes décrites dans cette rubrique requièrent une référence à la **Microsoft.SqlServer.ManagedDTS** assembly. Après avoir ajouté la référence d’un nouveau projet, importez le <xref:Microsoft.SqlServer.Dts.Runtime> espace de noms en utilisant un **à l’aide de** ou **importations** instruction.  
  
> [!IMPORTANT]  
>  Les méthodes de la <xref:Microsoft.SqlServer.Dts.Runtime.Application> classe pour travailler avec le magasin de packages SSIS prennent uniquement en charge «. », localhost ou le nom du serveur local. Vous ne pouvez pas utiliser « (local) ».  
  
## <a name="determining-which-roles-are-available"></a>Identification des rôles disponibles  
 Pour identifier les rôles disponibles pour les packages stockés sur un serveur particulier, appelez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> de la classe <xref:Microsoft.SqlServer.Dts.Runtime.Application>.  
  
## <a name="determining-which-roles-are-assigned"></a>Identification des rôles assignés  
 Pour identifier les rôles déjà attribués à un package particulier, appelez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A>. Pour attribuer des rôles à un package, appelez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Les Services d’intégration rôles &#40; Service SSIS &#41;](../../integration-services/security/integration-services-roles-ssis-service.md)  
  
  

