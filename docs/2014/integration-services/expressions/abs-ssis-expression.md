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
ms.openlocfilehash: 79e0c524c2b74b76921f8eafe6f8e4cc47a9f6b5
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966699"
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
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
