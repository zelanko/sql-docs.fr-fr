---
title: "Cellules (Analysis Services - données multidimensionnelles) du cube | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- storing data [Analysis Services], cells
- hierarchies [Analysis Services], cells
- OLAP objects [Analysis Services], cells
- data members [Analysis Services]
- cubes [Analysis Services], cells
- empty cells [Analysis Services]
- nonleaf members
- cubes [Analysis Services], examples
- storage [Analysis Services], cells
- nonleaf cells
- calculated cells [Analysis Services]
- dimensions [Analysis Services], cells
- cells [Analysis Services]
- leaf members
- leaf cells
ms.assetid: 9945773c-a43b-40d4-91cf-3d2ebc90bca5
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7da5c513675b85a209e76da5787828eb31be24f8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="cube-cells-analysis-services---multidimensional-data"></a>Cellules de cube (Analysis Services - Données multidimensionnelles)
  Un cube est composé de cellules organisées en groupes de mesures et en dimensions. Une cellule représente l'unique intersection logique dans un cube d'un membre de chaque dimension du cube. Par exemple, le cube décrit dans le diagramme suivant contient un groupe de mesures comprenant deux mesures, organisées en fonction de trois dimensions nommées Source, Itinéraire et Temps.  
  
 ![Diagramme de cube identifiant une cellule unique](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro5.gif "diagramme de Cube identifiant une cellule unique")  
  
 L'unique cellule ombrée dans ce diagramme est l'intersection des membres suivants :  
  
-   le membre air de la dimension Itinéraire ;  
  
-   le membre Afrique de la dimension Source ;  
  
-   le membre quatrième trimestre de la dimension Temps ;  
  
-   la mesure Packages.  
  
## <a name="leaf-and-nonleaf-cells"></a>Cellules feuille et non-feuille  
 La valeur d'une cellule dans un cube peut être obtenue de différentes façons. Dans l’exemple précédent, la valeur dans la cellule permettre être récupérée directement à partir de la table de faits du cube, car tous les membres utilisés pour identifier cette cellule sont *des membres feuille*. Un membre feuille n'a pas de membre enfant, d'un point de vue hiérarchique, et il fait généralement référence à un seul enregistrement dans une table de dimension. Ce type de cellule est appelé un *cellule feuille*.  
  
 Toutefois, une cellule peut également être identifiée à l’aide de *membres non-feuilles*. Un membre non-feuille est un membre qui possède un ou plusieurs membres enfants. Dans ce cas, la valeur de la cellule dérive le plus souvent de l'agrégation de membres enfants associés au membre non-feuille. Par exemple, l'intersection entre les membres et dimensions suivants est une cellule dont la valeur est fournie par agrégation :  
  
-   le membre air de la dimension Itinéraire ;  
  
-   le membre Afrique de la dimension Source ;  
  
-   le membre de la deuxième partie de la dimension Temps ;  
  
-   le membre Packages.  
  
 le membre de la deuxième partie de la dimension Temps est un membre non-feuille ; par conséquent, toutes les valeurs qui lui sont associées doivent être agrégées, comme le montre le diagramme suivant.  
  
 ![3e et 4e cellules trimestre pour le membre 2nd half](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro6.gif "3e et 4e cellules trimestre pour le membre 2nd half")  
  
 Si l'on part du principe que les membres du troisième trimestre et du quatrième trimestre sont des sommes, la valeur de la cellule spécifiée est 400, soit le total de toutes les cellules feuille ombrées dans le diagramme précédent. Étant donné que la valeur de la cellule est dérivée de l’agrégation d’autres cellules, la cellule spécifiée est considéré comme un *cellule non-feuille*.  
  
 La valeur des cellules dérivées pour les membres qui utilisent des cumuls personnalisés et des groupes de membres, ainsi que des membres personnalisés, est gérée de façon analogue. En revanche, les valeurs de cellules dérivées pour des membres calculés se fondent entièrement sur l'expression MDX (Multidimensional Expressions) utilisée pour définir le membre calculé ; dans certains cas, elles peuvent très bien ne faire intervenir aucune donnée de cellule concrète. Pour plus d’informations, consultez [des opérateurs de cumul personnalisés dans les Dimensions Parent-enfant](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md), [définir des formules de membre personnalisées](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md), et [calculs](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md).  
  
## <a name="empty-cells"></a>Cellules vides  
 Il n'est pas nécessaire que toutes les cellules d'un cube contiennent une valeur ; il peut exister dans un cube des intersections qui ne contiennent pas de données. Ces intersections, appelées cellules vides, sont même fréquentes dans les cubes, car une intersection entre un attribut de dimension et une mesure à l'intérieur d'un cube ne contient pas nécessairement un enregistrement correspondant dans une table de faits. Le rapport entre les cellules vides dans un cube pour le nombre total de cellules dans un cube est fréquemment évoqué comme la *densité* d’un cube.  
  
 Ainsi, la structure du cube illustrée par le diagramme suivant rappelle certains exemples cités dans cette rubrique. La seule différence est l'absence d'expéditions par avion vers l'Afrique au cours du troisième trimestre et vers l'Australie au cours du quatrième trimestre. La table de faits ne contient pas de données pour les intersections de ces dimensions et mesures ; par conséquent les cellules constituant ces intersections sont vides.  
  
 ![Diagramme de cube identifiant les cellules vides](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro7.gif "diagramme de Cube identifiant les cellules vides")  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], une cellule vide est une cellule qui présente des qualités spéciales. Les cellules vides pouvant fausser les résultats des jointures croisées, des comptages, etc., un grand nombre de fonctions MDX permettent de les ignorer. Pour plus d’informations, consultez [Expressions multidimensionnelles &#40; MDX &#41; Référence](../../mdx/multidimensional-expressions-mdx-reference.md), et [Concepts clés pour MDX &#40; Analysis Services &#41; ](../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
## <a name="security"></a>Sécurité  
 Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], l'accès aux données des cellules est géré au niveau des rôles et il peut être soigneusement contrôlé en utilisant des expressions MDX Pour plus d’informations, consultez [octroyer un accès personnalisé à la dimension de données &#40; Analysis Services &#41; ](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md), et [octroyer un accès personnalisé à la cellule de données &#40; Analysis Services &#41; ](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Stockage de cube &#40; Analysis Services - données multidimensionnelles &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)   
 [Agrégations et conceptions d'agrégation](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
