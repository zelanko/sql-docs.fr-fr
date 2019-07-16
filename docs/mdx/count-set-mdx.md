---
title: Count (jeu) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: aac2f72cc8cd91e1964fd7734b858be8215cfdd8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68047293"
---
# <a name="count-set-mdx"></a>Count (Set) (MDX)


  Retourne le nombre de cellules d'un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Standard syntax  
Count(Set_Expression [ , ( EXCLUDEEMPTY | INCLUDEEMPTY ) ] )  
  
Alternate syntax  
Set_Expression.Count  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Le **Count (jeu)** fonction inclut ou exclut les cellules vides, selon la syntaxe utilisée. Si la syntaxe standard est utilisée, les cellules vides peuvent être exclus ou inclus à l’aide de la **EXCLUDEEMPTY** ou **INCLUDEEMPTY** indicateurs, respectivement. Si vous utilisez l'autre syntaxe proposée, la fonction inclut toujours les cellules vides.  
  
 Pour exclure les cellules vides dans le comptage d’un jeu, utilisez la syntaxe standard et la propriété facultative **EXCLUDEEMPTY** indicateur.  
  
> [!NOTE]  
>  Le **Count (jeu)** fonction compte les cellules vides par défaut. En revanche, le **nombre** fonction dans OLE DB qui compte un jeu exclut les cellules vides par défaut.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous compte le nombre de cellules dans le jeu de membres comprenant les enfants de la hiérarchie d'attribut Model Name dans la dimension Product.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant compte le nombre de produits dans la dimension Product en utilisant le **DrilldownLevel** fonction conjointement avec le **nombre** (fonction).  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 L’exemple suivant retourne les revendeurs dont les refus des ventes par rapport au trimestre précédent, à l’aide de la **nombre** fonction conjointement avec le **filtre** (fonction) et un nombre d’autres fonctions. Cette requête utilise le **agrégation** (fonction) pour prendre en charge la sélection de nombreux membres géographiques, comme pour les sélectionner à partir d’une liste déroulante, dans une application cliente.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
   (Filter  
      (Existing(Reseller.Reseller.Reseller),  
         [Measures].[Reseller Sales Amount]   
         < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
      )  
   )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate  
   ( {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
   )  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})  
      })  
   ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,  
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
   ,[Measures].[Declining Reseller Sales])  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40;Dimension&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [Nombre &#40;niveaux de hiérarchie&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Nombre &#40;Tuple&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize &#40;MDX&#41;](../mdx/hierarchize-mdx.md)   
 [Properties &#40;MDX&#41;](../mdx/properties-mdx.md)   
 [Aggregate &#40;MDX&#41;](../mdx/aggregate-mdx.md)   
 [Filter &#40;MDX&#41;](../mdx/filter-mdx.md)   
 [PrevMember &#40;MDX&#41;](../mdx/prevmember-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
