---
title: () (Parenthèses) (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fca370f011d132ccd7aea9a32afbd0f7d062a270
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437156"
---
# <a name="-parentheses-ssis-expression"></a>() (Parenthèses) (expression SSIS)
  Identifie l'ordre d'évaluation des expressions. Les expressions entre parenthèses ont la priorité d'évaluation la plus élevée. L'évaluation des expressions imbriquées placées entre parenthèses commence par celle située le plus à l'intérieur, puis se poursuit jusqu'à celle située le plus à l'extérieur.  
  
 Les parenthèses permettent également de faciliter la compréhension des expressions complexes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Peut être toute expression valide.  
  
## <a name="result-types"></a>Types des résultats  
 Le type de données *expression*. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple illustre la façon dont l'utilisation des parenthèses modifie la priorité des opérateurs. La première expression totalise 100 tandis que la seconde cumule à 31.  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Priorités et associativité des opérateurs](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md)  
  
  
