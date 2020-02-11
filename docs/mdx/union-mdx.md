---
title: Union (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 170e3764795e1bb6db3fc9589ecf1fe486078633
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097300"
---
# <a name="union--mdx"></a>Union (MDX)


  Retourne un jeu produit par l'union de deux jeux, en conservant éventuellement les membres en double.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Standard syntax  
Union(Set_Expression1, Set_Expression2 [,...n][, ALL])  
  
Alternate syntax 1  
Set_Expression1 + Set_Expression2 [+...n]  
  
Alternate syntax 2  
{Set_Expression1 , Set_Expression2 [,...n]}  
```  
  
## <a name="arguments"></a>Arguments  
 *Définir l’expression 1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Définir l’expression 2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Cette fonction retourne l’Union de deux ou plusieurs jeux spécifiés. Avec la syntaxe standard et l’autre syntaxe 1, les doublons sont éliminés par défaut. Avec la syntaxe standard, l’utilisation de l’indicateur **All** conserve les doublons dans le jeu joint. Les doublons sont supprimés de la fin du jeu. Avec la syntaxe alternative 2, les doublons sont toujours conservés.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent le comportement de la fonction **Union** à l’aide de chaque syntaxe.  
  
### <a name="standard-syntax-duplicates-eliminated"></a>Syntaxe standard, doublons supprimés  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="standard-syntax-duplicates-retained"></a>Syntaxe standard, doublons conservés  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   , ALL  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-1-duplicates-eliminated"></a>Syntaxe alternative 1, doublons supprimés  
  
```  
SELECT   
   [Date].[Calendar Year].children   
   + {[Date].[Calendar Year].[CY 2002]}   
   + {[Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-2-duplicates-retained"></a>Syntaxe alternative 2, doublons conservés  
  
```  
SELECT   
   {[Date].[Calendar Year].children  
   , [Date].[Calendar Year].[CY 2002]  
   , [Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [+ &#40;Union&#41; &#40;MDX&#41;](../mdx/union-mdx-operator-reference.md)   
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
