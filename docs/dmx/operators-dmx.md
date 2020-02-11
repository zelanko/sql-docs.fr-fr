---
title: Opérateurs (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2f03c3152e3144b137c079cbdfddeff5b9cd5156
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68008172"
---
# <a name="operators-dmx"></a>Opérateurs (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Vous pouvez utiliser des opérateurs DMX (Data Mining Extensions) pour effectuer des opérations arithmétiques, de comparaison, de concaténation et logiques dans une requête dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise les opérateurs pour effectuer les actions suivantes :  
  
-   Rechercher des valeurs ou des objets selon un critère spécifique.  
  
-   Implémenter une décision entre des valeurs ou des expressions.  
  
 DMX utilise plusieurs catégories d'opérateurs, décrites ci-dessous. Pour plus d’informations sur les opérateurs individuels, consultez [Data Mining Extensions &#40;DMX&#41; opérateur Reference](../dmx/data-mining-extensions-dmx-operator-reference.md).  
  
|Catégorie d'opérateurs|Type d’opération|  
|-----------------------|-----------------------|  
|[Opérateurs arithmétiques &#40;&#41;DMX](../dmx/operators-arithmetic.md)|Effectuer une addition, une soustraction, une multiplication ou une division.|  
|[Opérateurs de comparaison &#40;&#41;DMX](../dmx/operators-comparison.md)|Comparez une valeur à une autre valeur ou une expression.|  
|[Opérateurs logiques &#40;&#41;DMX](../dmx/operators-logical.md)|Tester une condition telle que AND, OR ou NOT.|  
|[Opérateurs unaires &#40;&#41;DMX](../dmx/operators-unary.md)|Effectuer une opération sur un opérande unique.|  
  
 Vous pouvez utiliser les opérateurs pour combiner des petites expressions DMX en expressions plus complexes. Dans les expressions complexes, les opérateurs sont analysés suivant l'ordre de priorité défini par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Les opérateurs dont le degré de priorité est le plus élevé sont exécutés avant les opérateurs de priorité moindre. Pour plus d’informations sur les expressions, consultez [expressions &#40;DMX&#41;](../dmx/expressions-dmx.md).  
  
 Lorsque vous combinez des expressions simples pour former une expression complexe, le type de données de l'expression obtenue est déterminé par la combinaison des règles pour les opérateurs avec celles des priorités de types de données. Si le résultat est un caractère ou une valeur Unicode, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] détermine le classement du résultat par la combinaison des règles pour les opérateurs avec celles pour la priorité de classement. Il existe également des règles pour déterminer la précision, l’échelle et la longueur du résultat basées sur la précision, l’échelle et la longueur des expressions simples.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l'instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
