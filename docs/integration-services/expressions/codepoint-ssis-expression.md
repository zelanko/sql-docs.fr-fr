---
title: CODEPOINT (Expression SSIS) | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: af56c3de2d4e285960b9e6631084b20440396eb3
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="codepoint-ssis-expression"></a>CODEPOINT (expression SSIS)
  Renvoie le point de code Unicode du caractère placé à l'extrême gauche d'une expression de caractères.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *character_expression*  
 Expression de type caractère dont le caractère situé à l'extrême gauche sera évalué.  
  
## <a name="result-types"></a>Types des résultats  
 DT_UI2  
  
## <a name="remarks"></a>Notes  
 *character_expression* doit être du type de données DT_WSTR.  
  
 CODEPOINT retourne un résultat Null si *character_expression* est Null ou est une chaîne vide.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant utilise un littéral de chaîne. Le résultat obtenu est 77, soit le point de code Unicode de M.  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 L'exemple suivant utilise une variable. Si **Name** a pour valeur « Tout-terrain », le résultat obtenu est 84, soit le point de code Unicode de T.  
  
```  
CODEPOINT(@Name)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40; Expression SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

