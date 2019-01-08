---
title: LEN (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LEN function
- number of characters
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f04ce15704920ce8ac110946019883f153c57b05
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52799861"
---
# <a name="len-ssis-expression"></a>LEN (expression SSIS)
  Renvoie le nombre de caractères d'une expression de caractères. Si la chaîne comprend des espaces de début et de fin, la fonction les inclut dans le nombre. La fonction LEN renvoie la même valeur pour une chaîne donnée, que celle-ci soit composée de caractères codés sur un octet ou sur deux octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LEN(character_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_caractère*  
 Expression à évaluer.  
  
## <a name="result-types"></a>Types de résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 L’argument *character_expression* peut être d’un type de données DT_WSTR, DT_TEXT, DT_NTEXT ou DT_IMAGE. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
 Si *character_expression* est un littéral de chaîne ou une colonne de données avec le type de données DT_STR, il est implicitement converti dans le type de données DT_WSTR avant que la fonction LEN soit exécutée. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Cast &#40;expression SSIS&#41;](cast-ssis-expression.md).  
  
 Si l'argument transmis à la fonction LEN a un type de données BLOB (Binary Large Object Block), tel que DT_TEXT, DT_NTEXT ou DT_IMAGE, la fonction renvoie un nombre d'octets.  
  
 La fonction LEN renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple renvoie la longueur d'un littéral de chaîne. Le résultat obtenu est 12.  
  
```  
LEN("Ball Bearing")  
```  
  
 L'exemple suivant renvoie la différence de longueur des valeurs des colonnes **FirstName** et **LastName** .  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 Renvoie la longueur d'un nom d'ordinateur à partir de la variable système **MachineName**.  
  
```  
LEN(@MachineName)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
