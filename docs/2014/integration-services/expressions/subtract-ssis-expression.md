---
title: '- (Soustraire) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (subtract)'
- subtract operator (-)
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 82d268ed8f61085a2a829821ee3d68931f31e680
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161829"
---
# <a name="--subtract-ssis-expression"></a>- (Soustraction) (expression SSIS)
  Soustrait la deuxième expression numérique de la première.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
numeric_expression1 – numeric_expression2  
  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_numérique1, expression_numérique2*  
 Toute expression valide d'un type de données numérique. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types de résultats  
 Déterminés par les types de données des deux arguments. Pour plus d’informations, consultez [Types de données Integration Services dans les expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Notes  
 Ajoutez l'expression unaire négative entre parenthèses pour garantir que l'expression est évaluée dans l'ordre correct  
  
## <a name="remarks"></a>Notes  
 Si l'un des opérandes est NULL, le résultat est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant soustrait des littéraux numériques.  
  
```  
5 - 6.09  
```  
  
 L’exemple suivant soustrait la valeur de la colonne **StandardCost** de la valeur de la colonne **ListPrice** .  
  
```  
ListPrice - StandardCost  
```  
  
 L’exemple suivant soustrait une valeur calculée de la colonne **ListPrice** . La variable **Discount%** doit figurer entre crochets, car le nom contient le caractère %. Pour plus d’informations, consultez [Identificateurs &#40;SSIS&#41;](identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs et associativité](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;SSIS Expression&#41;](operators-ssis-expression.md)  
  
  
