---
title: YEAR (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], YEAR
- YEAR function
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f228aa02e5537ddd52a7acb0fe4c7d4fbb855d5b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52767880"
---
# <a name="year-ssis-expression"></a>YEAR (expression SSIS)
  Renvoie un entier qui représente la partie année d'une date.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
YEAR(date)  
```  
  
## <a name="arguments"></a>Arguments  
 *date*  
 Date à n'importe quel format de date.  
  
## <a name="result-types"></a>Types de résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 La fonction YEAR renvoie un résultat NULL si l'argument est NULL.  
  
 Un littéral de date doit être explicitement converti dans l'un des types de données date. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  L’expression ne parvient pas à valider lorsqu’un littéral de date est explicitement converti à un des types de données de date suivants : DT_DBTIMESTAMPOFFSET et DT_DBTIMESTAMP2.  
  
 L'utilisation de la fonction YEAR est plus directe mais elle est équivalente à celle de la fonction DATEPART("Year", date).  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple renvoie le nombre représentant l'année dans un littéral de date. Si le format de la date est « mm/jj/aaaa », l'exemple renvoie « 2002 ».  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 L’exemple suivant renvoie l’entier qui représente l’année dans la colonne **ModifiedDate** .  
  
```  
YEAR(ModifiedDate)  
```  
  
 L'exemple suivant renvoie l'entier qui représente l'année de la date actuelle.  
  
```  
YEAR(GETDATE())  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DATEADD &#40;expression SSIS&#41;](dateadd-ssis-expression.md)   
 [DATEDIFF &#40;expression SSIS&#41;](datediff-ssis-expression.md)   
 [DATEPART &#40;expression SSIS&#41;](datepart-ssis-expression.md)   
 [DAY &#40;expression SSIS&#41;](day-ssis-expression.md)   
 [MONTH &#40;expression SSIS&#41;](month-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
