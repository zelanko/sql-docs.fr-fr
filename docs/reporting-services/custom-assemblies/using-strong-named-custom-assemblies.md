---
title: "À l’aide d’un nom fort des assemblys personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: cf8ee5462bd75ab82ea4296a5b71136cb2eb9ee9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="using-strong-named-custom-assemblies"></a>Utilisation d'assemblys personnalisés avec noms forts
  Un nom fort identifie un assembly et comprend le nom de l'assembly, le numéro de version en quatre parties, les informations de culture (si fournies), une clé publique et une signature numérique stockée dans le manifeste de l'assembly. Un nom fort identifie de façon unique un assembly dans le Common Language Runtime (CLR) et garantit l'intégrité binaire.  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a>Utilisation de l'attribut AllowPartiallyTrustedCallersAttribute  
 Pour utiliser des assemblys avec nom fort avec des rapports, vous devez autoriser votre assembly avec nom fort à être appelé par du code partiellement fiable à l’aide de l’assembly **AllowPartiallyTrustedCallers** attribut. Vous pouvez utiliser **AllowPartiallyTrustedCallersAttribute** pour autoriser les assemblys avec nom fort à être appelé par le Concepteur de rapports ou le serveur de rapports dans les expressions de rapport. Pour permettre à du code d'un niveau de confiance partiel d'appeler des assemblys avec noms forts, ajoutez l'attribut de niveau assembly suivant au fichier d'attribut de votre assembly.  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 **AllowPartiallyTrustedCallersAttribute** est efficace uniquement lorsqu’il est appliqué à un assembly avec nom fort au niveau de l’assembly. Pour plus d’informations sur l’application des attributs au niveau de l’assembly, consultez « Application des attributs » dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] documentation du Kit de développement logiciel.  
  
> [!CAUTION]  
>  Lorsque **AllowPartiallyTrustedCallersAttribute** est présent, la valeur par défaut **FullTrustLinkDemand** des vérifications de sécurité ne sont pas autorisées, qui effectue l’assembly peut être appelée à partir de n’importe quel autre partiellement approuvé l’assembly. Toutes les vérifications de sécurité, notamment les attributs de sécurité déclaratifs au niveau de la classe ou de la méthode, doivent être déclarées explicitement.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'assemblages personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
