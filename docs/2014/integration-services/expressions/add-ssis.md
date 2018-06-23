---
title: + (Ajouter) (SSIS) | Microsoft Docs
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
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b96a6e5c659925ea5eed876e1f7505997ea02b71
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141394"
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
  
## <a name="result-types"></a>Types de résultats  
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
 [Opérateurs et associativité](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;Expression SSIS&#41;](operators-ssis-expression.md)  
  
  