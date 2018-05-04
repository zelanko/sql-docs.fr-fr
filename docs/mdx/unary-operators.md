---
title: Opérateurs unaires | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- unary operators
ms.assetid: bf1b5518-6040-4484-9ce8-79c0eb4373a9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 1486ab5907a9c3b738bc9ab23e8154e696766f16
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="unary-operators"></a>Opérateurs unaires
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Dans la syntaxe MDX (Multidimensional Expressions), les opérateurs unaires exécutent une opération sur un opérande unique, telle que le retour de la valeur négative ou positive d'une expression numérique.  
  
 MDX prend en charge les opérateurs unaires répertoriés dans le tableau suivant.  
  
|Opérateur| Description|  
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
 [Opérateurs &#40;syntaxe MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
