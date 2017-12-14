---
title: REVERSE (expression SSIS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b2a20cd5329e2d94cb4da44208e6811fd076d6cb
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="reverse-ssis-expression"></a>REVERSE (expression SSIS)
  Renvoie une expression de caractères en ordre inverse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
REVERSE(character_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *character_expression*  
 Expression de caractères à inverser.  
  
## <a name="result-types"></a>Types des résultats  
 DT_WSTR  
  
## <a name="remarks"></a>Notes  
 L’argument *character_expression* doit être du type de données DT_WSTR.  
  
 REVERSE retourne un résultat Null si *character_expression* est Null.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant utilise un littéral de chaîne. Le résultat obtenu est « ekiB niatnuoM ».  
  
```  
REVERSE("Mountain Bike")  
```  
  
 L'exemple suivant utilise une variable. Si la variable **Name** contient « VTT », le résultat obtenu est « TTV ».  
  
```  
REVERSE(@Name)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
