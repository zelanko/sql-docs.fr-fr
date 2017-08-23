---
title: '- (Inverser) (Expression SSIS) | Documents Microsoft'
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
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bf561a2e4533f47e7bf6219e141c995ad4c2e60e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="--negate-ssis-expression"></a>- (Négatif) (expression SSIS)
  Inverse une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Toute expression valide d’un type de données numérique. Seuls les types de données numériques signés sont pris en charge. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données *numeric_expression*.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple inverse la valeur de la variable **Counter** et ajoute le littéral numérique 50.  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs et associativité](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40; Expression SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
