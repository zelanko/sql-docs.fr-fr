---
title: CurrentOrdinal (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d6fe956591b6bde0c5e6b074115fec8724995a59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248195"
---
# <a name="currentordinal-mdx"></a>CurrentOrdinal (MDX)


  Retourne le numéro d'itération actuel dans un jeu lors d'une itération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set_Expression.CurrentOrdinal  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Lors de l’itération via un ensemble, comme avec la [Filter (MDX)](../mdx/filter-mdx.md) ou [Generate (MDX)](../mdx/generate-mdx.md) fonctions, le **CurrentOrdinal** fonction retourne le numéro d’itération.  
  
## <a name="examples"></a>Exemples  
 L’exemple simple suivant illustre comment **CurrentOrdinal** peut être utilisé avec **générer** pour retourner une chaîne contenant le nom de chaque élément dans un jeu, ainsi que sa position dans le jeu :  
  
 `WITH SET MySet AS [Customer].[Customer Geography].[Country].MEMBERS`  
  
 `MEMBER MEASURES.CURRENTORDINALDEMO AS`  
  
 `GENERATE(MySet, CSTR(MySet.CURRENTORDINAL) + ") " + MySet.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTORDINALDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
 L'utilisation pratique de CurrentOrdinal est limitée aux calculs très complexes. L’exemple suivant retourne le nombre de produits dans le jeu qui sont uniques, à l’aide de la **ordre** fonction pour classer les tuples non vides avant d’utiliser le **filtre** (fonction). Le **CurrentOrdinal** fonction est utilisée pour comparer et éliminer les liens.  
  
```  
WITH MEMBER [Measures].[PrdTies] AS Count  
   (Filter  
      (Order  
        (NonEmpty  
          ([Product].[Product].[Product].Members  
          , {[Measures].[Reseller Order Quantity]}  
          )  
       , [Measures].[Reseller Order Quantity]  
       , BDESC  
       ) AS OrdPrds  
    , NOT((OrdPrds.CurrentOrdinal < OrdPrds.Count   
       AND [Measures].[Reseller Order Quantity] =   
          ( [Measures].[Reseller Order Quantity]  
            , OrdPrds.Item  
               (OrdPrds.CurrentOrdinal  
               )  
            )  
         )  
         OR (OrdPrds.CurrentOrdinal > 1   
            AND [Measures].[Reseller Order Quantity] =   
               ([Measures].[Reseller Order Quantity]  
               , OrdPrds.Item  
                  (OrdPrds.CurrentOrdinal-2)  
                )  
             )  
          ))  
       )  
SELECT {[Measures].[PrdTies]} ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
