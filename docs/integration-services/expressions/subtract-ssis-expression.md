---
title: "- (Soustraction) (expression SSIS) | Microsoft Docs"
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
  - "- (soustraction)"
  - "soustraction, opérateur (-)"
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# - (Soustraction) (expression SSIS)
  Soustrait la deuxième expression numérique de la première.  
  
## Syntaxe  
  
```  
  
numeric_expression1 – numeric_expression2  
  
```  
  
## Arguments  
 *expression_numérique1, expression_numérique2*  
 Toute expression valide d'un type de données numérique. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Types des résultats  
 Déterminés par les types de données des deux arguments. Pour plus d’informations, consultez [Types de données Integration Services dans les expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## Notes  
 Ajoutez l'expression unaire négative entre parenthèses pour garantir que l'expression est évaluée dans l'ordre correct  
  
## Notes  
 Si l'un des opérandes est NULL, le résultat est NULL.  
  
## Exemples d'expressions  
 L'exemple suivant soustrait des littéraux numériques.  
  
```  
5 - 6.09  
```  
  
 L’exemple suivant soustrait la valeur de la colonne **StandardCost** de la valeur de la colonne **ListPrice**.  
  
```  
ListPrice - StandardCost  
```  
  
 L’exemple suivant soustrait une valeur calculée de la colonne **ListPrice**. La variable **Discount%** doit figurer entre crochets, car le nom contient le caractère %. Pour plus d’informations, consultez [Identificateurs &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## Voir aussi  
 [Priorités et associativité des opérateurs](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  