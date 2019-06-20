---
title: TupleToStr (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5f07e71e5b8314320f76be4496744da5a9d9e81a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208468"
---
# <a name="tupletostr-mdx"></a>TupleToStr (MDX)


  Retourne une chaîne au format d’expression multidimensionnelle MDX qui correspond à un tuple spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TupleToStr(Tuple_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Tuple_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un tuple.  
  
## <a name="remarks"></a>Notes  
 Cette fonction permet de transférer une représentation de chaîne d'un tuple vers une fonction externe à des fins d'analyse. La chaîne retournée est placée entre accolades {} et chaque membre, si plusieurs sont expressément défini dans le tuple, séparée par une virgule.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne la chaîne ([Date]. [ Calendar Year]. & [2001], [Geography]. [Geography]. [Country]. & [United States]) :  
  
```  
WITH MEMBER Measures.x AS TupleToStr   
   (   
      ([Date].[Calendar Year].&[2001]  
         , [Geography].[Geography].[Country].&[United States]  
      )  
   )     
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 L'exemple ci-dessous retourne la même chaîne que dans l'exemple précédent.  
  
```  
WITH SET s AS   
   {  
      ([Date].[Calendar Year].&[2001],  
         [Geography].[Geography].[Country].&[United States]  
      )   
   }  
MEMBER Measures.x AS TupleToStr ( s.Item(0) )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
