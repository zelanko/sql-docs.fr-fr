---
title: Utilisation d’assemblys personnalisés avec noms forts | Microsoft Docs
description: Découvrez comment utiliser un assembly personnalisé avec un nom fort afin d’identifier de façon unique un assembly dans le Common Language Runtime (CLR) et garantir l’intégrité binaire.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-assemblies
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bdee8daafe68742dce4c91f1dffb61f849445998
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "80216994"
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
 [Utilisation d'assemblages personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
