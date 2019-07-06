---
title: Union  (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe80d94be42a9ea953a5829de43bcab3cb30955f
ms.sourcegitcommit: d9c5b9ab3c282775ed61712892eeb3e150ccc808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67597380"
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
 *Expression d’ensemble 1*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Expression d’ensemble 2*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Cette fonction retourne l’union de deux ou plusieurs jeux spécifiés. Avec la syntaxe standard et la syntaxe alternative 1, les doublons sont éliminés par défaut. Avec la syntaxe standard, à l’aide de la **tous les** indicateur conserve les doublons dans le jeu joint. Les doublons sont supprimés de la fin du jeu. Avec la syntaxe alternative 2, les doublons sont toujours conservés.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants montrent le comportement de la **Union** avec chaque syntaxe de fonction.  
  
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
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
