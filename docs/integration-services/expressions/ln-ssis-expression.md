---
title: "LN (expression SSIS) | Microsoft Docs"
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
  - "LN, fonction"
  - "logarithme népérien d'une expression [Integration Services]"
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
caps.latest.revision: 34
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 34
---
# LN (expression SSIS)
  Renvoie le logarithme népérien d'une expression numérique.  
  
## Syntaxe  
  
```  
  
LN(numeric_expression)  
```  
  
## Arguments  
 *numeric_expression*  
 Expression numérique valide non négative et différente de zéro.  
  
## Types des résultats  
 DT_R8  
  
## Notes  
 L'expression numérique est convertie vers le type de données DT_R8 avant le calcul du logarithme. Pour plus d’informations, consultez [Types de données d’Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Si l’argument *numeric_expression* donne une valeur inférieure ou égale à zéro, le résultat obtenu est Null.  
  
## Exemples d'expressions  
 L'exemple suivant utilise un littéral numérique. La fonction renvoie la valeur 3,737766961828337.  
  
```  
LN(42)  
```  
  
 L'exemple suivant utilise la colonne **Length**. Si la valeur de la colonne est 53,99, la fonction renvoie 3,9887988442302.  
  
```  
LN(Length)   
```  
  
 L'exemple suivant utilise la variable **Length**. La variable doit être d'un type de données numérique ou l'expression doit comprendre une conversion explicite vers un type de données numérique. Si la variable **Length** a pour valeur 234,567, la fonction renvoie 5,45774126708797.  
  
```  
LN(@Length)   
```  
  
## Voir aussi  
 [LOG &#40;expression SSIS&#41;](../../integration-services/expressions/log-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  