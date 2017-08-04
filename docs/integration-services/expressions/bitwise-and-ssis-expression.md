---
title: '&amp;(AND au niveau du bit) (Expression SSIS) | Documents Microsoft'
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
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6d5dad9457bbafe0218c1e71358d2c9c445f79a8
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="amp-bitwise-and-ssis-expression"></a>&amp;(AND au niveau du bit) (Expression SSIS)
  Effectue une opération AND au niveau du bit avec deux valeurs entières. Cette fonction compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si les deux bits ont pour valeur 1, le bit obtenu correspondant a pour valeur 1. Sinon, il a pour valeur 0.  
  
 Les deux conditions doivent être ou de type signed integer ou de type unsigned integer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## <a name="arguments"></a>Arguments  
 *integer_expression1, integer_expression2*  
 Toute expression valide de type de données signed integer ou unsigned integer. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 Déterminés par les types de données des deux arguments. Pour plus d’informations, consultez [Types de données Integration Services dans les expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Notes  
 Si l'une des deux conditions est NULL, le résultat de l'expression est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L’exemple suivant effectue une opération AND au niveau du bit entre les colonnes **NumberA** et **NumberB**. La colonne**NumberA** contient la valeur 3 (0000011) et la colonne **NumberB** contient la valeur 7 (00000111).  
  
```  
NumberA & NumberB  
```  
  
 L'expression renvoie la valeur 3 (00000011).  
  
 00000011  
  
 00000111  
  
 ----------\-  
  
 00000011  
  
 L’exemple suivant effectue une opération AND au niveau du bit entre les colonnes **ReorderPoint** et **SafetyStockLevel** .  
  
```  
ReorderPoint & SafetyStockLevel  
```  
  
 Si la colonne **ReorderPoint** contient la valeur 10 et la colonne **SafetyStockLevel** la valeur 8, l’expression prend la valeur 8 (00001000).  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001000  
  
 L'exemple suivant effectue une opération AND au niveau du bit entre deux entiers.  
  
```  
3 & 5   
```  
  
 L'expression renvoie la valeur 1 (00000001).  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000001  
  
## <a name="see-also"></a>Voir aussi  
 [& & &#40; AND logique &#41; &#40; Expression SSIS &#41;](../../integration-services/expressions/logical-and-ssis-expression.md)   
 [Opérateurs et associativité](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Opérateurs &#40; Expression SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
