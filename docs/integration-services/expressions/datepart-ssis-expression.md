---
title: DATEPART (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5d82da0734ba0e3dda009b912fa9c537e77a6f39
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58280603"
---
# <a name="datepart-ssis-expression"></a>DATEPART (expression SSIS)
  Renvoie un entier représentant une partie d'une date.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a>Arguments  
 *partie de date*  
 Paramètre qui indique la partie de date pour laquelle il faut retourner une nouvelle valeur.  
  
 *date*  
 Expression renvoyant une date valide ou une chaîne dans un format de date.  
  
## <a name="result-types"></a>Types des résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes   
 La fonction DATEPART renvoie un résultat NULL si l'argument est NULL.  
  
 Un littéral de date doit être explicitement converti dans l'un des types de données date. Pour plus d’informations, consultez [Types de données Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Le tableau suivant décrit les parties de date et les abréviations reconnues par l'évaluateur d'expression. Les noms de partie de date ne respectent pas la casse.  
  
|partie de date|Abréviations|  
|--------------|-------------------|  
|Année|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Jour de l'année|dy, y|  
|Jour|dd, d|  
|Week|wk, ww|  
|JourSem|dw|  
|Heure|Hh|  
|Minute|mi, n|  
|Seconde|ss, s|  
|Milliseconde|Ms|  
  
## <a name="ssis-expression-examples"></a>Exemples d'expressions SSIS  
 L'exemple suivant renvoie l'entier qui représente le mois dans un littéral de date. Si le format de la date est « mm/jj/aaaa », l'exemple renvoie 11.  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 L’exemple suivant retourne l’entier qui représente le jour dans la colonne **ModifiedDate** .  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 L'exemple suivant renvoie l'entier qui représente l'année de la date actuelle.  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## <a name="see-also"></a> Voir aussi  
 [DATEADD &#40;expression SSIS&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40;expression SSIS&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DAY &#40;expression SSIS&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH &#40;expression SSIS&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR &#40;expression SSIS&#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
