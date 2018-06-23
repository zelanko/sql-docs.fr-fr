---
title: '&amp;&amp; (AND logique) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9f6cdb28a48a69ee1702b19918b9326ac861eb29
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040425"
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
  
## <a name="result-types"></a>Types de résultats  
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
 [& &#40;Au niveau du bit AND&#41; &#40;Expression SSIS&#41;](bitwise-and-ssis-expression.md)   
 [Opérateurs et associativité](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;Expression SSIS&#41;](operators-ssis-expression.md)  
  
  