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
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f34128df8045d69fd6e783dd3ec1a91170ed5beb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="reverse-ssis-expression"></a>REVERSE (expression SSIS)
  Renvoie une expression de caractères en ordre inverse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
REVERSE(character_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_caractère*  
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
  
## <a name="see-also"></a> Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
