---
description: Item (Member) (MDX)
title: Item (membre) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a374d1fcc7f972828832c2f82375acf640d45fb2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483962"
---
# <a name="item-member-mdx"></a>Item (Member) (MDX)


  Retourne un membre à partir d'un tuple spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Tuple_Expression.Item( Index )  
```  
  
## <a name="arguments"></a>Arguments  
 *Tuple_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un tuple.  
  
 *Index*  
 Expression numérique valide qui précise le membre spécifique par position dans le tuple à retourner.  
  
## <a name="remarks"></a>Notes  
 La fonction **Item** retourne un membre à partir du tuple spécifié. La fonction retourne le membre trouvé à la position de base zéro spécifiée par *index*.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant retourne le membre `[2003]` - le premier élément dans le tuple `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).`- sur les colonnes :  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
