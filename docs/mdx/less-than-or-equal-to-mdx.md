---
title: '&lt;= (Inférieur ou égal à) (MDX) | Microsoft Docs'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 00021ea9c23de80f6b025963543af2cf4be2f572
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905682"
---
# <a name="lt-less-than-or-equal-to-mdx"></a>&lt;= (Inférieur ou égal à) (MDX)


  Exécute une opération de comparaison qui détermine si la valeur d'une expression MDX (Multidimensional Expressions) est inférieure ou égale à celle d'une autre expression MDX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MDX_Expression <= MDX_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *MDX_Expression*  
 Expression MDX valide.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne basée sur les conditions suivantes :  
  
-   Si**les** deux paramètres sont non null, et si le premier paramètre a une valeur qui est inférieure ou égale à la valeur du deuxième paramètre.  
  
-   f**false** si les deux paramètres sont non null, et si le premier paramètre a une valeur supérieure à la valeur du deuxième paramètre.  
  
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
 [Référence des opérateurs MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)  
  
  
