---
title: "~ (NOT au niveau du bit) (expression SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "opération NOT au niveau du bit (~)"
  - "~ (opération NOT au niveau du bit)"
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# ~ (NOT au niveau du bit) (expression SSIS)
  Effectue une négation au niveau du bit d'un entier. Cet opérateur est applicable aux types de données entier signé et non signé.  
  
## Syntaxe  
  
```  
  
~integer_expression  
  
```  
  
## Arguments  
 *integer_expression*  
 Toute expression valide d'un type de données integer. *integer*_*expression* est un nombre entier transformé en nombre binaire pour l’opération au niveau du bit. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Types des résultats  
 Retourne le type de données *integer_expression*.  
  
## Notes  
 Aucun  
  
## Exemples d'expressions  
 L'exemple suivant réalise une opération NOT au niveau du bit ( ~ ) sur le nombre 170 (0000 0000 1010 1010). Le nombre est un entier signé.  
  
```  
  
~ 170  
```  
  
 L'expression renvoie la valeur -170 (1111111101010101).  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## Voir aussi  
 [Priorités et associativité des opérateurs](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  