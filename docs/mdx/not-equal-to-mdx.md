---
title: '&lt;&gt; (Différent de) (MDX) | Documents Microsoft'
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
- <>
dev_langs:
- kbMDX
helpviewer_keywords:
- not equal to operator (<>)
- <> (not equal to operator)
ms.assetid: b4eb3f1c-8b68-4530-a8f3-e3b8414ac789
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 4670c8f96ac37547ade0951234d483337542a668
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ltgt-not-equal-to-mdx"></a>&lt;&gt; (Différent de) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Exécute une opération de comparaison qui détermine si la valeur d'une expression MDX est différente de la valeur d'une autre expression MDX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MDX_Expression <> MDX_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *MDX_Expression*  
 Expression MDX valide.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur booléenne basée sur les conditions suivantes :  
  
-   **true** si les deux paramètres sont non null et que le premier paramètre n’est pas égal au deuxième paramètre.  
  
-   **false** si les deux paramètres sont non null et que le premier paramètre est égal au second paramètre.  
  
-   NULL si l'un ou l'autre ou les deux paramètres ont une valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
