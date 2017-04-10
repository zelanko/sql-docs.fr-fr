---
title: "SIGN (expression SSIS) | Microsoft Docs"
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
  - "valeurs positives [Integration Services]"
  - "SIGN (fonction)"
  - "valeurs négatives"
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# SIGN (expression SSIS)
  Renvoie le nombre positif (+1), le nombre négatif (-1) ou zéro (0) selon le signe d'une expression numérique.  
  
## Syntaxe  
  
```  
  
SIGN(numeric_expression)  
```  
  
## Arguments  
 *numeric_expression*  
 Expression numérique signée valide. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Types des résultats  
 DT_I4  
  
## Notes  
 La fonction SIGN renvoie un résultat NULL si l'argument est NULL.  
  
## Exemples d'expressions  
 L'exemple suivant renvoie le signe d'un littéral numérique. Le résultat obtenu est -1.  
  
```  
SIGN(-123.45)  
```  
  
 L’exemple suivant retourne le signe du résultat de la soustraction de la colonne **StandardCost** de la colonne **DealerPrice**.  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  