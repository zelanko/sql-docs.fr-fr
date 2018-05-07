---
title: À l’aide de la Dimension, hiérarchie et fonctions de niveau | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- dimensions [Analysis Services], functions
- level functions [MDX]
- hierarchy functions [MDX]
ms.assetid: e730f65a-1798-4094-9acf-2739e2505d52
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ee0b18ebe3b72da6d417763be12f2d803eaf9c8c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Utilisation de fonctions de dimension, de hiérarchie et de niveau
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Les fonctions de dimension, de hiérarchie et de niveau peuvent être utiles pour parcourir les structures multidimensionnelles contenues dans Analysis Services. Pour obtenir des informations sur les membres d'une dimension, d'une hiérarchie ou d'un niveau, vous utilisez généralement ce type de fonctions conjointement avec d'autres fonctions.  
  
 L’exemple suivant montre comment utiliser le **. Dimension**, **. Hiérarchie**, et **. Niveau** fonctions :  
  
 `WITH`  
  
 `MEMBER MEASURES.DIMENSIONNAME AS [Date].[Calendar].CURRENTMEMBER.DIMENSION.NAME`  
  
 `MEMBER MEASURES.HIERARCHYNAME AS [Date].[Calendar].CURRENTMEMBER.HIERARCHY.NAME`  
  
 `MEMBER MEASURES.LEVELNAME AS [Date].[Calendar].LEVEL.NAME`  
  
 `SELECT`  
  
 `{MEASURES.DIMENSIONNAME, MEASURES.HIERARCHYNAME, MEASURES.LEVELNAME}`  
  
 `ON Columns,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Dimension &#40;MDX&#41;](../mdx/dimension-mdx.md)   
 [Fonctions &#40;syntaxe MDX&#41;](../mdx/functions-mdx-syntax.md)   
 [Hiérarchie &#40;MDX&#41;](../mdx/hierarchy-mdx.md)   
 [Niveau &#40;MDX&#41;](../mdx/level-mdx.md)  
  
  
