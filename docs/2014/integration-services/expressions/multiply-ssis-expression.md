---
title: '* (Multiplier) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '* (multiply operator)'
- multiply operator (*)
ms.assetid: d457f052-ffbb-4485-833f-f4bed4349b69
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b4814d45b0cb4184356f6a5059d33c556e239361
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52808951"
---
# <a name="-multiply-ssis-expression"></a>* (Multiplication) (expression SSIS)
  Multiplie deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
numeric_expression1 * numeric_expression2  
  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_numérique1, expression_numérique2*  
 Toute expression valide d'un type de données numérique. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types de résultats  
 Déterminés par les types de données des deux arguments. Pour plus d’informations, consultez [Types de données Integration Services dans les expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Notes  
 Si l'un des opérandes est NULL, le résultat est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant multiplie des littéraux numériques.  
  
```  
5 * 6.09  
```  
  
 L’exemple suivant multiplie les valeurs de la colonne **ListPrice** par 10 pour cent.  
  
```  
ListPrice * .10  
```  
  
 Cet exemple soustrait le résultat d’une expression de la colonne **ListPrice** . La variable **Discount%** doit figurer entre crochets car elle contient le caractère « % ». Pour plus d’informations, consultez [Identificateurs &#40;SSIS&#41;](identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Priorités et associativité des opérateurs](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md)  
  
  
