---
title: Lag (MDX) | Documents Microsoft
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
- LAG
dev_langs:
- kbMDX
helpviewer_keywords:
- Lag function
ms.assetid: 08c704ea-35d8-44ee-abe5-93bd24b99906
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a219e0b8455ff3a66d20a8c670bb8675481498e4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="lag-mdx"></a>Lag (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne le membre qui est un nombre spécifié de positions avant un membre spécifié au niveau du membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Lag(Index)   
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Index*  
 Expression numérique valide qui spécifie le nombre de positions de membres à décaler.  
  
## <a name="remarks"></a>Notes   
 Les positions des membres dans un niveau sont déterminées en fonction de l'ordre naturel de la hiérarchie d'attribut. La numérotation des positions commence à zéro.  
  
 Si le décalage spécifié est égal à zéro, le **Lag** fonction retourne le membre spécifié lui-même.  
  
 Si le décalage spécifié est négatif, le **Lag** fonction retourne un membre suivant.  
  
 `Lag(1)`équivaut à la [PrevMember](../mdx/prevmember-mdx.md) (fonction). `Lag(-1)`équivaut à la [NextMember](../mdx/nextmember-mdx.md) (fonction).  
  
 Le **Lag** fonction est similaire à la [entraîner](../mdx/lead-mdx.md) de fonction, à ceci près que le **entraîner** fonction recherche dans la direction opposée à la **Lag** (fonction). Ce qui signifie que `Lag(n)` est équivalent à `Lead(-n)`.  
  
## <a name="example"></a> Exemple  
 L'exemple ci-après retourne la valeur du mois de décembre 2001 :  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(2) ON 0  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-après retourne la valeur du mois de mars 2002 :  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(-1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
