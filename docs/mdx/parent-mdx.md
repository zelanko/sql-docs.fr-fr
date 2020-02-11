---
title: Parent (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9449c81e9f8e8de0c21d96062337e91b2f56398d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037196"
---
# <a name="parent-mdx"></a>Parent (MDX)


  Retourne le parent d'un membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Parent   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 La fonction **parente** retourne le membre parent du membre spécifié.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants retournent le parent du membre July 1, 2001. Le premier exemple définit ce membre dans le contexte de la hiérarchie d'attribut Date et retourne le membre All Periods.  
  
```  
SELECT [Date].[Date].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
 L'exemple ci-dessous spécifie le membre July 1, 2001 dans le contexte de la hiérarchie Calendar.  
  
```  
SELECT [Date].[Calendar].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
