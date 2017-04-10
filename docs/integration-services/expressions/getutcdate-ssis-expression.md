---
title: "GETUTCDATE (expression SSIS) | Microsoft Docs"
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
  - "dates [Integration Services], GETUTCDATE"
  - "date actuelle"
  - "temps UTC"
  - "GETUTCDATE (fonction)"
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# GETUTCDATE (expression SSIS)
  Renvoie la date actuelle du système en temps UTC (Universal Time Coordinate ou Greenwich Mean Time) au format DT_DBTIMESTAMP. La fonction GETUTCDATE ne comprend aucun argument.  
  
## Syntaxe  
  
```  
  
GETUTCDATE()  
```  
  
## Arguments  
 Aucun  
  
## Types des résultats  
 DT_DBTIMESTAMP  
  
## Exemples d'expressions  
 L'exemple suivant renvoie l'année de la date actuelle en temps UTC.  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 L’exemple suivant retourne le nombre de jours entre une date de la colonne **ModifiedDate** et la date UTC actuelle.  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 L'exemple suivant ajoute trois mois à la date UTC actuelle.  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## Voir aussi  
 [GETDATE &#40;expression SSIS&#41;](../../integration-services/expressions/getdate-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  