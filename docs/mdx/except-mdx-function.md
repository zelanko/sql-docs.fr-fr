---
title: À l’exception (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 03d9b5140eb0cbf9d868e43c65213efe917994a9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739998"
---
# <a name="except-mdx-function"></a>EXCEPT (fonction) (MDX)


  Évalue deux jeux et supprime les tuples du premier jeu qui existent également dans le deuxième jeu, en conservant éventuellement les doublons.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Except(Set_Expression1, Set_Expression2 [, ALL ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Si **tous les** est spécifiée, la fonction conserve les doublons trouvés dans le premier jeu ; les doublons trouvés dans le deuxième jeu va être supprimés. Les membres sont retournés dans l'ordre de leur apparition dans le premier jeu.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cette fonction.  
  
```  
   //This query shows the quantity of orders for all products,  
   //with the exception of Components, which are not  
   //sold.  
SELECT   
   [Date].[Month of Year].Children  ON COLUMNS,  
   Except  
      ([Product].[Product Categories].[All].Children ,  
         {[Product].[Product Categories].[Components]}  
      ) ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   ([Measures].[Order Quantity])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [- &#40;Sauf&#41; &#40;MDX&#41;](../mdx/except-mdx-operator.md)   
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
