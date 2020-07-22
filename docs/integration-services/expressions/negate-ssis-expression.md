---
title: '- (Négatif) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9322d5a25b8b65432e83ddeac03f486722a50b7c
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86911790"
---
# <a name="--negate-ssis-expression"></a>- (Négatif) (expression SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Inverse une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Toute expression valide d’un type de données numérique. Seuls les types de données numériques signés sont pris en charge. Pour plus d’informations, consultez [Types de données Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données *numeric_expression*.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple inverse la valeur de la variable **Counter** et ajoute le littéral numérique 50.  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Priorités et associativité des opérateurs](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
