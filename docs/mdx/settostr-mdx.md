---
title: SetToStr (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3965c3cc8ea2a2f2de292ca0c75e49c957e04f02
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036972"
---
# <a name="settostr-mdx"></a>SetToStr (MDX)


  Retourne une chaîne au format MDX correspondant au jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Cette fonction permet de transférer une représentation de chaîne d'un jeu vers une fonction externe à des fins d'analyse. La chaîne retournée est placée entre accolades {}, avec chaque élément du jeu séparé par une virgule.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne une chaîne contenant tous les membres de la hiérarchie d'attribut Geography.Country.  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
