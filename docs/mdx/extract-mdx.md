---
title: Extraire (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 26edefab1a81aebaa9bf63e69e24067428266de1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67906039"
---
# <a name="extract-mdx"></a>Extract (MDX)


  Retourne un jeu de tuples à partir d'éléments de hiérarchie extraits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Extract(Set_Expression, Hierarchy_Expression1 [,Hierarchy_Expression2, ...n] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Hierarchy_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
 *Hierarchy_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
## <a name="remarks"></a>Notes  
 La fonction **extract** retourne un jeu qui se compose de tuples à partir des éléments de hiérarchie extraits. Pour chaque tuple du jeu spécifié, les membres des hiérarchies concernées sont extraits vers de nouveaux tuples dans l'ensemble de résultats. Cette fonction supprime toujours les tuples dupliqués.  
  
 La fonction **extract** effectue l’action inverse de la fonction [CrossJoin](../mdx/crossjoin-mdx.md) .  
  
## <a name="examples"></a>Exemples  
 La requête suivante montre comment utiliser la fonction **extract** sur un jeu de tuples retourné par la fonction non **vide** :  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `//Returns the distinct combinations of Customer and Date for all purchases`  
  
 `//of Bike Racks or Bike Stands`  
  
 `EXTRACT(`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `*`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `*`  
  
 `{[Product].[Product Categories].[Subcategory].&[26],[Product].[Product Categories].[Subcategory].&[27]}`  
  
 `*`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `)`  
  
 `,  [Customer].[Customer], [Date].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
