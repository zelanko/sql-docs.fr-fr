---
title: UPPER (Expression SSIS) | Documents Microsoft
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
- UPPER function
- converting lowercase to uppercase
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1764b39b0242ce7e23d56c9c74f7b953f45009b2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="upper-ssis-expression"></a>UPPER (expression SSIS)
  Renvoie une chaîne de caractères après avoir converti les caractères minuscules en caractères majuscules.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UPPER(character_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_caractère*  
 Expression de type caractère à convertir en caractères majuscules.  
  
## <a name="result-types"></a>Types des résultats  
 DT_WSTR  
  
## <a name="remarks"></a>Notes  
 La fonction UPPER n'est opérationnelle qu'avec le type de données DT_WSTR. Un argument *expression_caractère* qui est un littéral de chaîne ou une colonne de données avec le type de données DT_STR est implicitement converti dans le type de données DT_WSTR avant que UPPER effectue son opération. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Types de données d’Integration Services](../../integration-services/data-flow/integration-services-data-types.md) et [Cast &#40;expression SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 La fonction UPPER renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant convertit un littéral de chaîne en caractères majuscules. Le résultat obtenu est « HELLO ».  
  
```  
UPPER("hello")  
```  
  
 L'exemple suivant transforme le premier caractère de la colonne **FirstName** en un caractère majuscule. Si l'argument **FirstName** a pour valeur « anna », le résultat obtenu est « A ». Pour plus d’informations, consultez [SUBSTRING &#40;expression SSIS&#41;](../../integration-services/expressions/substring-ssis-expression.md).  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 L'exemple suivant convertit la valeur de la variable **PostalCode** en caractères majuscules. Si la variable **PostalCode** a pour valeur « k4b1s2 », le résultat obtenu est « K4B1S2 ».  
  
```  
UPPER(@PostalCode)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [INFÉRIEUR &#40; Expression SSIS &#41;](../../integration-services/expressions/lower-ssis-expression.md)   
 [Fonctions &#40; Expression SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

