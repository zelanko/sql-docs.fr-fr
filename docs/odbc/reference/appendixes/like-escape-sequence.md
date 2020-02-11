---
title: COMME une séquence d’échappement | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 629ceaf666ae732d0838a216272c308dcb5b5658
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041711"
---
# <a name="like-escape-sequence"></a>Séquence d’échappement pour l’opérateur LIKE
ODBC utilise des séquences d’échappement pour la clause LIKE. La syntaxe de cette séquence d’échappement est la suivante :  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *ODBC-like-Escape* :: =  
  
 *ODBC-ESC-initiateur* Echap'*Escape-caractère*' *ODBC-ESC-terminateur*  
  
 *caractère d’échappement* :: = *caractère*  
  
 *ODBC-Echap-Initiator* :: = {  
  
 *ODBC-ESC-terminateur* :: =}  
  
 Pour déterminer si le pilote prend en charge la séquence d’échappement LIKE, une application peut appeler **SQLGetInfo** avec le type d’informations SQL_LIKE_ESCAPE_CLAUSE.
