---
title: "+ (Addition) (SSIS) | Microsoft Docs"
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
  - "+ (add)"
  - "addition, opérateur (+)"
  - "ajout d'expressions"
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# + (Addition) (SSIS)
  Additionne deux expressions numériques.  
  
## Syntaxe  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## Arguments  
 *numeric_expression1, numeric_ expression2*  
 Toute expression valide d'un type de données numérique.  
  
## Types des résultats  
 Déterminés par les types de données des deux arguments. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Notes  
 Si l'un des opérandes est NULL, le résultat est NULL.  
  
## Exemples d'expressions  
 L'exemple suivant additionne des littéraux numériques.  
  
```  
5 + 6.09 + 7.0  
```  
  
 L'exemple suivant additionne les valeurs des colonnes **VacationHours** et **SickLeaveHours** .  
  
```  
VacationHours + SickLeaveHours  
```  
  
 L'exemple suivant ajoute une valeur calculée à la colonne **StandardCost** . La variable **Profit%** doit figurer entre crochets car elle contient le caractère « % ». Pour plus d’informations, consultez [Identificateurs &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## Voir aussi  
 [Priorités et associativité des opérateurs](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  