---
title: '|| (Ou logique) (Expression SSIS) | Documents Microsoft'
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
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c369d66dbfdfefa0249ef0e479266bf17cf8f7d6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="-logical-or-ssis-expression"></a>|| (OU logique) (expression SSIS)
  Effectue une opération OR logique. L'expression renvoie la valeur TRUE si au moins une des deux conditions s'évalue à TRUE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a>Arguments  
 *boolean_expression1, boolean_expression2*  
 Expression valide qui renvoie TRUE, FALSE ou NULL.  
  
## <a name="result-types"></a>Types des résultats  
 DT_BOOL  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant indique le résultat de l'opérateur « || »  
  
|Résultat|Expression|Expression|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## <a name="ssis-expression-examples"></a>Exemples d'expressions SSIS  
 L'exemple suivant utilise les colonnes **StandardCost** et **ListPrice** . L'exemple renvoie la valeur TRUE si la valeur de la colonne **StandardCost** est inférieure à 300 ou que celle de la colonne **ListPrice** est supérieure à 500.  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 L'exemple suivant utilise les variables **SPrice** et **LPrice** au lieu de littéraux numériques.  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#124; &#40; Opérateur de bits OR inclusif &#41; &#40; Expression SSIS &#41;](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)   
 [^ &#40; Opérateur de bits OR exclusif &#41; &#40; Expression SSIS &#41;](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)   
 [Opérateurs et associativité](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40; Expression SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
