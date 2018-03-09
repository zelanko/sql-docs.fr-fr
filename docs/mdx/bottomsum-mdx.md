---
title: BottomSum (MDX) | Documents Microsoft
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
f1_keywords: BOTTOMSUM
dev_langs: kbMDX
helpviewer_keywords: BottomSum function
ms.assetid: b3b10e68-2a36-4c38-85f4-3bb7917d5ae8
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ea22390b27a2ec2925cbdbc3d4d6ae257b2675dc
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="bottomsum-mdx"></a>BottomSum (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Trie un jeu spécifié par ordre croissant et retourne un jeu de tuples avec les valeurs les plus faibles dont le total est égal ou inférieur à une valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Value*  
 Expression numérique valide qui précise la valeur par rapport à laquelle chaque tuple est comparé.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes   
 Le **BottomSum** fonction calcule la somme d’une mesure spécifique évaluée sur un jeu spécifié, en triant le jeu par ordre croissant. Elle retourne ensuite les éléments dotés des valeurs les plus faibles dont le total de l'expression numérique spécifiée correspond au moins à la valeur indiquée (somme). Enfin, elle retourne le plus petit sous-ensemble d'un jeu dont le total cumulé est égal au moins à la valeur précisée. Les éléments retournés sont triés du plus petit au plus grand.  
  
> [!IMPORTANT]  
>  Le **BottomSum** fonction, comme le [TopSum](../mdx/topsum-mdx.md) de fonction, la hiérarchie.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne pour la catégorie Bikes (bicyclettes) le plus petit jeu de membres au niveau City (ville) de la hiérarchie Geography (zone géographique) dans la dimension Geography de l'année fiscale 2003 dont le total cumulé et obtenu à l'aide de la mesure Reseller Sales Amount (volume de vente du revendeur) correspond au moins à la somme de 50 000 (en commençant par les membres de jeu en question avec le nombre le plus faible de ventes) :  
  
 `SELECT`  
  
 `[Product].[Product Categories].Bikes ON 0,`  
  
 `BottomSum`  
  
 `({[Geography].[Geography].[City].Members}`  
  
 `, 50000`  
  
 `, ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)`  
  
 `) ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
