---
title: "ISNULL (expression SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "valeurs NULL [Integration Services]"
  - "ISNULL (fonction)"
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# ISNULL (expression SSIS)
  Renvoie une valeur booléenne basée sur le test du caractère NULL d'une expression.  
  
## Syntaxe  
  
```  
  
ISNULL(expression)  
```  
  
## Arguments  
 *expression*  
 Expression valide d'un type de données quelconque.  
  
## Types des résultats  
 DT_BOOL  
  
## Exemples d'expressions  
 L'exemple suivant renvoie TRUE si la colonne **DiscontinuedDate** contient une valeur NULL.  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 L'exemple suivant renvoie « Unknown last name » si la valeur de la colonne **LastName** est NULL, sinon il renvoie la valeur de **LastName**.  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 L'exemple suivant renvoie toujours TRUE si la colonne **DaysToManufacture** est NULL, quelle que soit la valeur de la variable **AddDays**.  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)   
 [COALESCE &#40;Transact-SQL&#41;](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  