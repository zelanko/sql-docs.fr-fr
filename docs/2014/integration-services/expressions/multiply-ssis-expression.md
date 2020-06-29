---
title: '* (Multiplier) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '* (multiply operator)'
- multiply operator (*)
ms.assetid: d457f052-ffbb-4485-833f-f4bed4349b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c1606359b0757b24d0f9c2eee2bc2b3d76df334
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437206"
---
# <a name="-multiply-ssis-expression"></a>* (Multiplication) (expression SSIS)
  Multiplie deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
numeric_expression1 * numeric_expression2  
  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_numérique1, expression_numérique2*  
 Toute expression valide d'un type de données numérique. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 Déterminés par les types de données des deux arguments. Pour plus d’informations, consultez [Types de données Integration Services dans les expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Notes  
 Si l'un des opérandes est NULL, le résultat est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant multiplie des littéraux numériques.  
  
```  
5 * 6.09  
```  
  
 L’exemple suivant multiplie les valeurs de la colonne **ListPrice** par 10 pour cent.  
  
```  
ListPrice * .10  
```  
  
 Cet exemple soustrait le résultat d’une expression de la colonne **ListPrice** . La variable **Discount%** doit figurer entre crochets car elle contient le caractère « % ». Pour plus d’informations, consultez [Identificateurs &#40;SSIS&#41;](identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Priorités et associativité des opérateurs](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md)  
  
  
