---
title: TupleToStr (MDX) | Documents Microsoft
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
- TUPLETOSTR
dev_langs:
- kbMDX
helpviewer_keywords:
- TupletoStr function
ms.assetid: ad12347c-d1c4-4d8b-a910-3116bd6b68e0
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 9a3a17d50ac15f7f59b41881d95a6e0c5fc2a3a6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="tupletostr-mdx"></a>TupleToStr (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne une chaîne au format MDX (Multidimensional Expressions) qui correspond à un tuple spécifique.  
  
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
 L'exemple ci-dessous retourne la chaîne ([Date].[Calendar Year].&[2001],[Geography].[Geography].[Country].&[United States]) :  
  
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
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
