---
title: Cellules (Analysis Services - données multidimensionnelles) du cube | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ca4be0cf2c9045ec47d8731830db99c87f32cf0b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62727717"
---
# <a name="cube-cells-analysis-services---multidimensional-data"></a>Cellules de cube (Analysis Services - Données multidimensionnelles)
  Un cube est composé de cellules organisées en groupes de mesures et en dimensions. Une cellule représente l'unique intersection logique dans un cube d'un membre de chaque dimension du cube. Par exemple, le cube décrit dans le diagramme suivant contient un groupe de mesures comprenant deux mesures, organisées en fonction de trois dimensions nommées Source, Itinéraire et Temps.  
  
 ![Diagramme de cube identifiant une cellule unique](../../../2014/analysis-services/dev-guide/media/as-cubeintro5.gif "diagramme de Cube identifiant une cellule unique")  
  
 L'unique cellule ombrée dans ce diagramme est l'intersection des membres suivants :  
  
-   le membre air de la dimension Itinéraire ;  
  
-   le membre Afrique de la dimension Source ;  
  
-   le membre quatrième trimestre de la dimension Temps ;  
  
-   la mesure Packages.  
  
## <a name="leaf-and-nonleaf-cells"></a>Cellules feuille et non-feuille  
 La valeur d'une cellule dans un cube peut être obtenue de différentes façons. Dans l’exemple précédent, la valeur dans la cellule peut être directement récupérée à partir de la table de faits du cube, étant donné que tous les membres utilisés pour identifier cette cellule sont *des membres feuille*. Un membre feuille n'a pas de membre enfant, d'un point de vue hiérarchique, et il fait généralement référence à un seul enregistrement dans une table de dimension. Ce type de cellule est appelé un *cellule feuille*.  
  
 Toutefois, une cellule peut également être identifiée à l’aide de *membres non-feuilles*. Un membre non-feuille est un membre qui possède un ou plusieurs membres enfants. Dans ce cas, la valeur de la cellule dérive le plus souvent de l'agrégation de membres enfants associés au membre non-feuille. Par exemple, l'intersection entre les membres et dimensions suivants est une cellule dont la valeur est fournie par agrégation :  
  
-   le membre air de la dimension Itinéraire ;  
  
-   le membre Afrique de la dimension Source ;  
  
-   le membre de la deuxième partie de la dimension Temps ;  
  
-   le membre Packages.  
  
 le membre de la deuxième partie de la dimension Temps est un membre non-feuille ; par conséquent, toutes les valeurs qui lui sont associées doivent être agrégées, comme le montre le diagramme suivant.  
  
 ![3e et 4e cellules trimestre pour le membre de la 2e partie](../../../2014/analysis-services/dev-guide/media/as-cubeintro6.gif "3e et 4e cellules trimestre pour le membre de la 2e partie")  
  
 Si l'on part du principe que les membres du troisième trimestre et du quatrième trimestre sont des sommes, la valeur de la cellule spécifiée est 400, soit le total de toutes les cellules feuille ombrées dans le diagramme précédent. Étant donné que la valeur de la cellule est dérivée de l’agrégation d’autres cellules, la cellule spécifiée est considérée comme un *cellule non-feuille*.  
  
 La valeur des cellules dérivées pour les membres qui utilisent des cumuls personnalisés et des groupes de membres, ainsi que des membres personnalisés, est gérée de façon analogue. En revanche, les valeurs de cellules dérivées pour des membres calculés se fondent entièrement sur l'expression MDX (Multidimensional Expressions) utilisée pour définir le membre calculé ; dans certains cas, elles peuvent très bien ne faire intervenir aucune donnée de cellule concrète. Pour plus d’informations, consultez [des opérateurs de cumul personnalisé dans les Dimensions Parent-enfant](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md), [définir des formules de membre personnalisées](../multidimensional-models/attribute-properties-define-custom-member-formulas.md), et [calculs](../multidimensional-models-olap-logical-cube-objects/calculations.md).  
  
## <a name="empty-cells"></a>Cellules vides  
 Il n'est pas nécessaire que toutes les cellules d'un cube contiennent une valeur ; il peut exister dans un cube des intersections qui ne contiennent pas de données. Ces intersections, appelées cellules vides, sont même fréquentes dans les cubes, car une intersection entre un attribut de dimension et une mesure à l'intérieur d'un cube ne contient pas nécessairement un enregistrement correspondant dans une table de faits. Le rapport entre les cellules vides dans un cube pour le nombre total de cellules dans un cube est fréquemment appelé le *densité* d’un cube.  
  
 Ainsi, la structure du cube illustrée par le diagramme suivant rappelle certains exemples cités dans cette rubrique. La seule différence est l'absence d'expéditions par avion vers l'Afrique au cours du troisième trimestre et vers l'Australie au cours du quatrième trimestre. La table de faits ne contient pas de données pour les intersections de ces dimensions et mesures ; par conséquent les cellules constituant ces intersections sont vides.  
  
 ![Diagramme de cube identifiant les cellules vides](../../../2014/analysis-services/dev-guide/media/as-cubeintro7.gif "diagramme de Cube identifiant les cellules vides")  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], une cellule vide est une cellule qui présente des qualités spéciales. Les cellules vides pouvant fausser les résultats des jointures croisées, des comptages, etc., un grand nombre de fonctions MDX permettent de les ignorer. Pour plus d’informations, consultez [Expressions multidimensionnelles &#40;MDX&#41; référence](/sql/mdx/multidimensional-expressions-mdx-reference), et [Concepts clés dans MDX &#40;Analysis Services&#41;](../multidimensional-models/key-concepts-in-mdx-analysis-services.md).  
  
## <a name="security"></a>Sécurité  
 Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], l'accès aux données des cellules est géré au niveau des rôles et il peut être soigneusement contrôlé en utilisant des expressions MDX Pour plus d’informations, consultez [octroyer un accès personnalisé aux données de dimension &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md), et [octroyer un accès personnalisé aux données des cellules &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Stockage de cube &#40;Analysis Services - données multidimensionnelles&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)   
 [Agrégations et conceptions d’agrégation](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
