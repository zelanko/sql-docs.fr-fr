---
title: Décalage (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c7e95af96249b64f86bb1466283e8a1a38a32d90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905776"
---
# <a name="lag-mdx"></a>Lag (MDX)


  Retourne le membre qui est un nombre spécifié de positions avant un membre spécifié au niveau du membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Lag(Index)   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Évaluer*  
 Expression numérique valide qui spécifie le nombre de positions de membres à décaler.  
  
## <a name="remarks"></a>Notes  
 Les positions des membres dans un niveau sont déterminées en fonction de l'ordre naturel de la hiérarchie d'attribut. La numérotation des positions commence à zéro.  
  
 Si le décalage spécifié est égal à zéro, la fonction **lag** retourne le membre spécifié lui-même.  
  
 Si le décalage spécifié est négatif, la fonction **lag** retourne un membre suivant.  
  
 `Lag(1)`équivaut à la fonction [PrevMember](../mdx/prevmember-mdx.md) . `Lag(-1)`équivaut à la fonction [NextMember](../mdx/nextmember-mdx.md) .  
  
 La fonction **lag** est similaire à la fonction [Lead](../mdx/lead-mdx.md) , sauf que la fonction **Lead** regarde dans la direction opposée à la fonction **lag** . Ce qui signifie que `Lag(n)` est équivalent à `Lead(-n)`.  
  
## <a name="example"></a>Exemple  
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
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
