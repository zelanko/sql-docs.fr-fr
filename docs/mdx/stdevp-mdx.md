---
title: StdevP (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: STDEVP
dev_langs: kbMDX
helpviewer_keywords: StdevP function [MDX]
ms.assetid: cd8ae7c9-3cef-49f0-bb41-8f577c7b6f31
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 697f1da527f797a203a8536c80894ba8bffe5dec
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="stdevp-mdx"></a>StdevP (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne l’écart-type de population d’une expression numérique évaluée sur un jeu, à l’aide de la formule de remplissage biaisée (division par  *n* ).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
StdevP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes   
 Le **StdevP** fonction utilise le remplissage biaisée formule lors de la [Stdev](../mdx/stdev-mdx.md) fonction utilise la formule de remplissage non biaisée.  
  
## <a name="example"></a> Exemple  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
