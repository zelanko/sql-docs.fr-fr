---
title: "Enregistrement d’un Package par programme | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: building-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: f6b99377f6eaf720b9511b560e5cf563ede2b869
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="saving-a-package-programmatically"></a>Enregistrement d'un package par programme
  Après avoir généré un package par programme, ou modifié un package existant, vous souhaitez généralement enregistrer vos modifications.  
  
 Toutes les méthodes de cette rubrique qui permettent d'enregistrer des packages requièrent une référence à l'assembly **Microsoft.SqlServer.ManagedDTS** . Après avoir ajouté la référence d’un nouveau projet, importez le <xref:Microsoft.SqlServer.Dts.Runtime> espace de noms avec un **à l’aide de** ou **importations** instruction.  
  
## <a name="saving-a-package-programmatically"></a>Enregistrement d'un package par programme  
 Pour enregistrer un package par programme, appelez l’une des méthodes suivantes de la [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> classe :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Fichier|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> ou<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  Les méthodes de la classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> qui permettent d'utiliser le magasin de packages SSIS prennent uniquement en charge « . » ou le nom du serveur local. Vous ne pouvez pas utiliser « (local) » ou « localhost ».  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer des packages](../../integration-services/save-packages.md)  
  
  

