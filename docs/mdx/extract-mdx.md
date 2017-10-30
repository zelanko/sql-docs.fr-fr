---
title: Extraire (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXTRACT
dev_langs:
- kbMDX
helpviewer_keywords:
- Extract function
ms.assetid: c0d27d31-e36e-4b7f-bb86-1e4707351392
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0e18c7ac7dcf37ce41bc7917c9d7170a815c1f58
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="extract-mdx"></a>Extract (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne un jeu de tuples à partir d'éléments de hiérarchie extraits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Extract(Set_Expression, Hierarchy_Expression1 [,Hierarchy_Expression2, ...n] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Hierarchy_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
 *Hierarchy_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
## <a name="remarks"></a>Notes  
 Le **extraire** fonction retourne un jeu composé de tuples à partir d’éléments de hiérarchie extraits. Pour chaque tuple du jeu spécifié, les membres des hiérarchies concernées sont extraits vers de nouveaux tuples dans l'ensemble de résultats. Cette fonction supprime toujours les tuples dupliqués.  
  
 Le **extraire** fonction effectue l’action inverse de la [Crossjoin](../mdx/crossjoin-mdx.md) (fonction).  
  
## <a name="examples"></a>Exemples  
 La requête suivante montre comment utiliser le **extraire** fonction sur un jeu de tuples retournés par le **NonEmpty** fonction :  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

