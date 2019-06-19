---
title: COMME séquence d’échappement | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 65447904f32b7e0457ed807f18e942b334ddc236
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188803"
---
# <a name="like-escape-sequence"></a>Séquence d’échappement pour l’opérateur LIKE
ODBC utilise les séquences d’échappement pour la clause LIKE. La syntaxe de cette séquence d’échappement est comme suit :  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *Échappement ODBC-like* :: =  
  
 *ODBC-ÉCHAP-initiateur* escape ' *-caractère d’échappement*' *ODBC ÉCHAP-marque de fin*  
  
 *escape-character* ::= *character*  
  
 *ODBC-esc-initiator* ::= {  
  
 *ODBC ÉCHAP-marque de fin* :: =}  
  
 Pour déterminer si le pilote prend en charge la séquence d’échappement LIKE séquence, une application peut appeler **SQLGetInfo** avec le type d’information SQL_LIKE_ESCAPE_CLAUSE.
