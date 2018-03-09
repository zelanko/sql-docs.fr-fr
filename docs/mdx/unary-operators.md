---
title: "Opérateurs unaires | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: unary operators
ms.assetid: bf1b5518-6040-4484-9ce8-79c0eb4373a9
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9c729af732238916a2cb88795fb94d0729ce9f85
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="unary-operators"></a>Opérateurs unaires
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Dans la syntaxe MDX (Multidimensional Expressions), les opérateurs unaires exécutent une opération sur un opérande unique, telle que le retour de la valeur négative ou positive d'une expression numérique.  
  
 MDX prend en charge les opérateurs unaires répertoriés dans le tableau suivant.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[- (Négatif)](../mdx/negative-mdx.md)|Retourne la valeur négative d'une expression numérique.|  
|[+ (Positif)](../mdx/positive-mdx.md)|Retourne la valeur positive d'une expression numérique.|  
  
 L'exemple suivant illustre l'utilisation d'un opérateur unaire pour retourner la valeur négative d'une mesure :  
  
```  
WITH   
   MEMBER [Measures].[NegDiscountAmount] AS  
   -[Measures].[Discount Amount]  
SELECT   
   {[Measures].[Discount Amount],[Measures].[NegDiscountAmount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 En outre, MDX utilise des opérateurs unaires spéciaux pour déterminer l’opération d’agrégation exécutée par le [RollupChildren](../mdx/rollupchildren-mdx.md) (fonction). Pour plus d’informations sur ces opérateurs unaires particuliers, consultez [ajouter une agrégation personnalisée à une Dimension](../analysis-services/multidimensional-models/bi-wizard-add-a-custom-aggregation-to-a-dimension.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs &#40; La syntaxe MDX &#41;](../mdx/operators-mdx-syntax.md)  
  
  
