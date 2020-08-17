---
description: Lead (MDX)
title: Lead (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ca78bdeca6103758d5d102ed8b85eb00b3138e18
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387325"
---
# <a name="lead-mdx"></a>Lead (MDX)


  Retourne un membre correspondant à un nombre spécifique de positions après un membre spécifié le long du niveau du membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Index*  
 Expression numérique valide qui spécifie un nombre de positions de membres.  
  
## <a name="remarks"></a>Notes  
 Les positions des membres dans un niveau sont déterminées en fonction de l'ordre naturel de la hiérarchie d'attribut. La numérotation des positions commence à zéro.  
  
 Si le prospect spécifié est égal à zéro (0), la fonction **Lead** retourne le membre spécifié.  
  
 Si le prospect spécifié est négatif, la fonction **Lead** retourne un membre antérieur.  
  
 `Lead(1)` équivaut à la fonction [NextMember](../mdx/nextmember-mdx.md) . `Lead(-1)` équivaut à la fonction [PrevMember](../mdx/prevmember-mdx.md) .  
  
 La fonction **Lead** est similaire à la fonction [lag](../mdx/lag-mdx.md) , sauf que la fonction **lag** regarde dans la direction opposée à la fonction **Lead** . Ce qui signifie que `Lead(n)` est équivalent à `Lag(-n)`.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-après retourne la valeur du mois de décembre 2001 :  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(-2) ON 0  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-après retourne la valeur du mois de mars 2002 :  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
