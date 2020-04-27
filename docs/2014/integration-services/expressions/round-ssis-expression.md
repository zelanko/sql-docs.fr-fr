---
title: ROUND (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bfb82476d42bf471853a66b3c93736952d876071
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62897330"
---
# <a name="round-ssis-expression"></a>ROUND (expression SSIS)
  Renvoie une expression numérique, arrondie à la longueur ou à la précision indiquée. La valeur du paramètre de longueur doit correspondre à un entier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression d'un type numérique valide. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
 *length*  
 Expression entière. Il s’agit de la précision avec laquelle *numeric_expression* est arrondie.  
  
## <a name="result-types"></a>Types des résultats  
 Type similaire à celui de *numeric*_*expression*.  
  
## <a name="remarks"></a>Notes  
 L'argument *length* doit avoir une valeur positive entière ou égale à zéro.  
  
 La fonction ROUND renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Les exemples suivants arrondissent des littéraux numériques à une longueur de trois. Le premier résultat obtenu est 137,1570, tandis que le second est 137,1580.  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
