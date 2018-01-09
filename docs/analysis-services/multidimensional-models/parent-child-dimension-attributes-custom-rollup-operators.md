---
title: "Opérateurs de cumul personnalisés dans les Dimensions Parent-enfant | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 84ed7fd34e017fe0ea076822d1931ea1143b5849
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="parent-child-dimension-attributes---custom-rollup-operators"></a>Attributs de Dimension parent-enfant - opérateurs de cumul personnalisé
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Opérateurs de cumul personnalisés fournissent un moyen simple de contrôler comment les valeurs de membre sont reportées dans les valeurs parentes dans une hiérarchie parent-enfant. Dans une dimension dotée d'une relation parent-enfant, vous spécifiez une colonne contenant des opérateurs unaires qui spécifient le cumul de tous les membres non calculés de l'attribut parent. L'opérateur unaire est appliqué aux membres dès que les valeurs des membres parents sont évaluées.  
  
 Les opérateurs unaires sont stockés dans la colonne définie par la propriété **UnaryOperatorColumn** de l'attribut parent et ils sont appliqués à chaque membre de l'attribut. La colonne spécifiée par cette propriété peut résider dans la table de dimension ou dans une table liée à la table de dimension par une clé étrangère de la table de dimension.  
  
 Les opérateurs de cumul personnalisé proposent des fonctionnalités analogues aux formules de membre personnalisées, mais plus simples. Une formule de membre personnalisée utilise les expressions MDX (Multidimensional Expressions) pour déterminer le mode de cumul des membres. De son côté, un opérateur de cumul personnalisé utilise un simple opérateur unaire pour déterminer comment la valeur d'un membre affecte le parent. Les formules de membre personnalisées du niveau précédent d'une dimension remplacent l'opérateur de cumul personnalisé d'un niveau.  
  
## <a name="custom-rollup-precedence"></a>Précédence du cumul personnalisé  
 En termes de précédence, les opérateurs de cumul personnalisé de l'attribut source d'un niveau de la hiérarchie remplacent les formules de membre personnalisées du niveau précédent. Toutefois, les formules de membre personnalisées d'un niveau sont prioritaires sur les opérateurs de cumul personnalisés du niveau suivant.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des formules de membre personnalisées](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md)   
 [Opérateurs unaires dans les Dimensions Parent-enfant](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-unary-operators.md)  
  
  
