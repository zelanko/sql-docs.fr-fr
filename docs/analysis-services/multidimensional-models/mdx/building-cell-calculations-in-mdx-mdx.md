---
title: "Cr&#233;ation de calculs de cellules &#224; l&#39;aide de la syntaxe MDX (MDX) | Microsoft Docs"
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
  - "cellules calculées [MDX]"
  - "requêtes [MDX], calculs de cellules"
  - "cellules [MDX]"
  - "MDX [Analysis Services], calculs"
  - "calcul de sous-cubes [MDX]"
  - "valeurs calculées [MDX]"
  - "Expressions multidimensionnelles [Analysis Services], calculs de cellules"
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Cr&#233;ation de calculs de cellules &#224; l&#39;aide de la syntaxe MDX (MDX)
  MDX (Multidimensional Expressions) propose un certain nombre d'outils qui vous permettent de générer des valeurs calculées comme des membres calculés, des cumuls personnalisés et des membres personnalisés. Cependant, il est difficile d'affecter un jeu de cellules spécifique (voire une cellule unique) à l'aide de ces outils.  
  
 Pour générer des valeurs calculées en particulier pour des cellules, vous devez utiliser la fonctionnalité de cellules calculées de MDX. Les cellules calculées permettent de définir une « tranche » de cellules, appelée *sous-cube de calcul*, et d’appliquer une formule à chacune des cellules de ce sous-cube de calcul, sous réserve d’une condition facultative qui peut être appliquée à chaque cellule.  
  
 Les cellules calculées proposent également des fonctionnalités complexes (par exemple, des formules de recherche d’objectif, telles qu'elles sont utilisées dans les KPI, ou des formules d'analyse spéculative). Ce niveau de fonctionnalité provient de la fonctionnalité d’ordre de passage de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] qui permet d’effectuer des passages récursifs sur des cellules calculées, avec des formules de calcul appliquées lors de passages spécifiques dans l’ordre de passage. Pour plus d’informations sur l’ordre de passage, consultez [Présentation des concepts d’ordre de passage et d’ordre de résolution &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/understanding-pass-order-and-solve-order-mdx.md).  
  
 Du point de vue de leur portée, les cellules calculées sont semblables aux jeux nommés et aux membres calculés en ce sens qu'elles peuvent créées temporairement pour la durée d'une session ou d'une seule requête, ou encore être globalement mises à la disposition des utilisateurs dans le cadre d'un cube :  
  
-   **Étendue de requête** Pour créer une cellule calculée définie en tant que partie d’une requête MDX, et dont l’étendue est donc limitée à la requête, utilisez le mot clé WITH. Vous pouvez ensuite utiliser la cellule calculée au sein d'une instruction MDX SELECT. De cette manière, vous pouvez modifier la cellule calculée créée à l’aide du mot clé **WITH** sans porter atteinte à l’instruction SELECT.  
  
     Pour plus d’informations sur l’utilisation du mot clé WITH pour la création de membres calculés, consultez [Création de calculs de cellules au niveau de la requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-cell-calculations-mdx.md).  
  
-   **Étendue de session** Pour créer un membre calculé dont l’étendue est plus étendue que le contexte de la requête, c’est-à-dire dont l’étendue est la durée de vie de la session MDX, vous devez utiliser l’instruction CREATE CELL CALCULATION ou ALTER CUBE.  
  
     Pour plus d’informations sur l’utilisation de l’instruction CREATE CELL CALCULATION ou ALTER CUBE afin de créer des cellules calculées dans une session, consultez [Création de cellules calculées au niveau de la session](../../../analysis-services/multidimensional-models/mdx/creating-session-scoped-calculated-cells.md).  
  
## Voir aussi  
 [Instruction ALTER CUBE &#40;MDX&#41;](../Topic/ALTER%20CUBE%20Statement%20\(MDX\).md)   
 [Instruction CREATE CELL CALCULATION &#40;MDX&#41;](../Topic/CREATE%20CELL%20CALCULATION%20Statement%20\(MDX\).md)   
 [Création de calculs de cellules au niveau de la requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-cell-calculations-mdx.md)   
 [Principes de base des requêtes MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  