---
title: Séquence d’évasion de jointure extérieure (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37ce446328d263f492cdfd369f6e8f9f64fe6dfc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303610"
---
# <a name="outer-join-escape-sequence"></a>Séquence d’échappement pour les jointures externes
ODBC utilise des séquences d’évasion pour les jointures extérieures. La syntaxe de cette séquence d’évasion est la suivante :  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *ODBC-outer-join-escape* ::  
  
 *ODBC-esc-initiateur* oj *outer-join ODBC-esc-terminator*  
  
 *l’extérieur-join* ::md *nom de table* [ nom de*corrélation*] 'LEFT &#124; RIGHT &#124; FULL'  
  
 OUTER JOINMD*nom de table* [ nom de*corrélation*] *&#124;'extérieur-join*- ON  
  
 *recherche-*  
  
 *Condition*  
  
 *nom de corrélation* ::- *nom défini par l’utilisateur*  
  
 *ODBC-esc-initiateur* ::  
  
 *ODBC-esc-terminator* ::  
  
 Pour déterminer quelles parties de cette déclaration sont prises en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_OJ_CAPABILITIES. Pour les jointures extérieures, *l’état de recherche* ne doit contenir que l’état de jointure entre les *noms de table*spécifiés.
