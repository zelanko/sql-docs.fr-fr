---
title: "Opérateurs (DMX) | Documents Microsoft"
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
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- operators [DMX]
- DMX [Analysis Services], operators
- Data Mining Extensions [Analysis Services], operators
ms.assetid: e453e570-1ad1-4604-892f-6130308936ac
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 238b90116aadae4e56328995ac48624a67390fa6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="operators-dmx"></a>Opérateurs (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Vous pouvez utiliser des opérateurs d’Extensions DMX (Data Mining) pour effectuer des opérations arithmétiques, de comparaison, concaténation et opérations logiques dans une requête dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise les opérateurs pour effectuer les actions suivantes :  
  
-   Rechercher des valeurs ou des objets selon un critère spécifique.  
  
-   Implémenter une décision entre des valeurs ou des expressions.  
  
 DMX utilise plusieurs catégories d'opérateurs, décrites ci-dessous. Pour plus d’informations sur chacun des opérateurs, consultez [Extensions d’exploration de données &#40; DMX &#41; Référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md).  
  
|Catégorie d'opérateurs|Type d’opération|  
|-----------------------|-----------------------|  
|[Arithmétique opérateurs &#40; DMX &#41;](../dmx/operators-arithmetic.md)|Effectuer une addition, une soustraction, une multiplication ou une division.|  
|[Opérateurs de comparaison &#40; DMX &#41;](../dmx/operators-comparison.md)|Comparer une valeur par rapport à une autre valeur ou une expression.|  
|[Logique opérateurs &#40; DMX &#41;](../dmx/operators-logical.md)|Tester une condition telle que AND, OR ou NOT.|  
|[Opérateurs unaires &#40; DMX &#41;](../dmx/operators-unary.md)|Effectuer une opération sur un opérande unique.|  
  
 Vous pouvez utiliser les opérateurs pour combiner des petites expressions DMX en expressions plus complexes. Dans les expressions complexes, les opérateurs sont analysés suivant l'ordre de priorité défini par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Les opérateurs dont le degré de priorité est le plus élevé sont exécutés avant les opérateurs de priorité moindre. Pour plus d’informations sur les expressions, consultez [Expressions &#40; DMX &#41;](../dmx/expressions-dmx.md).  
  
 Lorsque vous combinez des expressions simples pour former une expression complexe, le type de données de l'expression obtenue est déterminé par la combinaison des règles pour les opérateurs avec celles des priorités de types de données. Si le résultat est un caractère ou une valeur Unicode, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] détermine le classement du résultat par la combinaison des règles pour les opérateurs avec celles pour la priorité de classement. Il existe également des règles pour déterminer la précision, l’échelle et la longueur du résultat basées sur la précision, l’échelle et la longueur des expressions simples.  
  
## <a name="see-also"></a>Voir aussi  
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence](../dmx/data-mining-extensions-dmx-reference.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Conventions de syntaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Éléments de syntaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Fonctions de prédiction générales &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  

