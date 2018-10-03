---
title: Opérateurs de cumul personnalisés dans les Dimensions Parent-enfant | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 444c67248da2ade5db322fcf6630f6230e46c032
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054219"
---
# <a name="custom-rollup-operators-in-parent-child-dimensions"></a>Opérateurs de cumul personnalisé dans les dimensions parent-enfant
  Les opérateurs de cumul personnalisé proposent une façon simple de contrôler le mode de cumul des valeurs de membre dans les valeurs parentes à l'intérieur d'une hiérarchie parent-enfant. Dans une dimension dotée d'une relation parent-enfant, vous spécifiez une colonne contenant des opérateurs unaires qui spécifient le cumul de tous les membres non calculés de l'attribut parent. L'opérateur unaire est appliqué aux membres dès que les valeurs des membres parents sont évaluées.  
  
 Les opérateurs unaires sont stockés dans la colonne définie par la propriété `UnaryOperatorColumn` de l'attribut parent et ils sont appliqués à chaque membre de l'attribut. La colonne spécifiée par cette propriété peut résider dans la table de dimension ou dans une table liée à la table de dimension par une clé étrangère de la table de dimension.  
  
 Les opérateurs de cumul personnalisé proposent des fonctionnalités analogues aux formules de membre personnalisées, mais plus simples. Une formule de membre personnalisée utilise les expressions MDX (Multidimensional Expressions) pour déterminer le mode de cumul des membres. De son côté, un opérateur de cumul personnalisé utilise un simple opérateur unaire pour déterminer comment la valeur d'un membre affecte le parent. Les formules de membre personnalisées du niveau précédent d'une dimension remplacent l'opérateur de cumul personnalisé d'un niveau.  
  
## <a name="custom-rollup-precedence"></a>Précédence du cumul personnalisé  
 En termes de précédence, les opérateurs de cumul personnalisé de l'attribut source d'un niveau de la hiérarchie remplacent les formules de membre personnalisées du niveau précédent. Toutefois, les formules de membre personnalisées d'un niveau sont prioritaires sur les opérateurs de cumul personnalisés du niveau suivant.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des formules de membre personnalisées](attribute-properties-define-custom-member-formulas.md)   
 [Opérateurs unaires dans les dimensions parent-enfant](parent-child-dimension-attributes-unary-operators.md)  
  
  
