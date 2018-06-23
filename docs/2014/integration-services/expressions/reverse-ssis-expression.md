---
title: REVERSE (expression SSIS) | Microsoft Docs
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
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 02175d277793a1be7ca7d82edc4fd47b862d26f3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142757"
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
  
## <a name="result-types"></a>Types de résultats  
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
 [Fonctions &#40;Expression SSIS&#41;](functions-ssis-expression.md)  
  
  