---
description: DrillupLevel (MDX)
title: DrillupLevel (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cfdb8e77fcb92fe208e83f45c32a5c20c5d29615
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421903"
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (MDX)


  Extrait vers le haut les membres d'un jeu situé au-dessous du niveau spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
## <a name="remarks"></a>Notes  
 La fonction **DrillupLevel** retourne un ensemble de membres organisés hiérarchiquement en fonction des membres inclus dans le jeu spécifié. L'ordre des membres dans le jeu spécifié est conservé.  
  
 Si une expression de niveau est spécifiée, la fonction **DrillupLevel** construit le jeu en extrayant uniquement les membres qui se trouvent au-dessus du niveau spécifié. Si une expression de niveau est spécifiée et qu’il n’y a aucun membre du niveau spécifié représenté dans le jeu spécifié, le jeu spécifié est retourné.  
  
 Si aucune expression de niveau n'est spécifiée, la fonction construit le jeu en récupérant uniquement les membres situés un niveau au-dessus du niveau le plus bas de la première dimension référencée dans le jeu spécifié.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne l'ensemble des membres du premier jeu placés au-dessus du niveau Subcategory.  
  
```  
SELECT DrillUpLevel   
  ({[Product].[Product Categories].[All Products]  
    ,[Product].[Product Categories].[Subcategory].&[32],  
    [Product].[Product Categories].[Product].&[215]},  
  [Product].[Product Categories].[Subcategory]  
    )  
  ON 0  
  FROM [Adventure Works]  
  WHERE [Measures].[Internet Order Quantity]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
