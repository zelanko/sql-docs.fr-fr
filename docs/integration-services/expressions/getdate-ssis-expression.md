---
title: "GETDATE (expression SSIS) | Microsoft Docs"
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
  - "date actuelle"
  - "GETDATE (fonction)"
  - "dates [Integration Services], GETDATE"
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# GETDATE (expression SSIS)
  Renvoie la date actuelle du système dans un format DT_DBTIMESTAMP. La fonction GETDATE ne prend aucun argument.  
  
> [!NOTE]  
>  La fonction GETDATE retourne un résultat d'une longueur de 29 caractères.  
  
## Syntaxe  
  
```  
  
GETDATE()  
```  
  
## Arguments  
 Aucun  
  
## Types des résultats  
 DT_DBTIMESTAMP  
  
## Exemples d'expressions  
 L'exemple suivant renvoie l'année de la date actuelle.  
  
```  
DATEPART("year",GETDATE())  
```  
  
 L’exemple suivant renvoie le nombre de jours entre une date de la colonne **ModifiedDate** et la date actuelle.  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 L'exemple suivant ajoute trois mois à la date actuelle.  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## Voir aussi  
 [GETUTCDATE &#40;expression SSIS&#41;](../../integration-services/expressions/getutcdate-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  