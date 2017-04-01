---
title: "Restriction de la requ&#234;te avec des axes de requ&#234;te et de secteur (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
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
  - "expressions multidimensionnelles [Analysis Services], axes"
  - "requêtes [MDX], axes"
  - "axes [MDX]"
  - "MDX [Analysis Services], axes"
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Restriction de la requ&#234;te avec des axes de requ&#234;te et de secteur (MDX)
  Lors de la formulation d'une instruction SELECT MDX (Multidimensional Expressions), une application examine généralement un cube et divise le jeu de hiérarchies en deux sous-ensembles :  
  
-   Les **axes de requête** — jeu de hiérarchies dont des données sont extraites pour plusieurs membres. Pour plus d’informations sur les axes de requête, consultez [Spécification du contenu d’un axe de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-query-axis-mdx.md).  
  
-   **L’axe de secteur** — jeu de hiérarchies dont des données sont extraites pour un seul membre. Pour plus d’informations sur l’axe de secteur, consultez [Spécification du contenu d’un axe de secteur &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-slicer-axis-mdx.md).  
  
 Dans la mesure où les axes de requête et de secteur peuvent être construits à partir de plusieurs hiérarchies du cube à interroger, ces termes permettent de différencier les hiérarchies utilisées par le cube devant faire l'objet d'une interrogation par rapport aux hiérarchies créées dans le cube retourné par une requête MDX.  
  
 Pour obtenir un exemple d’utilisation des axes de requête et de secteur, consultez [Utilisation d’axes de requête et de secteur dans un exemple simple&#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-query-and-slicer-axes-in-a-simple-example-mdx.md).  
  
## Voir aussi  
 [Utilisation de membres, de tuples et de jeux &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Principes de base des requêtes MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  