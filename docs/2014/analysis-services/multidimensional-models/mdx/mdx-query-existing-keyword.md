---
title: EXISTING Keyword (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ceaeac711ed30028dab3bc09827df9b6ae1f0e0a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62725353"
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
 L'exemple ci-dessous retourne le nombre de revendeurs dont les ventes ont baissé sur la période précédente en se basant sur les valeurs de membres State-Province (état-province) sélectionnées par l'utilisateur et évaluées à l'aide de la fonction `Aggregate`. Le mot clé [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) et [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) sont utilisées pour retourner des valeurs de ventes en baisse concernant les catégories de produits inscrites dans la dimension Product. Le `Existing` mot clé force le jeu dans le `Filter` fonction à évaluer dans le contexte actuel, autrement dit, pour les membres Washington et Oregon de la hiérarchie d’attribut State-Province.  
  
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
 [Count &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx)   
 [AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx)   
 [Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx)   
 [Filter &#40;MDX&#41;](/sql/mdx/filter-mdx)   
 [Propriétés &#40;MDX&#41;](/sql/mdx/properties-mdx)   
 [DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx)   
 [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx)   
 [Informations de référence sur les fonctions MDX &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  
