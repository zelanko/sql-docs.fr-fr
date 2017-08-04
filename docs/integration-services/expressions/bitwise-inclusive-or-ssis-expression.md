---
title: "| (Opérateur de bits OR inclusif) (Expression SSIS) | Documents Microsoft"
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
- '| (bitwise inclusive OR)'
- bitwise inclusive OR (|)
ms.assetid: 4dce9eb2-3680-4adc-81a3-816ea52cef49
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 90a8167d52a50c569418af86d4f36526ad3482c0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="-bitwise-inclusive-or-ssis-expression"></a>| (OR inclusive au niveau du bit) (expression SSIS)
  Effectue une opération OR au niveau du bit avec deux valeurs entières. Cette fonction compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si l'un des deux bits a pour valeur 1, le bit obtenu correspondant a pour valeur 1. Sinon, il a pour valeur zéro (0).  
  
 Les deux conditions doivent être de type de données signed integer ou unsigned integer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
integer_expression1 | integer_expression2  
  
```  
  
## <a name="arguments"></a>Arguments  
 *integer_expression1, integer_expression2*  
 Toute expression valide de type de données signed integer ou unsigned integer. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 Déterminés par les types de données des deux arguments. Pour plus d’informations, consultez [Types de données Integration Services dans les expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Notes  
 Si l'une des deux conditions est NULL, le résultat de l'expression est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L’exemple suivant effectue une opération OR inclusive au niveau du bit entre les variables **NumberA** et **NumberB**. La variable**NumberA** contient la valeur 3 (00000011) et la variable **NumberB** contient la valeur 9 (00001001).  
  
```  
@NumberA | @NumberB  
```  
  
 L'expression renvoie la valeur 11 (00001011).  
  
 00000011  
  
 00001001  
  
 ----------\-  
  
 00001011  
  
 L’exemple suivant effectue une opération OR inclusive au niveau du bit entre les colonnes **ReorderPoint** et **SafetyStockLevel** .  
  
```  
ReorderPoint | SafetyStockLevel  
```  
  
 Si la colonne **ReorderPoint** contient la valeur 10 et la colonne **SafetyStockLevel** la valeur 8, l’expression renvoie la valeur 10 (00001010).  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001010  
  
 L'exemple suivant effectue une opération OR inclusive au niveau du bit entre deux entiers.  
  
```  
3 | 5   
```  
  
 L'expression renvoie la valeur 7 (00000111).  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000111  
  
## <a name="see-also"></a>Voir aussi  
 [&#124; &#124; &#40; OR logique &#41; &#40; Expression SSIS &#41;](../../integration-services/expressions/logical-or-ssis-expression.md)   
 [^ &#40; Opérateur de bits OR exclusif &#41; &#40; Expression SSIS &#41;](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)   
 [Opérateurs et associativité](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40; Expression SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
