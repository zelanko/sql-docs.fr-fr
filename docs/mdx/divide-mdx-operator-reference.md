---
title: (Division) (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: /
dev_langs: kbMDX
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 42b7d3ea-234d-41b3-a849-f457be6d7972
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ecc1808f1a0bccc6fc5d14895f7a8bc1cca9dafb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="divide---mdx-operator-reference"></a>Division - référence des opérateurs MDX
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exécute une opération arithmétique qui divise un nombre par un autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Dividende*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur numérique.  
  
 *Diviseur*  
 Expression MDX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur dont le type de données du paramètre possède la priorité la plus élevée.  
  
## <a name="remarks"></a>Notes  
 La valeur réelle retournée par le **/ (division)** opérateur représente le quotient de la première expression divisée par la seconde expression.  
  
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si *diviseur* prend une valeur null, l’opérateur génère une erreur. Si les deux *diviseur* et *dividende* évaluer à une valeur null, l’opérateur retourne une valeur null.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
-- This query returns the freight cost per user,  
-- for products, averaged by month.   
With Member [Measures].[Freight Per Customer] as  
    [Measures].[Internet Freight Cost]  
    /   
    [Measures].[Customer Count]  
  
SELECT   
    [Ship Date].[Calendar].[Calendar Year] Members ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
 Diviser une valeur non nulle ou non NULL par zéro ou NULL retourne la valeur Infinity qui est affichée dans les résultats de la requête comme valeur "1.#INF". Dans la plupart des cas, vous devez vérifier la présence d'une division par zéro pour éviter cette situation. L'exemple suivant illustre les opérations suivantes :  
  
 `//Returns 1.#INF when Internet Sales Amount is zero or null`  
  
 `Member [Measures].[Reseller to Internet Ratio] AS`  
  
 `[Measures].[Reseller Sales Amount]`  
  
 `/`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `//Traps the division by zero scenario and returns null instead of 1.#INF`  
  
 `Member [Measures].[Reseller to Internet Ratio With Error Handling] AS`  
  
 `IIF([Measures].[Internet Sales Amount]=0, NULL,`  
  
 `[Measures].[Reseller Sales Amount]`  
  
 `/`  
  
 `[Measures].[Internet Sales Amount])`  
  
 `SELECT`  
  
 `{[Measures].[Reseller to Internet Ratio],[Measures].[Reseller to Internet Ratio With Error Handling]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 `WHERE([Date].[Calendar].[Calendar Year].&[2001])`  
  
## <a name="see-also"></a>Voir aussi  
 [IIf &#40; MDX &#41;](../mdx/iif-mdx.md)   
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
