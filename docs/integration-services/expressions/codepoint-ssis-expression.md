---
title: CODEPOINT (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d097a135cbca0714b53797fbaa4d5357849b15c3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107684"
---
# <a name="codepoint-ssis-expression"></a>CODEPOINT (expression SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Renvoie le point de code Unicode du caractère placé à l'extrême gauche d'une expression de caractères.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_caractère*  
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
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
