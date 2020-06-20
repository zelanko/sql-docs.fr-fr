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
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 50d18745a064ed8d9550017ce1fcfef8c2c0805d
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969139"
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
  
  
