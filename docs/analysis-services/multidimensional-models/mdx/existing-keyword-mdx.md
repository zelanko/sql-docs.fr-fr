---
title: "Mot cl&#233; EXISTING (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXISTING"
helpviewer_keywords: 
  - "Mot clé Existing"
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
caps.latest.revision: 38
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Mot cl&#233; EXISTING (MDX)
  Force un jeu spécifié à être évalué dans le contexte actuel.  
  
## Syntaxe  
  
```  
  
Existing Set_Expression  
```  
  
## Arguments  
 *Set_Expression*  
 Expression d'ensemble MDX (Multidimensional Expressions) valide.  
  
## Notes  
 Par défaut, les jeux sont évalués dans le contexte du cube qui contient les membres de ce jeu. Le mot clé **Existing** contraint un jeu spécifié à être évalué dans le contexte actuel à la place.  
  
## Exemple  
 L’exemple ci-dessous retourne le nombre de revendeurs dont les ventes ont baissé sur la période précédente en se basant sur les valeurs de membres State-Province (état-province) sélectionnées par l’utilisateur et évaluées à l’aide de la fonction **Aggregate**. Les fonctions [Hierarchize &#40;MDX&#41;](../../../mdx/hierarchize-mdx.md) et [DrilldownLevel (MDX)](../../../mdx/drilldownlevel-mdx.md) sont utilisées pour retourner des valeurs de ventes en baisse concernant les catégories de produits inscrites dans la dimension Product. Le mot clé **Existing** force le jeu dans la fonction **Filter** à être évalué dans le contexte actuel, c’est-à-dire pour les membres Washington et Oregon de la hiérarchie d’attribut State-Province.  
  
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
  
## Voir aussi  
 [Count &#40;Set&#41; &#40;MDX&#41;](../../../mdx/count-set-mdx.md)   
 [AddCalculatedMembers &#40;MDX&#41;](../../../mdx/addcalculatedmembers-mdx.md)   
 [Aggregate &#40;MDX&#41;](../../../mdx/aggregate-mdx.md)   
 [Filter &#40;MDX&#41;](../../../mdx/filter-mdx.md)   
 [Propriétés &#40;MDX&#41;](../../../mdx/properties-mdx.md)   
 [DrilldownLevel &#40;MDX&#41;](../../../mdx/drilldownlevel-mdx.md)   
 [Hierarchize &#40;MDX&#41;](../../../mdx/hierarchize-mdx.md)   
 [Informations de référence sur les fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)  
  
  