---
title: LN (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LN function
- natural logarithm of expression [Integration Services]
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 521ed3f1c817f687bfbddc497f638ee4eed4a834
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62897546"
---
# <a name="ln-ssis-expression"></a>LN (expression SSIS)
  Renvoie le logarithme népérien d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LN(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique valide non négative et différente de zéro.  
  
## <a name="result-types"></a>Types de résultats  
 DT_R8  
  
## <a name="remarks"></a>Notes  
 L'expression numérique est convertie vers le type de données DT_R8 avant le calcul du logarithme. Pour plus d’informations, consultez [Types de données d’Integration Services](../data-flow/integration-services-data-types.md).  
  
 Si l’argument *numeric_expression* donne une valeur inférieure ou égale à zéro, le résultat obtenu est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant utilise un littéral numérique. La fonction renvoie la valeur 3,737766961828337.  
  
```  
LN(42)  
```  
  
 L'exemple suivant utilise la colonne **Length**. Si la valeur de la colonne est 53,99, la fonction renvoie 3,9887988442302.  
  
```  
LN(Length)   
```  
  
 L'exemple suivant utilise la variable **Length**. La variable doit être d'un type de données numérique ou l'expression doit comprendre une conversion explicite vers un type de données numérique. Si la variable **Length** a pour valeur 234,567, la fonction renvoie 5,45774126708797.  
  
```  
LN(@Length)   
```  
  
## <a name="see-also"></a>Voir aussi  
 [LOG &#40;expression SSIS&#41;](log-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
