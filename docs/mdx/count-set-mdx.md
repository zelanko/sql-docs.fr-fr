---
description: Count (Set) (MDX)
title: Count (Set) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3a8760d4df4aa1479aaa9ad365c92a5168eb3869
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341525"
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
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 La fonction **Count (Set)** inclut ou exclut les cellules vides, selon la syntaxe utilisée. Si la syntaxe standard est utilisée, les cellules vides peuvent être exclues ou incluses à l’aide des indicateurs **ExcludeEmpty** ou **INCLUDEEMPTY** , respectivement. Si vous utilisez l'autre syntaxe proposée, la fonction inclut toujours les cellules vides.  
  
 Pour exclure des cellules vides dans le nombre d’un jeu, utilisez la syntaxe standard et l’indicateur **ExcludeEmpty** facultatif.  
  
> [!NOTE]  
>  La fonction **Count (Set)** compte les cellules vides par défaut. En revanche, la fonction **Count** de OLE DB qui compte un jeu exclut les cellules vides par défaut.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous compte le nombre de cellules dans le jeu de membres comprenant les enfants de la hiérarchie d'attribut Model Name dans la dimension Product.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant compte le nombre de produits dans la dimension Product à l’aide de la fonction **DrilldownLevel** conjointement avec la fonction **Count** .  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 L’exemple suivant retourne ces revendeurs dont les ventes sont refusées par rapport au trimestre calendaire précédent, à l’aide de la fonction **Count** , conjointement à la fonction **Filter** et à un certain nombre d’autres fonctions. Cette requête utilise la fonction **Aggregate** pour prendre en charge la sélection de plusieurs membres Geography, par exemple pour la sélection dans une liste déroulante dans une application cliente.  
  
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
 [Nombre &#40;dimension&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [Nombre &#40;niveaux de hiérarchie&#41; &#40;&#41;MDX ](../mdx/count-hierarchy-levels-mdx.md)   
 [Nombre &#40;Tuple&#41; &#40;&#41;MDX ](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel&#41;MDX &#40;](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers&#41;MDX &#40;](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize&#41;MDX &#40;](../mdx/hierarchize-mdx.md)   
 [Propriétés &#40;MDX&#41;](../mdx/properties-mdx.md)   
 [&#41;MDX &#40;Aggregate ](../mdx/aggregate-mdx.md)   
 [Filtre &#40;&#41;MDX ](../mdx/filter-mdx.md)   
 [PrevMember&#41;MDX &#40;](../mdx/prevmember-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
