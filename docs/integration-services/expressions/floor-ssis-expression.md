---
title: "FLOOR (expression SSIS) | Microsoft Docs"
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
  - "entier le plus élevé inférieur ou égal à l'expression"
  - "FLOOR, fonction [SSIS]"
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# FLOOR (expression SSIS)
  Renvoie l'entier le plus élevé inférieur ou égal à une expression numérique.  
  
## Syntaxe  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## Arguments  
 *numeric_expression*  
 Expression numérique valide.  
  
## Types des résultats  
 Type de données numérique de l'expression de l'argument. Le résultat est la partie entière de la valeur calculée dans le même type de données que *numeric_expression.*  
  
## Notes  
 La fonction FLOOR renvoie un résultat NULL si l'argument est NULL.  
  
## Exemples d'expressions  
 Les exemples suivants appliquent la fonction FLOOR à une valeur successivement positive, négative et nulle.  
  
```  
FLOOR(123.45)  
```  
  
 Retourne 123.00  
  
```  
FLOOR(-123.45)  
```  
  
 Retourne -124.00  
  
```  
FLOOR(0.00)  
```  
  
 Renvoie 0,00  
  
## Voir aussi  
 [CEILING &#40;expression SSIS&#41;](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  