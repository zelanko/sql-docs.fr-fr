---
title: Racine (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Root
dev_langs: kbMDX
helpviewer_keywords: Root function
ms.assetid: f6c42e87-5a52-4e43-9dd1-ca757f2db79c
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d9ff454cb9953c084a75e1bf3621ff45d047d00d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="root-mdx"></a>Root (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne un tuple qui se compose de la **tous les** membres de chaque hiérarchie d’attribut dans la portée actuelle dans un cube, une dimension ou un tuple. Pour plus d’informations sur l’étendue, consultez [instruction SCOPE &#40; MDX &#41; ](../mdx/mdx-scripting-scope.md).  
  
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
 Si un nom de dimension, ni une expression de tuple est spécifiée, la **racine** fonction retourne un tuple qui contient le **tous les** membre (ou le membre par défaut si le **tous les** membre n’existe pas) de chaque hiérarchie d’attribut dans le cube. L'ordre des membres dans le tuple dépend de la séquence dans laquelle les hiérarchies d'attributs sont définies au sein du cube.  
  
 Si un nom de dimension est spécifié, le **racine** fonction retourne un tuple qui contient le **tous les** membre (ou le membre par défaut si le **tous les** membre n’existe pas) de chaque hiérarchie d’attribut dans la dimension spécifiée en fonction du contexte du membre actuel. L'ordre des membres dans le tuple dépend de la séquence dans laquelle les hiérarchies d'attributs sont définies au sein de la dimension.  
  
> [!NOTE]  
>  Si un nom de hiérarchie est spécifié, la **Tuple** fonction choisira le nom de dimension à partir du nom de la hiérarchie spécifié.  
  
 Si une expression de tuple est spécifiée, la **racine** fonction retourne un tuple qui contient l’intersection du tuple spécifié et la **tous les** membres de tous les autres attributs de dimension ne sont pas explicitement inclus dans le tuple spécifié.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne le tuple contenant le **tous les** membre (ou la valeur par défaut si le **tous les** membre n’existe pas) de chaque hiérarchie dans le cube Adventure Works.  
  
```  
SELECT Root()ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant retourne le tuple contenant le **tous les** membre (ou la valeur par défaut si le **tous les** membre n’existe pas) de chaque hiérarchie dans la dimension Date dans le cube Adventure Works et la valeur du membre spécifié de la dimension de mesures située à l’intersection de ces membres par défaut.  
  
```  
SELECT Root([Date]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
 L’exemple suivant retourne le tuple contenant le membre du tuple spécifié (1er juillet 2001, avec la **tous les** membre (ou la valeur par défaut si le **tous les** membre n’existe pas) de chaque hiérarchie non spécifiée dans la Date de dimension de cube Adventure Works et la valeur du membre spécifié de la dimension de mesures située à l’intersection de ces membres.  
  
```  
SELECT Root([Date].[July 1, 2001]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
