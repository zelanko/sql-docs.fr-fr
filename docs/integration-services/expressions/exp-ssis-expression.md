---
title: EXP (Expression SSIS) | Documents Microsoft
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
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6ad14b1426435034ef5f4371cc8bb6904b536798
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="exp-ssis-expression"></a>EXP (expression SSIS)
  Renvoie l'exposant en base e d'une expression numérique. La fonction EXP est complémentaire de l'action LN et est parfois appelée « antilogarithme ».  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique valide.  
  
## <a name="result-types"></a>Types des résultats  
 DT_R8  
  
## <a name="remarks"></a>Notes  
 L'expression numérique est convertie vers le type de données DT_R8 avant le calcul du l'exposant. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Le résultat obtenu est toujours un nombre positif.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Les exemples suivants appliquent la fonction EXP à des valeurs positive, négative, ainsi qu'à la valeur zéro.  
  
```  
EXP(74)  
```  
  
 Renvoie 1,373382979540176E+32.  
  
```  
EXP(-27)  
```  
  
 Renvoie 1,879528816539083E-12.  
  
```  
EXP(0)  
```  
  
 Renvoie 1.  
  
## <a name="see-also"></a>Voir aussi  
 [JOURNAL &#40; Expression SSIS &#41;](../../integration-services/expressions/log-ssis-expression.md)   
 [Fonctions &#40; Expression SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
