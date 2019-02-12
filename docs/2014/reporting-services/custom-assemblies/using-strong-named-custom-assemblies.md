---
title: Utilisation d’assemblys personnalisés avec noms forts | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: e4a12c97b476a0231e230dda16eaa667fcf0a642
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020741"
---
# <a name="using-strong-named-custom-assemblies"></a>Utilisation d'assemblys personnalisés avec noms forts
  Un nom fort identifie un assembly et comprend le nom de l'assembly, le numéro de version en quatre parties, les informations de culture (si fournies), une clé publique et une signature numérique stockée dans le manifeste de l'assembly. Un nom fort identifie de façon unique un assembly dans le Common Language Runtime (CLR) et garantit l'intégrité binaire.  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a>Utilisation de l'attribut AllowPartiallyTrustedCallersAttribute  
 Pour utiliser des assemblys avec noms forts avec des rapports, vous devez autoriser votre assembly avec nom fort à être appelé par du code d’un niveau de confiance partiel à l’aide de l’attribut **AllowPartiallyTrustedCallers** de l’assembly. Vous pouvez utiliser l’attribut **AllowPartiallyTrustedCallersAttribute** pour autoriser des assemblys avec noms forts à être appelés par le Concepteur de rapports ou le serveur de rapports dans des expressions de rapport. Pour permettre à du code d'un niveau de confiance partiel d'appeler des assemblys avec noms forts, ajoutez l'attribut de niveau assembly suivant au fichier d'attribut de votre assembly.  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 L’attribut **AllowPartiallyTrustedCallersAttribute** est uniquement efficace quand il est appliqué au niveau de l’assembly par un assembly avec nom fort. Pour plus d’informations sur l’application d’attributs au niveau de l’assembly, consultez « Application des attributs » dans la documentation du SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
> [!CAUTION]  
>  Quand l’attribut **AllowPartiallyTrustedCallersAttribute** est présent, les vérifications de sécurité **FullTrustLinkDemand** par défaut sont empêchées, ce qui rend l’assembly appelable à partir de tout autre assembly d’un niveau de confiance partiel. Toutes les vérifications de sécurité, notamment les attributs de sécurité déclaratifs au niveau de la classe ou de la méthode, doivent être déclarées explicitement.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'assemblages personnalisés avec des rapports](using-custom-assemblies-with-reports.md)  
  
  
