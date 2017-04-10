---
title: "LOG (expression SSIS) | Microsoft Docs"
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
  - "logarithmes de base 10"
  - "LOG, fonction"
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# LOG (expression SSIS)
  Renvoie le logarithme de base 10 d'une expression numérique.  
  
## Syntaxe  
  
```  
  
LOG(numeric_expression)  
```  
  
## Arguments  
 *numeric_expression*  
 Expression numérique valide différente de zéro ou non négative.  
  
## Types des résultats  
 DT_R8  
  
## Notes  
 *L’expression numérique* est convertie vers le type de données DT_R8 avant le calcul du logarithme. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Si l’argument *numeric_expression* donne une valeur inférieure ou égale à zéro, le résultat obtenu est NULL.  
  
## Exemples d'expressions  
 L'exemple suivant utilise un littéral numérique. La fonction renvoie la valeur 1,988291341907488.  
  
```  
LOG(97.34)  
```  
  
 L'exemple suivant utilise la colonne **Length**. Si la valeur de la colonne est 101,24, la fonction renvoie 2,005352136486217.  
  
```  
LOG(Length)   
```  
  
 L'exemple suivant utilise la variable **Length**. La variable doit être d'un type de données numérique ou l'expression doit comprendre une conversion explicite en un type de données [!INCLUDE[ssIS](../../includes/ssis-md.md)] numérique. Si la variable **Length** a pour valeur 234,567, la fonction renvoie 2,370266913465859.  
  
```  
LOG(@Length)   
```  
  
## Voir aussi  
 [EXP &#40;expression SSIS&#41;](../../integration-services/expressions/exp-ssis-expression.md)   
 [LN &#40;expression SSIS&#41;](../../integration-services/expressions/ln-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  