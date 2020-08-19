---
description: '&amp;&amp; (AND logique) (expression SSIS)'
title: '&amp;&amp; (AND logique) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
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
ms.openlocfilehash: abb14eae98abaad9ebaaf70331abd42300ee4eee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425401"
---
# <a name="ampamp-logical-and-ssis-expression"></a>&amp;&amp; (AND logique) (expression SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


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
|false|true|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|NULL|NULL|true|  
|FALSE|NULL|false|  
  
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
 [& &#40;AND au niveau du bit&#41; &#40;expression SSIS&#41;](../../integration-services/expressions/bitwise-and-ssis-expression.md)   
 [Priorités et associativité des opérateurs](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
