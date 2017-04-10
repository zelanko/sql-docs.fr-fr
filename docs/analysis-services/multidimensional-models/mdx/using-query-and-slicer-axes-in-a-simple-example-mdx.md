---
title: "Utilisation d&#39;axes de requ&#234;te et de d&#233;coupage dans un exemple simple (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
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
  - "axe de secteur"
  - "axe de requête [MDX]"
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Utilisation d&#39;axes de requ&#234;te et de d&#233;coupage dans un exemple simple (MDX)
  L'exemple simple fourni dans cette rubrique illustre les principes de base de la spécification et de l'utilisation d'axes de requête et de découpage.  
  
## Le cube  
 Un cube, appelé TestCube, possède deux dimensions simples appelées Route et Time. Chaque dimension ne possède qu'une hiérarchie d'utilisateur, appelées respectivement Route et Time. Puisque les mesures de ce cube font partie de la dimension Measures, ce cube possède trois dimensions.  
  
## La requête  
 La requête consiste à fournir une matrice dans laquelle la mesure Packages peut être comparée d'après des routes et des heures (Time).  
  
 Dans l'exemple de requête MDX suivant, les hiérarchies Route et Time sont les axes de requête et la dimension Measures est l'axe de découpage. La fonction [Members](../../../mdx/members-set-mdx.md) indique que la syntaxe MDX doit utiliser les membres de la hiérarchie ou du niveau pour construire un jeu. Grâce à l'utilisation de la fonction **Members** , vous ne devez pas déclarer explicitement chaque membre d'une hiérarchie ou d'un niveau spécifiques dans une requête MDX.  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## Les résultats  
 Le résultat est une grille identifiant la valeur de la mesure Packages à chaque intersection des dimensions d'axe COLUMNS et ROWS. Le tableau suivant représente l'aspect de cette grille.  
  
||air|sea|  
|-|---------|---------|  
|1st quarter|60|50|  
|2nd quarter|45|45|  
  
## Voir aussi  
 [Spécification du contenu d’un axe de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-query-axis-mdx.md)   
 [Spécification du contenu d’un axe de secteur &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-slicer-axis-mdx.md)  
  
  