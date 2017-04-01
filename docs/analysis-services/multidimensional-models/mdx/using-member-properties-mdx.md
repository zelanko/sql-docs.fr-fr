---
title: "Utilisation des propri&#233;t&#233;s de membre (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DIMENSION PROPERTIES (mot clé)"
  - "fonction Properties"
  - "propriétés de membre [MDX]"
  - "membres [MDX], propriétés"
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Utilisation des propri&#233;t&#233;s de membre (MDX)
  Les propriétés de membre couvrent les informations de base relatives à chaque membre de chaque tuple. Ces informations de base comprennent le nom du membre, le niveau parent, le nombre d'enfants, etc. Les propriétés de membre sont mises à la disposition de tous les membres situés à un niveau donné. D'un point de vue organisationnel, les propriétés de membre sont regroupées en dimensions et traitées comme telles.  
  
> [!NOTE]  
>  Dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les propriétés de membre sont appelées relations d’attributs. Pour plus d’informations, consultez [Relations d’attributs](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
 Les propriétés de membre sont soit *intrinsèques*, soit *personnalisées* :  
  
 Propriétés de membre intrinsèques  
 Tous les membres prennent en charge les propriétés de membre intrinsèques, telles que la mise en forme de leur valeur, tandis que les dimensions et les niveaux fournissent des propriétés de membre intrinsèques supplémentaires relatives aux dimensions ou aux niveaux, telles que l'identificateur d'un membre.  
  
 Pour plus d’informations, consultez [Propriétés de membre intrinsèques &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/intrinsic-member-properties-mdx.md).  
  
 Propriétés de membre définies par l'utilisateur  
 Des propriétés supplémentaires sont souvent associées aux membres. Par exemple, le niveau Products peut fournir les propriétés SKU, SRP, Weight et Volume de chaque produit. Ces propriétés ne sont pas des membres, mais elles contiennent des informations supplémentaires sur les membres situés au niveau Products.  
  
 Pour plus d’informations, consultez [Propriétés de membre définies par l’utilisateur &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/user-defined-member-properties-mdx.md).  
  
 Vous pouvez récupérer les propriétés de membre intrinsèques et définies par l’utilisateur à l’aide du mot clé **PROPERTIES** ou de la fonction [Properties](../../../mdx/properties-mdx.md).  
  
## Utilisation du mot clé PROPERTIES  
 Le mot clé **PROPERTIES** spécifie les propriétés de membre à utiliser pour une dimension donnée d’un axe. Le mot clé **PROPERTIES** est compris dans la clause `<axis specification>` de l’instruction MDX [SELECT](../Topic/SELECT%20Statement%20\(MDX\).md) :  
  
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
>  Pour plus d’informations sur les valeurs `<set>` et `<axis_name>`, consultez [Spécification du contenu d’un axe de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-query-axis-mdx.md).  
  
 La clause `<dim_props>` permet d’interroger les propriétés de dimension, de niveau et de membre à l’aide du mot clé **PROPERTIES**. La syntaxe suivante illustre le format de la clause `<dim_props>` :  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 Le détail de la syntaxe de `<property>` varie en fonction de la propriété interrogée :  
  
-   Les propriétés de membre intrinsèques sensibles au contexte doivent être précédées du nom de la dimension ou du niveau. Par contre, les propriétés de membre intrinsèques non sensibles au contexte ne peuvent pas être spécifiées à l'aide du nom de la dimension ou du niveau. Pour plus d’informations sur l’utilisation du mot clé **PROPERTIES** avec des propriétés de membre intrinsèques, consultez [Propriétés de membre intrinsèques &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/intrinsic-member-properties-mdx.md).  
  
-   Les propriétés de membre définies par l'utilisateur doivent être précédées du nom du niveau dans lequel elles résident. Pour plus d’informations sur la façon d’utiliser le mot clé **PROPERTIES** avec des propriétés de membre définies par l’utilisateur, consultez [Propriétés de membre définies par l’utilisateur &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/user-defined-member-properties-mdx.md).  
  
## Voir aussi  
 [Création et utilisation de valeurs de propriétés &#40;MDX&#41;](../Topic/Creating%20and%20Using%20Property%20Values%20\(MDX\).md)  
  
  