---
title: Head (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 05cfcb3c23a0369f010b8440d4a27e94ffacdb21
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63125565"
---
# <a name="head-mdx"></a>Head (MDX)


  Retourne le premier nombre spécifié d'éléments dans un jeu, en conservant les doublons.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Head(Set_Expression [ ,Count ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Compter*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
## <a name="remarks"></a>Notes  
 Le **Head** fonction retourne le nombre spécifié de tuples à partir du début du jeu spécifié. L'ordre des éléments est conservé. La valeur par défaut de Count est 1. Si le nombre de tuples spécifié est inférieur à 1, le **Head** fonction retourne un jeu vide. Si le nombre de tuples spécifié dépasse le nombre de tuples dans le jeu, la fonction retourne le jeu d'origine.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne les cinq premières sous-catégories de vente de produits, quelle que soit la hiérarchie et conformément à la mesure Reseller Gross Profit (marge brute du revendeur). Le **Head** fonction est utilisée pour retourner uniquement les 5 premiers jeux dans le résultat une fois que le résultat est trié à l’aide de la **ordre** (fonction).  
  
```  
SELECT   
[Measures].[Reseller Gross Profit] ON 0,  
Head  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,5  
   ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tail &#40;MDX&#41;](../mdx/tail-mdx.md)   
 [Item &#40;Tuple&#41; &#40;MDX&#41;](../mdx/item-tuple-mdx.md)   
 [Item &#40;Member&#41; &#40;MDX&#41;](../mdx/item-member-mdx.md)   
 [Rank &#40;MDX&#41;](../mdx/rank-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
