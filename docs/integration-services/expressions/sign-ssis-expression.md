---
title: SIGN (Expression SSIS) | Documents Microsoft
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
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3a926bddda6c86a7930a349915cc2a77602448b4
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="sign-ssis-expression"></a>SIGN (expression SSIS)
  Renvoie le nombre positif (+1), le nombre négatif (-1) ou zéro (0) selon le signe d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique signée valide. Pour plus d’informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 La fonction SIGN renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant renvoie le signe d'un littéral numérique. Le résultat obtenu est -1.  
  
```  
SIGN(-123.45)  
```  
  
 L’exemple suivant retourne le signe du résultat de la soustraction de la colonne **StandardCost** de la colonne **DealerPrice** .  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40; Expression SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

