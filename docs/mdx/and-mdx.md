---
title: ET (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 930fe19abe7b1d783b4c69ef54b9b2550a05d538
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017089"
---
# <a name="and-mdx"></a>AND (MDX)


  Effectue une conjonction logique sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur numérique.  
  
 *Expression2*  
 Expression MDX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne qui retourne true si les deux paramètres ont la valeur **true**; Sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 L’opérateur **and** traite les deux expressions comme des valeurs booléennes (zéro, 0, **false**; sinon, **true**) avant que l’opérateur effectue la conjonction logique. Le tableau suivant illustre la façon dont l’opérateur **and** effectue la conjonction logique.  
  
|*Expression1*|*Expression2*|Valeur de retour|  
|-------------------|-------------------|------------------|  
|**:**|**:**|**:**|  
|**:**|**fausses**|**fausses**|  
|**fausses**|**:**|**fausses**|  
|**fausses**|**fausses**|**fausses**|  
  
## <a name="example"></a>Exemple  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for clothing sales where the GPM is between 20% and 30%.  
With Member [Measures].[LowGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] <= .3 AND   
      [Measures].[Gross Profit Margin] >= .2,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT NON EMPTY  
    [Sales Territory].[Sales Territory Country].Members ON 0,  
    [Product].[Category].[Clothing] ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[LowGPM])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)  
  
  
