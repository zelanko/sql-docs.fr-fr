---
title: Root (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c2301f44cbdac4505bef95d590ce206c8b6b509
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63150236"
---
# <a name="root-mdx"></a>Root (MDX)


  Retourne un tuple qui se compose de la **tous les** membres de chaque hiérarchie d’attribut dans la portée actuelle dans un cube, une dimension ou un tuple. Pour plus d’informations sur l’étendue, consultez [instruction SCOPE &#40;MDX&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Si une hiérarchie d’attribut n’est pas un **tous les** membre, tuple contient le membre par défaut pour cette hiérarchie.  
  
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
 Si un nom de dimension, ni une expression de tuple est spécifiée, le **racine** fonction retourne un tuple qui contient le **tous les** membre (ou le membre par défaut si le **tous les** membre n’existe pas) de chaque hiérarchie d’attribut dans le cube. L'ordre des membres dans le tuple dépend de la séquence dans laquelle les hiérarchies d'attributs sont définies au sein du cube.  
  
 Si un nom de dimension est spécifié, le **racine** fonction retourne un tuple qui contient le **tous les** membre (ou le membre par défaut si le **tous les** membre n’existe pas) à partir de chaque hiérarchie d’attribut dans la dimension spécifiée en fonction du contexte du membre actuel. L'ordre des membres dans le tuple dépend de la séquence dans laquelle les hiérarchies d'attributs sont définies au sein de la dimension.  
  
> [!NOTE]  
>  Si un nom de la hiérarchie est spécifié, le **Tuple** fonction utilisera le nom de dimension à partir du nom de hiérarchie spécifié.  
  
 Si une expression de tuple est spécifiée, le **racine** fonction retourne un tuple qui contient l’intersection du tuple spécifié et le **tous les** membres de tous les autres attributs de dimension non explicitement inclus dans le tuple spécifié.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne le tuple contenant le **tous les** membre (ou la valeur par défaut si le **tous les** membre n’existe pas) de chaque hiérarchie dans le cube Adventure Works.  
  
```  
SELECT Root()ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant retourne le tuple contenant le **tous les** membre (ou la valeur par défaut si le **tous les** membre n’existe pas) de chaque hiérarchie dans la dimension Date dans le cube Adventure Works et la valeur de le membre spécifié de la dimension de mesures située à l’intersection de ces membres par défaut.  
  
```  
SELECT Root([Date]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
 L’exemple suivant retourne le tuple contenant le membre du tuple spécifié (le 1er juillet 2001 avec le **tous les** membre (ou la valeur par défaut si le **tous les** membre n’existe pas) de chaque hiérarchie non spécifié dans la Date dimension de cube Adventure Works et la valeur du membre spécifié de la dimension de mesures située à l’intersection de ces membres.  
  
```  
SELECT Root([Date].[July 1, 2001]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
