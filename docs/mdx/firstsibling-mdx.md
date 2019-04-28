---
title: FirstSibling (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1cb097e89a36eaa4d7ef68eca3b88aa6ca03d49a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62690421"
---
# <a name="firstsibling-mdx"></a>FirstSibling (MDX)


  Retourne le premier enfant du parent d'un membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.FirstSibling   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
### <a name="example"></a>Exemple  
 La requête suivante retourne le premier frère de l'année fiscale 2003 dans la hiérarchie Fiscal, soit l'année fiscale 2002.  
  
```  
SELECT [Date].[Fiscal].[Fiscal Year].&[2003].FirstSibling ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
