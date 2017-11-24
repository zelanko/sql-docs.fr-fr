---
title: SetToStr (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SETTOSTR
dev_langs: kbMDX
helpviewer_keywords: SetToStr function
ms.assetid: b761e002-26cd-460e-b424-fb8e306746fa
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: eaa3a119c2d3e8465919234bcfa50ecfacf2aa15
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="settostr-mdx"></a>SetToStr (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une chaîne au format MDX correspondant au jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Cette fonction permet de transférer une représentation de chaîne d'un jeu vers une fonction externe à des fins d'analyse. La chaîne qui est retournée apparaît entre accolades {}, avec chaque élément du jeu séparé par une virgule.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne une chaîne contenant tous les membres de la hiérarchie d'attribut Geography.Country.  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
