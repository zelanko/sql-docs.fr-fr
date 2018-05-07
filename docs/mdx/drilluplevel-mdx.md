---
title: DrillupLevel (MDX) | Documents Microsoft
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
- DRILLUPLEVEL
dev_langs:
- kbMDX
helpviewer_keywords:
- DrillupLevel function
ms.assetid: 63431f79-f3a1-40c4-bf57-2b6bd8991cc3
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 8fb99e8e1984f0bbfddf4e7e8bd48e7fa05c0e45
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Extrait vers le haut les membres d'un jeu situé au-dessous du niveau spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
## <a name="remarks"></a>Notes  
 Le **DrillupLevel** fonction retourne un jeu de membres organisé hiérarchiquement selon les membres inclus dans le jeu spécifié. L'ordre des membres dans le jeu spécifié est conservé.  
  
 Si une expression de niveau est spécifiée, la **DrillupLevel** fonction construit le jeu en récupérant uniquement les membres qui sont au-dessus du niveau spécifié. Si une expression de niveau est spécifiée, et il n’existe aucun membre du niveau représenté dans le jeu spécifié, le jeu spécifié est retourné.  
  
 Si aucune expression de niveau n'est spécifiée, la fonction construit le jeu en récupérant uniquement les membres situés un niveau au-dessus du niveau le plus bas de la première dimension référencée dans le jeu spécifié.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne l'ensemble des membres du premier jeu placés au-dessus du niveau Subcategory.  
  
```  
SELECT DrillUpLevel   
  ({[Product].[Product Categories].[All Products]  
    ,[Product].[Product Categories].[Subcategory].&[32],  
    [Product].[Product Categories].[Product].&[215]},  
  [Product].[Product Categories].[Subcategory]  
    )  
  ON 0  
  FROM [Adventure Works]  
  WHERE [Measures].[Internet Order Quantity]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
