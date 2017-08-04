---
title: ABS (Expression SSIS) | Documents Microsoft
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
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cf829866d0e55798b612af57a8d8c6cef6d3fcd4
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

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
  
## <a name="result-types"></a>Types des résultats  
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
 [Fonctions &#40; Expression SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
