---
title: ABS (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7fafc0ba09a8345e0639016aadfdef185900589d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58375260"
---
# <a name="abs-ssis-expression"></a>ABS (expression SSIS)
  Renvoie la valeur absolue d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique signée ou non signée.  
  
## <a name="result-types"></a>Types de résultats  
 Type de données de l'expression numérique envoyée à la fonction.  
  
## <a name="remarks"></a>Notes  
 La fonction ABS renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Les exemples suivants appliquent la fonction ABS à un nombre positif et à un nombre négatif. Tous les deux renvoient le résultat 1,23.  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 L'exemple suivant applique la fonction ABS à une expression qui calcule la différence entre les valeurs des variables **HighTemperature** et **LowTempature**.  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
