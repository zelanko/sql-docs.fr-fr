---
title: CODEPOINT (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a5cdd95f9df8aba20b389ab92da48a884629ab82
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122639"
---
# <a name="codepoint-ssis-expression"></a>CODEPOINT (expression SSIS)
  Renvoie le point de code Unicode du caractère placé à l'extrême gauche d'une expression de caractères.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_caractère*  
 Expression de type caractère dont le caractère situé à l'extrême gauche sera évalué.  
  
## <a name="result-types"></a>Types de résultats  
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
 [Fonctions &#40;SSIS Expression&#41;](functions-ssis-expression.md)  
  
  
