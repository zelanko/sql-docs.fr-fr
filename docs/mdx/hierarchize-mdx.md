---
title: Hierarchize (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8ab2c866f201c53684c316282a143b4f672cb8e9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105433"
---
# <a name="hierarchize-mdx"></a>Hierarchize (MDX)


  Ordonne les membres d'un jeu en hiérachie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Hierarchize(Set_Expression [ , POST ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 La fonction **Hierarchize** organise les membres du jeu spécifié dans l’ordre hiérarchique. La fonction conserve toujours les doublons.  
  
-   Si l' **envoi** n’est pas spécifié, la fonction trie les membres d’un niveau dans leur ordre naturel. Leur ordre naturel est l'ordre par défaut des membres dans la hiérarchie lorsque aucune condition de tri n'est spécifiée. Les membres enfants suivent immédiatement leurs membres parents.  
  
-   Si la fonction de **publication** est spécifiée, la fonction **Hierarchize** trie les membres d’un niveau à l’aide d’un ordre de publication naturelle. En d'autres termes, les membres enfants précèdent leurs parents.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous remonte d'un niveau vers le membre Canada. La fonction **Hierarchize** est utilisée pour organiser les membres du jeu spécifié dans l’ordre hiérarchique, ce qui est requis par la fonction **DrillupMember** .  
  
```  
SELECT DrillUpMember   
   (  
      Hierarchize  
         (  
            {[Geography].[Geography].[Country].[Canada]  
            ,[Geography].[Geography].[Country].[United States]  
            ,[Geography].[Geography].[State-Province].[Alberta]  
            ,[Geography].[Geography].[State-Province].[Brunswick]  
            ,[Geography].[Geography].[State-Province].[Colorado]   
            }  
         ), {[Geography].[Geography].[Country].[United States]}  
   )  
ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant retourne la somme du `Measures.[Order Quantity]` membre, agrégée sur les neuf premiers mois de 2003 contenus dans la `Date` dimension, à partir du cube **Adventure Works** . La fonction **PeriodsToDate** définit les tuples dans le jeu sur lequel opère la fonction d’agrégation. La fonction **Hierarchize** organise les membres du jeu de membres spécifié à partir de la dimension Product dans l’ordre hiérarchique.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
