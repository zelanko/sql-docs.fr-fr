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
ms.openlocfilehash: 58bee93a4cef37a8a5a71211b292a16392687f12
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67999960"
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
 L’exemple suivant utilise la fonction **dimension** , conjointement avec la fonction **Name** , pour retourner le nom de la hiérarchie du membre spécifié.  
  
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
  
 L’exemple suivant utilise la fonction **dimension** , conjointement avec les **membres** et les fonctions **Count** , pour retourner le nombre de membres dans la hiérarchie contenant le membre spécifié.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40;niveaux de hiérarchie&#41; &#40;&#41;MDX](../mdx/count-hierarchy-levels-mdx.md)   
 [Nombre &#40;défini&#41; &#40;&#41;MDX](../mdx/count-set-mdx.md)   
 [Niveaux &#40;&#41;MDX](../mdx/levels-mdx.md)   
 [Membres &#40;définir&#41; &#40;&#41;MDX](../mdx/members-set-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
