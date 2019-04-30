---
title: Dimension (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cee82f3baa95df1d8636e314bfbb0798efe9527a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63248217"
---
# <a name="dimension-mdx"></a>Dimension (MDX)


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
  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
### <a name="examples"></a>Exemples  
 L’exemple suivant utilise le **Dimension** fonction, conjointement avec le **nom** (fonction), pour retourner le nom de la hiérarchie du membre spécifié.  
  
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
  
 L’exemple suivant utilise le **Dimension** fonction, conjointement avec le **membres** et **nombre** fonctions pour retourner le nombre de membres dans la hiérarchie contenant le membre spécifié.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40;niveaux de hiérarchie&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Count &#40;Set&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [Levels &#40;MDX&#41;](../mdx/levels-mdx.md)   
 [Membres &#40;définir&#41; &#40;MDX&#41;](../mdx/members-set-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
