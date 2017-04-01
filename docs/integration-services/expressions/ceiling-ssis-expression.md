---
title: "CEILING (expression SSIS) | Microsoft Docs"
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
  - "entier le moins élevé supérieur ou égal à l'expression"
  - "CEILING, fonction [SSIS]"
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# CEILING (expression SSIS)
  Renvoie le plus petit entier qui est supérieur ou égal à une expression numérique.  
  
## Syntaxe  
  
```  
  
CEILING(numeric_expression)  
```  
  
## Arguments  
 *expression_numérique*  
 Expression numérique valide.  
  
## Types des résultats  
 Type de données de l'expression numérique envoyée à la fonction.  
  
## Notes  
 La fonction CEILING renvoie un résultat NULL si l'argument est NULL.  
  
## Exemples d'expressions  
 Les exemples suivants appliquent la fonction CEILING à une valeur successivement positive, négative et nulle.  
  
```  
CEILING(123.74)  
```  
  
 Retourne 124.00  
  
```  
CEILING(-124.27)  
```  
  
 Retourne -124.00  
  
```  
CEILING(0.00)  
```  
  
 Renvoie 0,00  
  
## Voir aussi  
 [FLOOR &#40;expression SSIS&#41;](../../integration-services/expressions/floor-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  