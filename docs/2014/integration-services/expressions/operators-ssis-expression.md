---
title: Opérateurs (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ea7e6c9b8acb3301174a1e4086aee3844eb1ee81
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174509"
---
# <a name="operators-ssis-expression"></a>Opérateurs (expression SSIS)
  Cette section décrit les opérateurs du langage d'expression ainsi que l'associativité et la priorité des opérateurs utilisées par l'évaluateur d'expression.  
  
 Le tableau suivant indique les rubriques relatives aux opérateurs décrits dans cette section.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md)|Convertit une expression d'un type de données en un autre type de données.|  
|[&#40;&#41;&#40;Parenthèses&#41; &#40;SSIS Expression&#41;](parentheses-ssis-expression.md)|Identifie l'ordre d'évaluation des expressions.|  
|[+ &#40;Ajouter&#41; &#40;SSIS&#41;](add-ssis.md)|Additionne deux expressions numériques.|  
|[+ &#40;Concaténer&#41; &#40;SSIS Expression&#41;](concatenate-ssis-expression.md)|Concatène deux expressions.|  
|[- &#40;Soustraire&#41; &#40;SSIS Expression&#41;](subtract-ssis-expression.md)|Soustrait la deuxième expression numérique de la première.|  
|[- &#40;Negate&#41; &#40;SSIS Expression&#41;](negate-ssis-expression.md)|Inverse une expression numérique.|  
|[&#42;&#40;Multiplier&#41; &#40;SSIS Expression&#41;](multiply-ssis-expression.md)|Multiplie deux expressions numériques.|  
|[Diviser &#40;SSIS Expression&#41;](divide-ssis-expression.md)|Divise la première expression numérique par la deuxième.|  
|[&#40;Modulo&#41; &#40;SSIS Expression&#41;](modulo-ssis-expression.md)|Fournit le reste entier de la division de la première expression numérique par la deuxième.|  
|[&#124;&#124;&#40;OR logique&#41; &#40;SSIS Expression&#41;](logical-or-ssis-expression.md)|Effectue une opération OR logique.|  
|[& & &#40;AND logique&#41; &#40;SSIS Expression&#41;](logical-and-ssis-expression.md)|Effectue une opération AND logique.|  
|[! &#40;Not logique&#41; &#40;SSIS Expression&#41;](logical-not-ssis-expression.md)|Inverse un opérande booléen.|  
|[&#124;&#40;Au niveau du bit OR inclusif&#41; &#40;SSIS Expression&#41;](bitwise-inclusive-or-ssis-expression.md)|Effectue une opération OR au niveau du bit avec deux valeurs entières.|  
|[^ &#40;Au niveau du bit OR exclusif&#41; &#40;SSIS Expression&#41;](bitwise-exclusive-or-ssis-expression.md)|Effectue une opération OR exclusive au niveau du bit avec deux valeurs entières.|  
|[& &#40;Au niveau du bit AND&#41; &#40;SSIS Expression&#41;](bitwise-and-ssis-expression.md)|Effectue une opération AND au niveau du bit avec deux valeurs entières.|  
|[~ &#40;Not au niveau du bit&#41; &#40;SSIS Expression&#41;](bitwise-not-ssis-expression.md)|Effectue une négation au niveau du bit d'un entier.|  
|[== &#40;Égal&#41; &#40;SSIS Expression&#41;](equal-ssis-expression.md)|Effectue une comparaison pour déterminer si deux expressions sont égales.|  
|[\!= &#40;Non égal&#41; &#40;expression SSIS&#41;](unequal-ssis-expression.md)|Effectue une comparaison pour déterminer si deux expressions sont différentes.|  
|[&#62;&#40;Supérieur&#41; &#40;SSIS Expression&#41;](greater-than-ssis-expression.md)|Effectue une comparaison pour déterminer si la première expression est supérieure à la deuxième.|  
|[&#60;&#40;Inférieure à&#41; &#40;SSIS Expression&#41;](less-than-ssis-expression.md)|Effectue une comparaison pour déterminer si la première expression est inférieure à la deuxième.|  
|[&#62;= &#40;Supérieur ou égal à&#41; &#40;SSIS Expression&#41;](greater-than-or-equal-to-ssis-expression.md)|Effectue une comparaison pour déterminer si la première expression est supérieure ou égale à la deuxième.|  
|[&#60;= &#40;Inférieure ou égale à&#41; &#40;SSIS Expression&#41;](less-than-or-equal-to-ssis-expression.md)|Effectue une comparaison pour déterminer si la première expression est inférieure ou égale à la deuxième.|  
|[? : &#40;Conditionnel&#41; &#40;expression SSIS&#41;](conditional-ssis-expression.md)|Renvoie une des deux expressions selon l'évaluation d'une expression booléenne.|  
  
 Pour plus d’informations sur la position de chaque opérateur dans la hiérarchie des priorités, consultez [Priorités et associativité des opérateurs](operator-precedence-and-associativity.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;SSIS Expression&#41;](functions-ssis-expression.md)   
 [Exemples d’expressions Integration Services avancées](examples-of-advanced-integration-services-expressions.md)   
 [Expressions Integration Services &#40;SSIS&#41;](integration-services-ssis-expressions.md)  
  
  
