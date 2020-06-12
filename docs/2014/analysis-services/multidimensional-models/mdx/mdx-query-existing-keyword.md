---
title: Mot clé EXISTing (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: 115444c832fe8fe9b258a0c23b97b97553f32e8e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546211"
---
# <a name="existing-keyword-mdx"></a>Mot clé EXISTING (MDX)
  Force un jeu spécifié à être évalué dans le contexte actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression d'ensemble MDX (Multidimensional Expressions) valide.  
  
## <a name="remarks"></a>Notes  
 Par défaut, les jeux sont évalués dans le contexte du cube qui contient les membres de ce jeu. Le mot clé `Existing` contraint un jeu spécifié à être évalué dans le contexte actuel à la place.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne le nombre de revendeurs dont les ventes ont baissé sur la période précédente en se basant sur les valeurs de membres State-Province (état-province) sélectionnées par l'utilisateur et évaluées à l'aide de la fonction `Aggregate`. Le mot clé [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) et [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) sont utilisées pour retourner des valeurs de ventes en baisse concernant les catégories de produits inscrites dans la dimension Product. Le `Existing` mot clé force le jeu dans la `Filter` fonction à être évalué dans le contexte actuel, c’est-à-dire, pour les membres de Washington et Oregon de la hiérarchie d’attribut State-Province.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40;défini&#41; &#40;&#41;MDX](/sql/mdx/count-set-mdx)   
 [AddCalculatedMembers&#41;MDX &#40;](/sql/mdx/addcalculatedmembers-mdx)   
 [&#41;MDX &#40;Aggregate](/sql/mdx/aggregate-mdx)   
 [Filtre &#40;&#41;MDX](/sql/mdx/filter-mdx)   
 [Propriétés &#40;MDX&#41;](/sql/mdx/properties-mdx)   
 [DrilldownLevel&#41;MDX &#40;](/sql/mdx/drilldownlevel-mdx)   
 [Hierarchize&#41;MDX &#40;](/sql/mdx/hierarchize-mdx)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  
