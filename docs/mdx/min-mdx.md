---
description: Min (MDX)
title: Min (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c93abf0f98b04994f028379b8bd576deff4b7ea1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483812"
---
# <a name="min-mdx"></a>Min (MDX)


  Retourne la valeur minimale d'une expression numérique évaluée sur un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Min( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, cette expression est évaluée sur le jeu, puis retourne la valeur minimale produite par cette évaluation. Si aucune expression numérique n'est précisée, le jeu spécifié est évalué dans le contexte actuel des membres du jeu, puis retourne la valeur minimale de l'évaluation.  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ignore les valeurs NULL lors du calcul de la valeur minimale dans un jeu de nombres.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne les ventes trimestrielles minimales de chaque sous-catégorie et chaque pays inscrit dans le cube Adventure Works.  
  
```  
WITH MEMBER Measures.x AS Min   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
