---
title: À l’exception (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- EXCEPT
dev_langs:
- kbMDX
helpviewer_keywords:
- Except function
ms.assetid: 5d832c82-1e6d-4308-9c26-7edb8afe11dd
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: a918ebbed1b43dae8ad8e8aacb634f3b37781163
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="except-mdx-function"></a>EXCEPT (fonction) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
