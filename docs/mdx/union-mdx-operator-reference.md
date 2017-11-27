---
title: + (Union) (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- +
dev_langs:
- kbMDX
helpviewer_keywords:
- union operator (+)
- + (union operator)
ms.assetid: 6c6dfca2-7413-452a-98a2-3d8c58a8a3e6
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 49da0620fba34bf198a5d343ef7a8c5350c1cea8
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="union---mdx-operator-reference"></a>Union - référence des opérateurs MDX
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Exécute une opération de jeu qui retourne une union de deux jeux en supprimant les membres dupliqués.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set_Expression + Set_Expression      
```  
  
#### <a name="parameters"></a>Paramètres  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="return-value"></a>Valeur retournée  
 Jeu contenant les membres des deux jeux spécifiés.  
  
## <a name="remarks"></a>Notes  
 Le **+ (Union)** opérateur est fonctionnellement équivalente à la [Union &#40; MDX &#41; ](../mdx/union-mdx.md) (fonction).  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
-- This member returns the gross profit margin for each year for North American countries.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members ON 0,  
    {[Sales Territory].[Sales Territory].[Country].[United States]} +  
     {[Sales Territory].[Sales Territory].[Country].[Canada]} ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  

