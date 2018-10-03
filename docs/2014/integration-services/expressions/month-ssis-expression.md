---
title: MONTH (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], MONTH
- MONTH function
ms.assetid: b5a47a11-c2ef-49bd-bd70-235632ff7bf6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d4106fed90fd370ee30a6bb3a5ad2be5324caddf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102479"
---
# <a name="month-ssis-expression"></a>MONTH (expression SSIS)
  Renvoie un entier qui représente la partie mois d'une date.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MONTH(date)  
```  
  
## <a name="arguments"></a>Arguments  
 *date*  
 Date à n'importe quel format de date.  
  
## <a name="result-types"></a>Types de résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 La fonction MONTH renvoie un résultat NULL si l'argument est NULL.  
  
 Un littéral de date doit être explicitement converti dans l'un des types de données date. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  La validation de l'expression échoue lorsqu'un littéral de date est explicitement converti en un des types de données de date suivants : DT_DBTIMESTAMPOFFSET et DT_DBTIMESTAMP2.  
  
 L'utilisation de la fonction MONTH est plus directe mais équivalente à celle de la fonction DATEPART("Month", date).  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple renvoie le chiffre représentant le mois dans un littéral de date. Si le format de la date est « mm/jj/aaaa », l'exemple renvoie 11.  
  
```  
MONTH((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 L’exemple suivant renvoie l’entier qui représente le mois dans la colonne **ModifiedDate** .  
  
```  
MONTH(ModifiedDate)  
```  
  
 L'exemple suivant renvoie l'entier qui représente le mois de la date actuelle.  
  
```  
MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md)   
 [DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md)   
 [DATEPART &#40;expression SSIS&#41;](datepart-ssis-expression.md)   
 [DAY &#40;expression SSIS&#41;](day-ssis-expression.md)   
 [YEAR &#40;expression SSIS&#41;](year-ssis-expression.md)   
 [Fonctions &#40;SSIS Expression&#41;](functions-ssis-expression.md)  
  
  
