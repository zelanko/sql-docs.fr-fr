---
title: DAY (Expression SSIS) | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5e297f7021239ded4aa76ad61e75fddba528ccf6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="day-ssis-expression"></a>DAY (expression SSIS)
  Renvoie un entier qui représente la partie jour d'une date.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a>Arguments  
 *date*  
 Expression renvoyant une date valide ou une chaîne dans un format de date.  
  
## <a name="result-types"></a>Types des résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 La fonction DAY renvoie un résultat NULL si l'argument est NULL.  
  
 Un littéral de date doit être explicitement converti dans l'un des types de données date. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  La validation de l'expression échoue lorsqu'un littéral de date est explicitement converti en un des types de données de date suivants : DT_DBTIMESTAMPOFFSET et DT_DBTIMESTAMP2.  
  
 L'utilisation de la fonction DAY est plus directe mais équivalente à celle de la fonction DATEPART("Day", date).  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple renvoie le nombre représentant le jour dans un littéral de date. Si le format de la date est « mm/jj/aaaa », l'exemple renvoie 23.  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 L’exemple suivant retourne l’entier qui représente le jour dans la colonne **ModifiedDate** .  
  
```  
DAY(ModifiedDate)  
```  
  
 L'exemple suivant renvoie l'entier qui représente le jour de la date actuelle.  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DATEADD &#40; Expression SSIS &#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40; Expression SSIS &#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40; Expression SSIS &#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [MOIS &#40; Expression SSIS &#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [ANNÉE &#40; Expression SSIS &#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Fonctions &#40; Expression SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

