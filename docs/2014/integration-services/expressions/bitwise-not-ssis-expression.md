---
title: ~ (NOT au niveau du bit) (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 655f09c1470e37f7d1503e1e3d151a734210e45c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48154319"
---
# <a name="-bitwise-not-ssis-expression"></a>~ (NOT au niveau du bit) (expression SSIS)
  Effectue une négation au niveau du bit d'un entier. Cet opérateur est applicable aux types de données entier signé et non signé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>Arguments  
 *integer_expression*  
 Toute expression valide d'un type de données integer. *integer*_*expression* est un nombre entier transformé en nombre binaire pour l’opération au niveau du bit. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types de résultats  
 Retourne le type de données *integer_expression*.  
  
## <a name="remarks"></a>Notes  
 None  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant réalise une opération NOT au niveau du bit ( ~ ) sur le nombre 170 (0000 0000 1010 1010). Le nombre est un entier signé.  
  
```  
  
~ 170  
```  
  
 L'expression renvoie la valeur -170 (1111111101010101).  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs et associativité](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;SSIS Expression&#41;](operators-ssis-expression.md)  
  
  
