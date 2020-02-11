---
title: FirstChild (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c1bd2f37304131b881d49aaa874eaed13530fc0e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032075"
---
# <a name="firstchild-mdx"></a>FirstChild (MDX)


  Retourne le premier enfant d'un membre spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.FirstChild   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
### <a name="example"></a>Exemple  
 La requête suivante retourne le premier enfant de l'année fiscale 2003 dans la hiérarchie Fiscal, ce qui correspond au premier semestre de cette même année.  
  
```  
SELECT [Date].[Fiscal].[Fiscal Year].&[2003].FirstChild ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#41;MDX &#40;MDX](../mdx/lastchild-mdx.md)   
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
