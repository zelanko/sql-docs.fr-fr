---
title: À l’aide des propriétés de membre (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e650ee07183123f5c90e24129282820825cee652
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075545"
---
# <a name="using-member-properties-mdx"></a>Utilisation des propriétés de membre (MDX)
  Les propriétés de membre couvrent les informations de base relatives à chaque membre de chaque tuple. Ces informations de base comprennent le nom du membre, le niveau parent, le nombre d'enfants, etc. Les propriétés de membre sont mises à la disposition de tous les membres situés à un niveau donné. D'un point de vue organisationnel, les propriétés de membre sont regroupées en dimensions et traitées comme telles.  
  
> [!NOTE]  
>  Dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les propriétés de membre sont appelées relations d’attributs. Pour plus d’informations, consultez [Relations d’attributs](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
 Les propriétés de membre sont soit *intrinsèques* , soit *personnalisées*:  
  
 Propriétés de membre intrinsèques  
 Tous les membres prennent en charge les propriétés de membre intrinsèques, telles que la mise en forme de leur valeur, tandis que les dimensions et les niveaux fournissent des propriétés de membre intrinsèques supplémentaires relatives aux dimensions ou aux niveaux, telles que l'identificateur d'un membre.  
  
 Pour plus d’informations, consultez [Propriétés de membre intrinsèques &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).  
  
 Propriétés de membre définies par l'utilisateur  
 Des propriétés supplémentaires sont souvent associées aux membres. Par exemple, le niveau Products peut fournir les propriétés SKU, SRP, Weight et Volume de chaque produit. Ces propriétés ne sont pas des membres, mais elles contiennent des informations supplémentaires sur les membres situés au niveau Products.  
  
 Pour plus d’informations, consultez [Propriétés de membre définies par l’utilisateur &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).  
  
 Les deux propriétés de membre intrinsèques et définies par l’utilisateur peuvent être récupérées à l’aide de la `PROPERTIES` mot clé ou le [propriétés](/sql/mdx/properties-mdx) (fonction).  
  
## <a name="using-the-properties-keyword"></a>Utilisation du mot clé PROPERTIES  
 Le `PROPERTIES` mot clé spécifie les propriétés de membre doivent être utilisées pour une dimension d’axe donné. Le `PROPERTIES` mot clé est compris dans le `<axis specification>` clause du code MDX [sélectionnez](/sql/mdx/mdx-data-manipulation-select) instruction :  
  
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
>  Pour plus d’informations sur les valeurs `<set>` et `<axis_name>`, consultez [Spécification du contenu d’un axe de requête &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
 Le `<dim_props>` clause vous permet d’interroger dimension, niveau et les propriétés de membre à l’aide de la `PROPERTIES` mot clé. La syntaxe suivante illustre le format de la clause `<dim_props>` :  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 Le détail de la syntaxe de `<property>` varie en fonction de la propriété interrogée :  
  
-   Les propriétés de membre intrinsèques sensibles au contexte doivent être précédées du nom de la dimension ou du niveau. Par contre, les propriétés de membre intrinsèques non sensibles au contexte ne peuvent pas être spécifiées à l'aide du nom de la dimension ou du niveau. Pour plus d’informations sur l’utilisation de la `PROPERTIES` mot clé avec les propriétés de membre intrinsèques, consultez [propriétés de membre intrinsèques &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).  
  
-   Les propriétés de membre définies par l'utilisateur doivent être précédées du nom du niveau dans lequel elles résident. Pour plus d’informations sur l’utilisation de la `PROPERTIES` mot clé avec des propriétés de membre définies par l’utilisateur, consultez [propriétés de membre définies par l’utilisateur &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création et utilisation des valeurs de propriété &#40;MDX&#41;](../../creating-and-using-property-values-mdx.md)  
  
  
