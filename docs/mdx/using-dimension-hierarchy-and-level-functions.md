---
title: Utilisation des fonctions de dimension, de hiérarchie et de niveau | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8fa374ef93f56f8cddaed81bc9e3872d1eb206c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097179"
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Utilisation de fonctions de dimension, de hiérarchie et de niveau


  Les fonctions de dimension, de hiérarchie et de niveau peuvent être utiles pour parcourir les structures multidimensionnelles contenues dans Analysis Services. Pour obtenir des informations sur les membres d'une dimension, d'une hiérarchie ou d'un niveau, vous utilisez généralement ce type de fonctions conjointement avec d'autres fonctions.  
  
 L’exemple suivant montre comment utiliser **. Dimension**, **. Hiérarchie**et **. **Fonctions de niveau :  
  
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
 [&#41;de dimension &#40;MDX](../mdx/dimension-mdx.md)   
 [Fonctions &#40;syntaxe MDX&#41;](../mdx/functions-mdx-syntax.md)   
 [Hiérarchie &#40;MDX&#41;](../mdx/hierarchy-mdx.md)   
 [&#41;MDX de niveau &#40;](../mdx/level-mdx.md)  
  
  
