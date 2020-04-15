---
title: Séquence d’évasion LIKE Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 517c21f7b64fa7ceb662af9839a9fed1a1e6eff6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304920"
---
# <a name="like-escape-sequence"></a>Séquence d’échappement pour l’opérateur LIKE
ODBC utilise des séquences d’évasion pour la clause LIKE. La syntaxe de cette séquence d’évasion est la suivante :  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *ODBC-comme-évasion* ::  
  
 *ODBC-esc-initiator* escape '*escape-character*' *ODBC-esc-terminator*  
  
 *escape-character* ::- *caractère*  
  
 *ODBC-esc-initiateur* ::  
  
 *ODBC-esc-terminator* ::  
  
 Pour déterminer si le conducteur prend en charge la séquence d’évacuation LIKE, une application peut appeler **SQLGetInfo** avec le type d’information SQL_LIKE_ESCAPE_CLAUSE.
