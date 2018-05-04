---
title: Nombre (Set) (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- Count function [MDX]
ms.assetid: 22f530e9-f8e1-4608-affa-9a2bc0821591
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 8fb02f59ec89c8c3c54c13973251ebdd78cfa32f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="count-set-mdx"></a>Count (Set) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 Le **Count (Set)** fonction inclut ou exclut les cellules vides, selon la syntaxe utilisée. Si la syntaxe standard est utilisée, les cellules vides peuvent être exclus ou inclus à l’aide de la **EXCLUDEEMPTY** ou **INCLUDEEMPTY** indicateurs, respectivement. Si vous utilisez l'autre syntaxe proposée, la fonction inclut toujours les cellules vides.  
  
 Pour exclure les cellules vides dans le comptage d’un jeu, utilisez la syntaxe standard et le paramètre facultatif **EXCLUDEEMPTY** indicateur.  
  
> [!NOTE]  
>  Le **Count (Set)** fonction compte les cellules vides par défaut. En revanche, le **nombre** fonction dans OLE DB qui compte un jeu exclut les cellules vides par défaut.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous compte le nombre de cellules dans le jeu de membres comprenant les enfants de la hiérarchie d'attribut Model Name dans la dimension Product.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant compte le nombre de produits dans la dimension Product à l’aide de la **DrilldownLevel** fonction conjointement avec la **nombre** (fonction).  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 L’exemple suivant retourne les revendeurs dont les refus des ventes par rapport au trimestre précédent, à l’aide de la **nombre** fonction conjointement avec la **filtre** fonction et un nombre d’autres fonctions. Cette requête utilise le **d’agrégation** fonction pour prendre en charge la sélection de nombreux membres géographiques, telles que pour les sélectionner à partir d’une liste déroulante dans une application cliente.  
  
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
 [Nombre &#40;des niveaux de hiérarchie&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Nombre &#40;Tuple&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel & #40 ; MDX & #41 ;](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers & #40 ; MDX & #41 ;](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize & #40 ; MDX & #41 ;](../mdx/hierarchize-mdx.md)   
 [Propriétés & #40 ; MDX & #41 ;](../mdx/properties-mdx.md)   
 [Agrégat & #40 ; MDX & #41 ;](../mdx/aggregate-mdx.md)   
 [Filtre & #40 ; MDX & #41 ;](../mdx/filter-mdx.md)   
 [PrevMember &#40;MDX&#41;](../mdx/prevmember-mdx.md)   
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
