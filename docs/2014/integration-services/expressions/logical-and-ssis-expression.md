---
title: '&amp;&amp; (AND logique) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2dd2456bfada856e9f9e78e95a7d7561a2413dc2
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428356"
---
# <a name="ampamp-logical-and-ssis-expression"></a>&amp;&amp; (AND logique) (expression SSIS)
  Effectue une opération AND logique. L'expression renvoie la valeur TRUE si toutes les conditions s'évaluent à TRUE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a>Arguments  
 *boolean_expression1, boolean_expression2*  
 Expression valide qui renvoie TRUE, FALSE ou NULL.  
  
## <a name="result-types"></a>Types des résultats  
 DT_BOOL  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant indique le résultat de l'opérateur &&.  
  
|Résultats|Expression|Expression|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|NULL|NULL|TRUE|  
|FALSE|NULL|FALSE|  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L’exemple suivant utilise les colonnes **StandardCost** et **ListPrice** . L’exemple renvoie la valeur TRUE si la valeur de la colonne **StandardCost** est inférieure à 300 et que celle de la colonne **ListPrice** est supérieure à 500.  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 L’exemple suivant utilise les variables **SPrice** et **LPrice** au lieu de littéraux.  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>Voir aussi  
 [& &#40;AND au niveau du bit&#41; &#40;expression SSIS&#41;](bitwise-and-ssis-expression.md)   
 [Priorités et associativité des opérateurs](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md)  
  
  
