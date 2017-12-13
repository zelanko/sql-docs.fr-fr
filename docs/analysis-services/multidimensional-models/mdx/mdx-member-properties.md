---
title: "À l’aide des propriétés de membre (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e4e769b70bbea26f1a7e2d0c951095e9c2a044d3
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="mdx-member-properties"></a>Propriétés de membre MDX
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Propriétés de membre couvrent les informations de base sur chaque membre de chaque tuple. Ces informations de base comprennent le nom du membre, le niveau parent, le nombre d'enfants, etc. Les propriétés de membre sont mises à la disposition de tous les membres situés à un niveau donné. D'un point de vue organisationnel, les propriétés de membre sont regroupées en dimensions et traitées comme telles.  
  
> [!NOTE]  
>  Dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les propriétés de membre sont appelées relations d’attributs. Pour plus d’informations, consultez [Relations d’attributs](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
 Les propriétés de membre sont soit *intrinsèques* , soit *personnalisées*:  
  
 Propriétés de membre intrinsèques  
 Tous les membres prennent en charge les propriétés de membre intrinsèques, telles que la mise en forme de leur valeur, tandis que les dimensions et les niveaux fournissent des propriétés de membre intrinsèques supplémentaires relatives aux dimensions ou aux niveaux, telles que l'identificateur d'un membre.  
  
 Pour plus d’informations, consultez [Propriétés de membre intrinsèques &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md).  
  
 Propriétés de membre définies par l'utilisateur  
 Des propriétés supplémentaires sont souvent associées aux membres. Par exemple, le niveau Products peut fournir les propriétés SKU, SRP, Weight et Volume de chaque produit. Ces propriétés ne sont pas des membres, mais elles contiennent des informations supplémentaires sur les membres situés au niveau Products.  
  
 Pour plus d’informations, consultez [Propriétés de membre définies par l’utilisateur &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
 Vous pouvez récupérer les propriétés de membre intrinsèques et définies par l’utilisateur à l’aide du mot clé **PROPERTIES** ou de la fonction [Properties](../../../mdx/properties-mdx.md).  
  
## <a name="using-the-properties-keyword"></a>Utilisation du mot clé PROPERTIES  
 Le mot clé **PROPERTIES** spécifie les propriétés de membre à utiliser pour une dimension donnée d’un axe. Le mot clé **PROPERTIES** est compris dans la clause `<axis specification>` de l’instruction MDX [SELECT](../../../mdx/mdx-data-manipulation-select.md) :  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 La clause `<axis_specification>` comprend une clause `<dim_props>` facultative, comme illustré dans la syntaxe suivante :  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur les valeurs `<set>` et `<axis_name>`, consultez [Spécification du contenu d’un axe de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
 La clause `<dim_props>` permet d’interroger les propriétés de dimension, de niveau et de membre à l’aide du mot clé **PROPERTIES**. La syntaxe suivante illustre le format de la clause `<dim_props>` :  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 Le détail de la syntaxe de `<property>` varie en fonction de la propriété interrogée :  
  
-   Les propriétés de membre intrinsèques sensibles au contexte doivent être précédées du nom de la dimension ou du niveau. Par contre, les propriétés de membre intrinsèques non sensibles au contexte ne peuvent pas être spécifiées à l'aide du nom de la dimension ou du niveau. Pour plus d’informations sur l’utilisation du mot clé **PROPERTIES** avec des propriétés de membre intrinsèques, consultez [Propriétés de membre intrinsèques &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md).  
  
-   Les propriétés de membre définies par l'utilisateur doivent être précédées du nom du niveau dans lequel elles résident. Pour plus d’informations sur la façon d’utiliser le mot clé **PROPERTIES** avec des propriétés de membre définies par l’utilisateur, consultez [Propriétés de membre définies par l’utilisateur &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création et utilisation de valeurs de propriétés &#40;MDX&#41;](http://msdn.microsoft.com/library/0cafb269-03c8-4183-b6e9-220f071e4ef2)  
  
  
