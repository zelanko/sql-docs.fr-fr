---
title: Distinct (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DISTINCT
dev_langs:
- kbMDX
helpviewer_keywords:
- Distinct function
ms.assetid: d648f320-73dd-4a23-96e9-d72e93a64c0d
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4d489a5909ac889a4d15974541c69c7eb8c5a516
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="distinct-mdx"></a>Distinct (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Évalue un jeu spécifié, supprime les tuples dupliqués du jeu et retourne le jeu obtenu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Distinct(Set_Expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Si le **Distinct** fonction recherche des doublons de tuples dans le jeu spécifié, la fonction conserve uniquement la première instance du tuple dupliqué tout en conservant l’ordre du jeu.  
  
## <a name="examples"></a>Exemples  
 L'exemple de requête suivant illustre comment utiliser la fonction Distinct avec un jeu nommé, et comment l'utiliser avec la fonction Count pour rechercher le nombre de tuples distincts dans un jeu :  
  
 `WITH SET MySet AS`  
  
 `{[Customer].[Customer Geography].[Country].&[Australia],[Customer].[Customer Geography].[Country].&[Australia],`  
  
 `[Customer].[Customer Geography].[Country].&[Canada],[Customer].[Customer Geography].[Country].&[France],`  
  
 `[Customer].[Customer Geography].[Country].&[United Kingdom],[Customer].[Customer Geography].[Country].&[United Kingdom]}`  
  
 `MEMBER MEASURES.SETCOUNT AS`  
  
 `COUNT(MySet)`  
  
 `MEMBER MEASURES.SETDISTINCTCOUNT AS`  
  
 `COUNT(DISTINCT(MySet))`  
  
 `SELECT {MEASURES.SETCOUNT, MEASURES.SETDISTINCTCOUNT} ON 0,`  
  
 `DISTINCT(MySet) ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

