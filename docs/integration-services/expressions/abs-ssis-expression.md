---
title: "ABS (expression SSIS) | Microsoft Docs"
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
  - "ABS (fonction)"
  - "valeur positive absolue"
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# ABS (expression SSIS)
  Renvoie la valeur absolue d'une expression numérique.  
  
## Syntaxe  
  
```  
  
ABS(numeric_expression)  
```  
  
## Arguments  
 *numeric_expression*  
 Expression numérique signée ou non signée.  
  
## Types des résultats  
 Type de données de l'expression numérique envoyée à la fonction.  
  
## Notes  
 La fonction ABS renvoie un résultat NULL si l'argument est NULL.  
  
## Exemples d'expressions  
 Les exemples suivants appliquent la fonction ABS à un nombre positif et à un nombre négatif. Tous les deux renvoient le résultat 1,23.  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 L'exemple suivant applique la fonction ABS à une expression qui calcule la différence entre les valeurs des variables **HighTemperature** et **LowTempature**.  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  