---
title: NextMember (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4535b837d81db10f41f1445a7051678ce4fdd688
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742178"
---
# <a name="nextmember-mdx"></a>NextMember (MDX)


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
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne le membre August 2001 (août 2001) en tant que membre suivant du membre July 2001 (juillet 2001).  
  
```  
SELECT [Date].[Calendar].[Month].[July 2001].NextMember ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
