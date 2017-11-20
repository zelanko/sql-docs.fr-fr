---
title: ~ (Not au niveau du bit) (Expression SSIS) | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 398f902d224f49e00b3fdc62bf39300ba180fda8
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="-bitwise-not-ssis-expression"></a>~ (NOT au niveau du bit) (expression SSIS)
  Effectue une négation au niveau du bit d'un entier. Cet opérateur est applicable aux types de données entier signé et non signé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>Arguments  
 *integer_expression*  
 Toute expression valide d'un type de données integer. *integer*_*expression* est un nombre entier transformé en nombre binaire pour l’opération au niveau du bit. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données *integer_expression*.  
  
## <a name="remarks"></a>Notes  
 Aucun  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant réalise une opération NOT au niveau du bit ( ~ ) sur le nombre 170 (0000 0000 1010 1010). Le nombre est un entier signé.  
  
```  
  
~ 170  
```  
  
 L'expression renvoie la valeur -170 (1111111101010101).  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs et associativité](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40; Expression SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

