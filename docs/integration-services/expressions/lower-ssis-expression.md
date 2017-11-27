---
title: LOWER (Expression SSIS) | Documents Microsoft
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
- converting uppercase to lowercase
- LOWER function
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1d8887035d26ba829dae2153e4e9261836ada70d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="lower-ssis-expression"></a>LOWER (expression SSIS)
  Renvoie une expression de caractères après avoir transformé les caractères majuscules en caractères minuscules.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LOWER(character_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *character_expression*  
 Expression de type caractère à convertir en caractères minuscules.  
  
## <a name="result-types"></a>Types des résultats  
 DT_WSTR  
  
## <a name="remarks"></a>Notes  
 La fonction LOWER n'est opérationnelle qu'avec le type de données DT_WSTR. Un argument *character_expression* qui est un littéral de chaîne ou une colonne de données avec le type de données DT_STR est implicitement converti dans le type de données DT_WSTR avant que UPPER effectue son opération. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Types de données d’Integration Services](../../integration-services/data-flow/integration-services-data-types.md) et [Cast &#40;expression SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 La fonction LOWER renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant convertit un littéral de chaîne en caractères minuscules. Le résultat obtenu est « new york ».  
  
```  
LOWER("New York")  
```  
  
 L’exemple suivant convertit tous les caractères de la colonne d’entrée **Color** , à l’exception du premier caractère, en caractères minuscules. Si la colonne Color a pour valeur JAUNE, le résultat obtenu est « Jaune ». Pour plus d’informations, consultez [SUBSTRING &#40;expression SSIS&#41;](../../integration-services/expressions/substring-ssis-expression.md).  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 L’exemple suivant convertit la valeur de la variable **CityName** en caractères minuscules.  
  
```  
LOWER(@CityName)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SUPÉRIEUR &#40; Expression SSIS &#41;](../../integration-services/expressions/upper-ssis-expression.md)   
 [Fonctions &#40; Expression SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

