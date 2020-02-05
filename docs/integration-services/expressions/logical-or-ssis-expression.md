---
title: '|| (OR logique) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e9154b2ad6d574f251f3248903f2518e0f6b0b3d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "71289030"
---
# <a name="-logical-or-ssis-expression"></a>|| (OU logique) (expression SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
|Résultats|Expression|Expression|  
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
 [&#124; &#40;opération OR inclusive au niveau du bit&#41; &#40;expression SSIS&#41;](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)   
 [^ &#40;OR exclusif au niveau du bit&#41; &#40;expression SSIS&#41;](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)   
 [Priorités et associativité des opérateurs](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
