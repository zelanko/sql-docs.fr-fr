---
title: NextMember (MDX) | Documents Microsoft
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
- NEXTMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- NextMember function
ms.assetid: f67be3d0-082e-4bec-92e4-ba6ff33af303
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f4ee6b32df0c0aef1de919448baefac7e93b88a1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="nextmember-mdx"></a>NextMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne le membre suivant dans le niveau qui contient le membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.NextMember   
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes   
 Le **NextMember** fonction retourne le membre suivant dans le même niveau, qui contient le membre spécifié.  
  
## <a name="example"></a> Exemple  
 L'exemple ci-dessous retourne le membre August 2001 (août 2001) en tant que membre suivant du membre July 2001 (juillet 2001).  
  
```  
SELECT [Date].[Calendar].[Month].[July 2001].NextMember ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
