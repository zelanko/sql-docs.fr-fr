---
title: + (Ajouter) (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9341cb3647db9e8e7061b1418b169c4ac4d158d5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62769625"
---
# <a name="-add-ssis"></a>+ (Addition) (SSIS)
  Additionne deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression1, numeric_ expression2*  
 Toute expression valide d'un type de données numérique.  
  
## <a name="result-types"></a>Types des résultats  
 Déterminés par les types de données des deux arguments. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="remarks"></a>Notes  
 Si l'un des opérandes est NULL, le résultat est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant additionne des littéraux numériques.  
  
```  
5 + 6.09 + 7.0  
```  
  
 L'exemple suivant additionne les valeurs des colonnes **VacationHours** et **SickLeaveHours** .  
  
```  
VacationHours + SickLeaveHours  
```  
  
 L'exemple suivant ajoute une valeur calculée à la colonne **StandardCost** . La variable **Profit%** doit figurer entre crochets car elle contient le caractère « % ». Pour plus d’informations, consultez [Identificateurs &#40;SSIS&#41;](identifiers-ssis.md).  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Priorités et associativité des opérateurs](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md)  
  
  
