---
title: IsAncestor (MDX) | Documents Microsoft
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
- ISANCESTOR
dev_langs:
- kbMDX
helpviewer_keywords:
- IsAncestor function
ms.assetid: 49d2fcdf-8d9a-4c79-bd00-4910ea149141
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2f8b226312442d5fc7b287781a505af410f050db
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne une valeur indiquant si un membre spécifié est un ancêtre d'un autre membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Arguments  
 *Expression_membre1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Expression_membre2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes   
 Le **IsAncestor** fonction renvoie **true** si le premier membre spécifié est un ancêtre du deuxième membre spécifié. Sinon, la fonction retourne **false**.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant renvoie **true** si [Date]. [ Fiscal]. CurrentMember est un ancêtre de January 2003 :  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Ancêtre &#40; MDX &#41;](../mdx/ancestor-mdx.md)   
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
