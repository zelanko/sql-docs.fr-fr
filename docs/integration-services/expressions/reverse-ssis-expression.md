---
title: REVERSE (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f5d213179d88a70c2f02436e5b1d0b1f2674bce4
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2018
ms.locfileid: "35406701"
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
  
  
