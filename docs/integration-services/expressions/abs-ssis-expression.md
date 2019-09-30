---
title: ABS (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2d332c8cdffae320d602f0581c7641d69c31c4fa
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71297699"
---
# <a name="abs-ssis-expression"></a>ABS (expression SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
