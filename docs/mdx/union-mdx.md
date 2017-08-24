---
title: Union (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- functions [MDX], Union
ms.assetid: cc083455-8b3b-46af-bb55-1e238376f162
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d68afa2f9c424a0bb745ad2feaf781923eac624a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="union--mdx"></a>Union (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 Cette fonction retourne l’union de deux ou plusieurs jeux spécifiés*.* Avec la syntaxe standard et la syntaxe alternative 1, les doublons sont éliminés par défaut. Avec la syntaxe standard, à l’aide de la **tous les** indicateur conserve les doublons dans le jeu joint. Les doublons sont supprimés de la fin du jeu. Avec la syntaxe alternative 2, les doublons sont toujours conservés.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent le comportement de la **Union** avec chaque syntaxe de fonction.  
  
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
 [+ &#40; Union &#41; &#40; MDX &#41;](../mdx/union-mdx-operator-reference.md)   
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

