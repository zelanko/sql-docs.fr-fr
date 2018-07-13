---
title: DAY (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e79780ad62800eac8dfabbd6c8b80eacc3abe5dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148750"
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
  
## <a name="result-types"></a>Types de résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 La fonction DAY renvoie un résultat NULL si l'argument est NULL.  
  
 Un littéral de date doit être explicitement converti dans l'un des types de données date. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
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
 [DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md)   
 [DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md)   
 [DATEPART &#40;expression SSIS&#41;](datepart-ssis-expression.md)   
 [MONTH &#40;expression SSIS&#41;](month-ssis-expression.md)   
 [YEAR &#40;expression SSIS&#41;](year-ssis-expression.md)   
 [Fonctions &#40;SSIS Expression&#41;](functions-ssis-expression.md)  
  
  
