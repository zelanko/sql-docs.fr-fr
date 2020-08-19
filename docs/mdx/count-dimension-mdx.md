---
description: Count (Dimension) (MDX)
title: Count (dimension) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: afa58c330210e4fdb34d13892101e210f54cd3bd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429961"
---
# <a name="count-dimension-mdx"></a>Count (Dimension) (MDX)


  Retourne le nombre de hiérarchies dans un cube.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Dimensions.Count   
```  
  
## <a name="remarks"></a>Notes  
 Retourne le nombre de hiérarchies d'un cube, notamment la hiérarchie `[Measures].[Measures]`.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne le nombre de hiérarchies dans le cube Adventure Works.  
  
```  
WITH MEMBER measures.X AS  
  dimensions.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40;Tuple&#41; &#40;&#41;MDX ](../mdx/count-tuple-mdx.md)   
 [Nombre &#40;niveaux de hiérarchie&#41; &#40;&#41;MDX ](../mdx/count-hierarchy-levels-mdx.md)   
 [Nombre &#40;défini&#41; &#40;&#41;MDX ](../mdx/count-set-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
