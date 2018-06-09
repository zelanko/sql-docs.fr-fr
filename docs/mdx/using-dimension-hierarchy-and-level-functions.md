---
title: À l’aide de la Dimension, hiérarchie et fonctions de niveau | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fb6460ed28c856ef6b5ceea8bf89c7bf33f54f2e
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743388"
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Utilisation de fonctions de dimension, de hiérarchie et de niveau


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
  
  
