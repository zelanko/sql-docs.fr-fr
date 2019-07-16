---
title: '&gt; (Supérieur à) (MDX) | Microsoft Docs'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: bb4f04e623096857cce9dd27f0cddc77f6a59798
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67906036"
---
# <a name="gt-greater-than-mdx"></a>&gt; (Supérieur à) (MDX)


  Exécute une opération de comparaison qui détermine si la valeur d'une expression MDX est supérieure à celle d'une autre expression MDX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MDX_Expression > MDX_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *MDX_Expression*  
 Expression MDX valide.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne basée sur les conditions suivantes :  
  
-   **true** si les deux paramètres sont non null et que le premier paramètre a une valeur qui est supérieure à la valeur du second paramètre.  
  
-   **false** si les deux paramètres sont non null et que le premier paramètre a une valeur qui est égale ou inférieure à la valeur du second paramètre.  
  
-   NULL si l'un ou l'autre ou les deux paramètres ont une valeur NULL.  
  
## <a name="examples"></a>Exemples  
 L'exemple de requête ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for Australia where the GPM is more than 50%.  
With Member [Measures].[HighGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] > .5,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT   
NON EMPTY [Sales Territory].[Sales Territory Country].[Australia] ON 0,  
    NON EMPTY [Product].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[HighGPM])  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
