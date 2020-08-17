---
description: StdevP (MDX)
title: StdevP (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7b634f6bf6edf71f235458beb35e118165d126e1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386925"
---
# <a name="stdevp-mdx"></a>StdevP (MDX)


  Retourne l’écart-type de remplissage d’une expression numérique évaluée sur un jeu, à l’aide de la formule de remplissage biaisée (division par *n*).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
StdevP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 La fonction **StDevP** utilise la formule de remplissage biaisée, tandis que la fonction [StDev](../mdx/stdev-mdx.md) utilise la formule de remplissage non biaisée.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne l'écart-type de la mesure Internet Order Quantity (volume de commandes Internet) évaluée sur les trois premiers mois de l'année civile 2003 à l'aide de la formule de remplissage biaisée.  
  
```  
WITH MEMBER Measures.x AS   
   StdevP   
   ( { [Date].[Calendar].[Month].[January 2003],  
       [Date].[Calendar].[Month].[February 2003],  
       [Date].[Calendar].[Month].[March 2003]},  
    [Measures].[Internet Order Quantity])  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
