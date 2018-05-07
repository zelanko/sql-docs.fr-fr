---
title: '- (Soustraction) (MDX) | Documents Microsoft'
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '-'
dev_langs:
- kbMDX
helpviewer_keywords:
- '- (subtract)'
- subtract operator (-)
ms.assetid: 56e610a1-efbd-4c11-bd7c-bf20a6553e57
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 4cf3b463887f6b5a7b2f801ee2cbd702624929f6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="--subtract-mdx"></a>- (Soustraction) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Exécute une opération arithmétique qui soustrait un nombre d'un autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric_Expression - Numeric_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Numeric_expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur dont le type de données du paramètre possède la priorité la plus élevée.  
  
## <a name="remarks"></a>Notes  
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si une expression s'évalue à NULL, l'opérateur retourne le résultat de l'expression non NULL.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
-- This member returns the increase or decrease  
-- in gross profit margin over a month.  
WITH MEMBER [Measures].[GPM Delta] AS  
 (  
(Measures.[Gross Profit Margin]) -   
([Date].[Calendar].CurrentMember.PrevMember,   
Measures.[Gross Profit Margin])  
  ), FORMAT_STRING = 'Percent'  
  
SELECT   
DESCENDANTS(  
[Date].[Calendar].[Calendar Year].&[2002],   
[Date].[Calendar].[Month]) ON 0,  
[Product].[Category].[Category].Members ON 1  
FROM  
[Adventure Works]  
WHERE  
([Measures].[GPM Delta])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
