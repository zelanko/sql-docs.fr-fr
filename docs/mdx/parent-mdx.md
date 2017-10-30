---
title: Parent (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARENT
dev_langs:
- kbMDX
helpviewer_keywords:
- Parent function
ms.assetid: 7be9b172-4241-4618-bdba-53cde8badd9b
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 50a7c9b5df87a716db1ca5f64b1351e882d7a05d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="parent-mdx"></a>Parent (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le parent d'un membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Parent   
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Le **Parent** fonction retourne le membre parent du membre spécifié.  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

