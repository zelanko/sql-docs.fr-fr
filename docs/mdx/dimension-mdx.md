---
title: Dimension (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Dimension
dev_langs: kbMDX
helpviewer_keywords: Dimension function
ms.assetid: 0e3ce539-1d34-45ca-8342-67796e11b730
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 74c5beec4459c1d261a1850b9888a6a0906e9900
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="dimension-mdx"></a>Dimension (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la hiérarchie qui contient un membre, un niveau ou une hiérarchie spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.Dimension  
  
Level syntax  
Level_Expression.Dimension  
  
Member syntax  
Member_Expression.Dimension  
  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
### <a name="examples"></a>Exemples  
 L’exemple suivant utilise le **Dimension** fonction, conjointement avec la **nom** pour retourner le nom de la hiérarchie du membre spécifié.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Name  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 L'exemple ci-dessous utilise conjointement la fonction Dimension avec les fonctions Levels et Count pour retourner le nombre de niveaux dans la hiérarchie contenant le membre spécifié.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant utilise le **Dimension** fonction, conjointement avec la **membres** et **nombre** fonctions, pour retourner le nombre de membres dans la hiérarchie contenant le membre spécifié.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40; Niveaux de hiérarchie &#41; &#40; MDX &#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Nombre &#40; Définir le &#41; &#40; MDX &#41;](../mdx/count-set-mdx.md)   
 [Niveaux &#40; MDX &#41;](../mdx/levels-mdx.md)   
 [Les membres &#40; Définir le &#41; &#40; MDX &#41;](../mdx/members-set-mdx.md)   
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
