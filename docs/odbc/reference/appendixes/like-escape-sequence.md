---
title: "COMME séquence d’échappement | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 49004343a4081db0c617b97b09570bd7557f441e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="like-escape-sequence"></a>COMME séquence d’échappement
ODBC utilise les séquences d’échappement pour la clause LIKE. La syntaxe de cette séquence d’échappement est comme suit :  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *Type ODBC-échappement* :: =  
  
 *ÉCHAP ODBC-initiateur* escape '*-caractère d’échappement*' *ODBC ÉCHAP-marque de fin*  
  
 *caractères d’échappement* :: = *caractère*  
  
 *ÉCHAP ODBC-initiateur* :: = {}  
  
 *Terminateur d’ÉCHAP ODBC* :: =}  
  
 Pour déterminer si le pilote prend en charge la séquence d’échappement LIKE séquence, une application peut appeler **SQLGetInfo** avec le type d’informations SQL_LIKE_ESCAPE_CLAUSE.
