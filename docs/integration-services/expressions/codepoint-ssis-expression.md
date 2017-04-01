---
title: "CODEPOINT (expression SSIS) | Microsoft Docs"
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
  - "CODEPOINT (fonction)"
  - "caractère le plus à gauche dans une expression"
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# CODEPOINT (expression SSIS)
  Renvoie le point de code Unicode du caractère placé à l'extrême gauche d'une expression de caractères.  
  
## Syntaxe  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## Arguments  
 *character_expression*  
 Expression de type caractère dont le caractère situé à l'extrême gauche sera évalué.  
  
## Types des résultats  
 DT_UI2  
  
## Notes  
 *character_expression* doit être du type de données DT_WSTR.  
  
 CODEPOINT retourne un résultat Null si *character_expression* est Null ou est une chaîne vide.  
  
## Exemples d'expressions  
 L'exemple suivant utilise un littéral de chaîne. Le résultat obtenu est 77, soit le point de code Unicode de M.  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 L'exemple suivant utilise une variable. Si **Name** a pour valeur « Tout-terrain », le résultat obtenu est 84, soit le point de code Unicode de T.  
  
```  
CODEPOINT(@Name)  
```  
  
## Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  