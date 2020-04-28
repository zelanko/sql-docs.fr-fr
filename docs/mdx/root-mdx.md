---
title: Racine (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: be687d5cbfd4fdbb706ef5c10778a4f3e3f93197
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68037037"
---
# <a name="root-mdx"></a>Root (MDX)


  Retourne un tuple qui se compose de **tous** les membres de chaque hiérarchie d’attribut dans l’étendue actuelle d’un cube, d’une dimension ou d’un tuple. Pour plus d’informations sur l’étendue, consultez [instruction Scope &#40;&#41;MDX ](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Si une hiérarchie d’attribut n’a pas de membre **All** , le tuple contient le membre par défaut de cette hiérarchie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Cube syntax  
Root ()  
Dimension syntax  
Root( Dimension_Name )  
Tuple syntax  
Root( Tuple_Expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *Dimension_Name*  
 Expression de chaîne valide qui précise le nom d'une dimension.  
  
 *Tuple_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un tuple.  
  
## <a name="remarks"></a>Notes  
 Si ni un nom de dimension, ni une expression de tuple n’est spécifié, la fonction **root** retourne un tuple qui contient le membre **All** (ou le membre par défaut si le membre **All** n’existe pas) à partir de chaque hiérarchie d’attribut dans le cube. L'ordre des membres dans le tuple dépend de la séquence dans laquelle les hiérarchies d'attributs sont définies au sein du cube.  
  
 Si un nom de dimension est spécifié, la fonction **root** retourne un tuple qui contient le membre **All** (ou le membre par défaut si le membre **All** n’existe pas) de chaque hiérarchie d’attribut dans la dimension spécifiée en fonction du contexte du membre actuel. L'ordre des membres dans le tuple dépend de la séquence dans laquelle les hiérarchies d'attributs sont définies au sein de la dimension.  
  
> [!NOTE]  
>  Si un nom de hiérarchie est spécifié, la fonction **Tuple** choisit le nom de la dimension à partir du nom de la hiérarchie spécifié.  
  
 Si une expression de tuple est spécifiée, la fonction **racine** retourne un tuple qui contient l’intersection du tuple spécifié et **tous** les membres de tous les autres attributs de dimension qui ne sont pas explicitement inclus dans le tuple spécifié.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne le tuple contenant le membre **All** (ou la valeur par défaut si le membre **All** n’existe pas) de chaque hiérarchie dans le cube Adventure Works.  
  
```  
SELECT Root()ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant retourne le tuple contenant le membre **All** (ou la valeur par défaut si le membre **All** n’existe pas) de chaque hiérarchie de la dimension Date dans le cube Adventure Works et la valeur du membre spécifié de la dimension Measures qui entre en intersection avec ces membres par défaut.  
  
```  
SELECT Root([Date]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
 L’exemple suivant retourne le tuple contenant le membre de tuple spécifié (1er juillet 2001, ainsi que le membre **All** (ou la valeur par défaut si le membre **All** n’existe pas) à partir de chaque hiérarchie non spécifiée dans la dimension Date cube Adventure Works, ainsi que la valeur du membre spécifié de la dimension Measure qui croise ces membres.  
  
```  
SELECT Root([Date].[July 1, 2001]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
