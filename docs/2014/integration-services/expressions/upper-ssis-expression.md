---
title: UPPER (expression SSIS) | Microsoft Docs
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
- UPPER function
- converting lowercase to uppercase
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fc7b01b83ad0fac1f5da68fcd99ab082cebe89ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144550"
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
  
## <a name="result-types"></a>Types de résultats  
 DT_WSTR  
  
## <a name="remarks"></a>Notes  
 La fonction UPPER n'est opérationnelle qu'avec le type de données DT_WSTR. Un argument *expression_caractère* qui est un littéral de chaîne ou une colonne de données avec le type de données DT_STR est implicitement converti dans le type de données DT_WSTR avant que UPPER effectue son opération. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Types de données d’Integration Services](../data-flow/integration-services-data-types.md) et [Cast &#40;expression SSIS&#41;](cast-ssis-expression.md).  
  
 La fonction UPPER renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant convertit un littéral de chaîne en caractères majuscules. Le résultat obtenu est « HELLO ».  
  
```  
UPPER("hello")  
```  
  
 L'exemple suivant transforme le premier caractère de la colonne **FirstName** en un caractère majuscule. Si l'argument **FirstName** a pour valeur « anna », le résultat obtenu est « A ». Pour plus d’informations, consultez [SUBSTRING &#40;expression SSIS&#41;](substring-ssis-expression.md).  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 L'exemple suivant convertit la valeur de la variable **PostalCode** en caractères majuscules. Si la variable **PostalCode** a pour valeur « k4b1s2 », le résultat obtenu est « K4B1S2 ».  
  
```  
UPPER(@PostalCode)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [INFÉRIEUR &#40;Expression SSIS&#41;](lower-ssis-expression.md)   
 [Fonctions &#40;Expression SSIS&#41;](functions-ssis-expression.md)  
  
  