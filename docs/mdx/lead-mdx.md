---
title: "Entraîner (MDX) | Documents Microsoft"
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
- LEAD
dev_langs:
- kbMDX
helpviewer_keywords:
- Lead function
ms.assetid: f3250092-7b98-40b5-8dca-77e3b50734a0
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 127c84f38fe85453fa3da7ae2b1c9752b05b6ba7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="lead-mdx"></a>Lead (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne un membre correspondant à un nombre spécifique de positions après un membre spécifié le long du niveau du membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Index*  
 Expression numérique valide qui spécifie un nombre de positions de membres.  
  
## <a name="remarks"></a>Notes  
 Les positions des membres dans un niveau sont déterminées en fonction de l'ordre naturel de la hiérarchie d'attribut. La numérotation des positions commence à zéro.  
  
 Si le nombre placé en premier est zéro (0), la **entraîner** fonction retourne le membre spécifié.  
  
 Si le nombre placé en premier est négatif, le **entraîner** fonction retourne un membre précédent.  
  
 `Lead(1)`équivaut à la [NextMember](../mdx/nextmember-mdx.md) (fonction). `Lead(-1)`équivaut à la [PrevMember](../mdx/prevmember-mdx.md) (fonction).  
  
 Le **entraîner** fonction est similaire à la [Lag](../mdx/lag-mdx.md) de fonction, à ceci près que le **Lag** fonction recherche dans la direction opposée à la **entraîner** (fonction). Ce qui signifie que `Lead(n)` est équivalent à `Lag(-n)`.  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

