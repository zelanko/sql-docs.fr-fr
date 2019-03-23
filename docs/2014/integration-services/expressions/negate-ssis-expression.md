---
title: '- (Négatif) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1137fa6847cf851a6cb56ffd8a0da10032decc7a
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58384307"
---
# <a name="--negate-ssis-expression"></a>- (Négatif) (expression SSIS)
  Inverse une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Toute expression valide d’un type de données numérique. Seuls les types de données numériques signés sont pris en charge. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données *numeric_expression*.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple inverse la valeur de la variable **Counter** et ajoute le littéral numérique 50.  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Priorités et associativité des opérateurs](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md)  
  
  
