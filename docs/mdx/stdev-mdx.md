---
title: StDev (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDEV
dev_langs:
- kbMDX
helpviewer_keywords:
- Stdev function [MDX]
ms.assetid: c3e31763-18ca-4a2b-bc03-3ee777970c68
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8cd0171595e5cdfd44c850565c0eba42d45784eb
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="stdev-mdx"></a>Stdev (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne l'exemple d'écart-type d'une expression numérique évaluée sur un jeu à l'aide de la formule de remplissage non biaisée (division par n-1).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stdev(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Le **Stdev** fonction utilise le remplissage non biaisée formule lors de la [StdevP](../mdx/stdevp-mdx.md) fonction utilise la formule de remplissage biaisée.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne l'écart-type de la mesure Internet Order Quantity (volume de commandes Internet) évaluée sur les trois premiers mois de l'année civile 2003 à l'aide de la formule de remplissage non biaisée.  
  
```  
WITH MEMBER Measures.x AS   
   Stdev   
   ( { [Date].[Calendar].[Month].[January 2003],  
       [Date].[Calendar].[Month].[February 2003],  
       [Date].[Calendar].[Month].[March 2003]},  
    [Measures].[Internet Order Quantity])  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

