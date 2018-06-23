---
title: NULL (expression SSIS) | Microsoft Docs
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
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fef4010bd0a6c453fcf3ce69a843924a67754573
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051302"
---
# <a name="null-ssis-expression"></a>NULL (expression SSIS)
  Renvoie une valeur NULL d'un type de données demandé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a>Arguments  
 *typespec*  
 Type de données valide. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types de résultats  
 Tout type de données valide avec une valeur Null.  
  
## <a name="remarks"></a>Notes  
 La fonction NULL renvoie un résultat NULL si l'argument est NULL.  
  
 Des paramètres sont nécessaires pour demander une valeur NULL pour certains types de données. Le tableau suivant décrit ces types de données et leurs paramètres.  
  
|Type de données|Paramètre|Exemple|  
|---------------|---------------|-------------|  
|DT_STR|*charcount*<br /><br /> *codepage*|L'expression (DT_STR,30,1252) convertit 30 caractères vers le type de données DT_STR à l'aide de la page de codes 1252.|  
|DT_WSTR|*charcount*|L'expression (DT_WSTR,20) convertit 20 caractères vers le type de données DT_WSTR.|  
|DT_BYTES|*bytecount*|L'expression (DT_BYTES,50) convertit 50 octets vers le type de données DT_BYTES.|  
|DT_DECIMAL|*scale*|L'expression (DT_DECIMAL,2) convertit une valeur numérique dans le type de données DT_DECIMAL avec une échelle égale à 2.|  
|DT_NUMERIC|*precision*<br /><br /> *scale*|L'expression (DT_NUMERIC,10,3) convertit une valeur numérique dans le type de données DT_NUMERIC avec une précision de 10 et une échelle de 3.|  
|DT_TEXT|*codepage*|L'expression (DT_TEXT,1252) convertit une valeur vers le type de données DT_TEXT à l'aide de la page de codes 1252.|  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Les exemples ci-après renvoient la valeur Null des types de données suivants : DT_STR, DT_DATE et DT_BOOL.  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ISNULL &#40;Expression SSIS&#41;](null-ssis-expression.md)   
 [Fonctions &#40;Expression SSIS&#41;](functions-ssis-expression.md)  
  
  