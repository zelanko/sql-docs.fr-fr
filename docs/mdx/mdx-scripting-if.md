---
title: IF instruction (MDX Multidimensional) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: statements [MDX], IF
ms.assetid: 8830cce5-9e06-4f89-a555-295bb0d0a8a1
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3bfc3eb927d6e9764349281ea48ef94e7873675b
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="mdx-scripting---if"></a>Écriture de scripts MDX - IF
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Exécute une instruction si la condition est vérifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Expression MDX (Multidimensional Expressions) dont l'évaluation aboutit à une valeur booléenne retournant la valeur True ou False.  
  
 *affectation*  
 Expression MDX assignant une valeur à un sous-cube ou à une propriété calculée.  
  
## <a name="remarks"></a>Notes  
 Utilisez l’instruction IF pour le flux de contrôle, à la différence du [IIf &#40; MDX &#41; ](../mdx/iif-mdx.md) (fonction) et le [instruction CASE &#40; MDX &#41; ](../mdx/case-statement-mdx.md) qui peut uniquement être utilisé pour retourner des valeurs ou des objets.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, la portée est limitée au niveau Pays de la hiérarchie Customers Geography dans la dimension Customers. Si la mesure actuelle est Montant des ventes sur Internet, ce montant est défini sur 10 :  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
