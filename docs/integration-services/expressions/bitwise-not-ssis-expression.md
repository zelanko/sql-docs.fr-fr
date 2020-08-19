---
description: ~ (NOT au niveau du bit) (expression SSIS)
title: ~ (NOT au niveau du bit) (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ae8fa8bb0aae6700d1082e52385c7d162c193b84
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430611"
---
# <a name="-bitwise-not-ssis-expression"></a>~ (NOT au niveau du bit) (expression SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Effectue une négation au niveau du bit d'un entier. Cet opérateur est applicable aux types de données entier signé et non signé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>Arguments  
 *integer_expression*  
 Toute expression valide d'un type de données integer. *integer*_*expression* est un nombre entier transformé en nombre binaire pour l’opération au niveau du bit. Pour plus d’informations, consultez [Types de données Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
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
 [Priorités et associativité des opérateurs](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
