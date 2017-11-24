---
title: "&lt;= (Inférieur ou égal à) (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <=
dev_langs: kbMDX
helpviewer_keywords:
- <= (less than or equal to operator)
- less than or equal to operator (<=)
ms.assetid: 6c805c68-cf9d-48ca-a00b-2ef9ade89b0a
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a30d825b9e823400da8b77b9a7b2a77f9d5012a3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="lt-less-than-or-equal-to-mdx"></a>&lt;= (Inférieur ou égal à) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exécute une opération de comparaison qui détermine si la valeur d'une expression MDX (Multidimensional Expressions) est inférieure ou égale à celle d'une autre expression MDX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MDX_Expression <= MDX_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *MDX_Expression*  
 Expression MDX valide.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur booléenne basée sur les conditions suivantes :  
  
-   t**rue** si les deux paramètres sont non null et que le premier paramètre a une valeur qui est soit inférieure ou égale à la valeur du second paramètre.  
  
-   f**alse** si les deux paramètres sont non null et que le premier paramètre a une valeur qui dépasse la valeur du second paramètre.  
  
-   NULL si l'un ou l'autre ou les deux paramètres ont une valeur NULL.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for Australia where the GPM is less than or equal to 30%.  
With Member [Measures].[LowGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] <= .5,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT   
NON EMPTY [Sales Territory].[Sales Territory Country].[Australia] ON 0,  
    NON EMPTY [Product].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[LowGPM])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
