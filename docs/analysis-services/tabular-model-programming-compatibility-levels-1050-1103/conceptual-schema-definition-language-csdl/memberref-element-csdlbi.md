---
title: "L’élément MemberRef (CSDLBI) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 399aaa34-896c-48e7-aacb-18564f31b568
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8c1bb47c2273d79e320e53b49c524112b067a2d3
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="memberref-element-csdlbi"></a>Élément MemberRef (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
L'élément MemberRef spécifie le nom d'une propriété qui est la cible d'une référence.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément MemberRef.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Nom|Oui|Nom de la propriété contenue dans un élément MemberRef.|  
  
## <a name="memberrefs-element"></a>Élément MemberRefs  
 MemberRefs est un type complexe qui définit une collection de membres dans laquelle chaque membre est contenu dans un élément MemberRef.  
  
 Le tableau suivant répertorie les éléments et les attributs de type MemberRefs.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|MemberRef|Oui|Chaîne contenant la référence de membre.|  
  
## <a name="example"></a>Exemple  
 **Sous forme de tableau**  
  
 L'exemple suivant, en CSDLBI version 1.1, représente une partie du modèle de données exemple AdventureWorks qui définit la table Products. L'élément MemberRef est utilisé pour chaque colonne incluse dans l'ensemble de champs par défaut du modèle.  
  
```  
  
<bi:EntityType>  
   <bi:DefaultDetails>  
     <bi:MemberRef Name="Color" />  
     <bi:MemberRef Name="DealerPrice" />  
     <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>Exemple  
 **Multidimensionnel**  
  
 L'exemple suivant, en CSDLBI version 1.1, représente une partie du cube Contoso Operations qui définit la table Bikes. Dans cet exemple, un élément MemberRef est utilisé pour spécifier le nom de la colonne utilisée en tant qu'ensemble de champs par défaut dans les rapports et un autre élément MemberRef permet de référencer la colonne qui fournit l'ordre de tri.  
  
```  
  
<bi:DefaultDetails>  
   <bi:MemberRef Name="Color" />  
</bi:DefaultDetails>  
  
<bi:SortMembers>  
   <bi:MemberRef Name="Color" />  
</bi:SortMembers>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations techniques de référence pour les Annotations BI au langage CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
