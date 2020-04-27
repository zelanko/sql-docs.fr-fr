---
title: DATEDIFF (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DATEDIFF statement
- dates [Integration Services], DATEDIFF
ms.assetid: 449b327f-47c7-4709-8bc6-4ee9a35cc330
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b42115278e6866063639c7ce2fc596749ad2d39f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62898084"
---
# <a name="datediff-ssis-expression"></a>DATEDIFF (expression SSIS)
  Renvoie le nombre de limites de date et d'heure traversées entre deux dates données. Le paramètre *datepart* identifie quelles limites de date et d’heure il faut comparer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DATEDIFF(datepart, startdate, endate)  
```  
  
## <a name="arguments"></a>Arguments  
 *datepart*  
 Paramètre qui indique la partie de la date à comparer et pour laquelle une valeur doit être retournée.  
  
 *startdate*  
 Date de début de l'intervalle.  
  
 *endate*  
 Date de fin de l'intervalle.  
  
## <a name="result-types"></a>Types des résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant décrit les parties de date et les abréviations reconnues par l'évaluateur d'expression.  
  
|partie de date|Abréviations|  
|--------------|-------------------|  
|Year|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Jour de l'année|dy, y|  
|jour|dd, d|  
|Week|wk, ww|  
|Jour de la semaine|dw, w|  
|Heure|Hh|  
|Minute|mi, n|  
|Seconde|ss, s|  
|Milliseconde|Ms|  
  
 La fonction DATEDIFF renvoie un résultat NULL si un argument est NULL.  
  
 Un littéral de date doit être explicitement converti dans l'un des types de données date. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
 Une erreur se produit dans les cas suivants : une date n'est pas valide, l'unité de date ou d'heure n'est pas une chaîne, la date de début n'est pas une date ou la date de fin n'est pas une date.  
  
 Si la date de fin est antérieure à la date de début, la fonction renvoie un nombre négatif. Si les dates de début et de fin sont identiques ou qu'elles appartiennent au même intervalle, la fonction renvoie zéro.  
  
## <a name="ssis-expression-examples"></a>Exemples d'expressions SSIS  
 L'exemple suivant calcule le nombre de jours entre deux littéraux de date. Si le format de la date est « mm/jj/aaaa », la fonction renvoie 7.  
  
```  
DATEDIFF("dd", (DT_DBTIMESTAMP)"8/1/2003", (DT_DBTIMESTAMP)"8/8/2003")  
```  
  
 L'exemple suivant renvoie le nombre de mois entre un littéral de date et la date actuelle.  
  
```  
DATEDIFF("mm", (DT_DBTIMESTAMP)"8/1/2003",GETDATE())  
```  
  
 L’exemple suivant retourne le nombre de semaines entre la date de la colonne **ModifiedDate** et la variable **YearEndDate** . Si **YearEndDate** a un `date` type de données, aucun cast explicite n’est nécessaire.  
  
```  
DATEDIFF("Week", ModifiedDate,@YearEndDate)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DATEADD &#40;expression SSIS&#41;](dateadd-ssis-expression.md)   
 [DATEPART &#40;expression SSIS&#41;](datepart-ssis-expression.md)   
 [DAY &#40;expression SSIS&#41;](day-ssis-expression.md)   
 [MONTH &#40;expression SSIS&#41;](month-ssis-expression.md)   
 [YEAR &#40;expression SSIS&#41;](year-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
