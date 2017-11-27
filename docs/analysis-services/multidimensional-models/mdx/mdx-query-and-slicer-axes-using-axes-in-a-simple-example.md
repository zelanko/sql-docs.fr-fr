---
title: "À l’aide d’Axes de requête et segment dans un exemple Simple (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e27b8a961e692a9b1757573e4c735949fc537153
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-query-and-slicer-axes---using-axes-in-a-simple-example"></a>Requête MDX et les Axes de segment - utilisation des Axes dans un exemple Simple
  L'exemple simple fourni dans cette rubrique illustre les principes de base de la spécification et de l'utilisation d'axes de requête et de découpage.  
  
## <a name="the-cube"></a>Le cube  
 Un cube, appelé TestCube, possède deux dimensions simples appelées Route et Time. Chaque dimension ne possède qu'une hiérarchie d'utilisateur, appelées respectivement Route et Time. Puisque les mesures de ce cube font partie de la dimension Measures, ce cube possède trois dimensions.  
  
## <a name="the-query"></a>La requête  
 La requête consiste à fournir une matrice dans laquelle la mesure Packages peut être comparée d'après des routes et des heures (Time).  
  
 Dans l'exemple de requête MDX suivant, les hiérarchies Route et Time sont les axes de requête et la dimension Measures est l'axe de découpage. La fonction [Members](../../../mdx/members-set-mdx.md) indique que la syntaxe MDX doit utiliser les membres de la hiérarchie ou du niveau pour construire un jeu. Grâce à l'utilisation de la fonction **Members** , vous ne devez pas déclarer explicitement chaque membre d'une hiérarchie ou d'un niveau spécifiques dans une requête MDX.  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a>Les résultats  
 Le résultat est une grille identifiant la valeur de la mesure Packages à chaque intersection des dimensions d'axe COLUMNS et ROWS. Le tableau suivant représente l'aspect de cette grille.  
  
||air|sea|  
|-|---------|---------|  
|1st quarter|60|50|  
|2nd quarter|45|45|  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification du contenu d’un axe de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)   
 [Spécification du contenu d’un axe de secteur &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
