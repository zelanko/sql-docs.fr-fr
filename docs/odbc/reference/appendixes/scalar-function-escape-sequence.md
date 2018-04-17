---
title: Séquence d’échappement de fonction scalaire | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d334249cdbf96d056f78c454ca5f8e84873b16e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="scalar-function-escape-sequence"></a>Séquence d’échappement de fonction scalaire
ODBC utilise les séquences d’échappement pour les fonctions scalaires. La syntaxe de cette séquence d’échappement est comme suit :  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *ODBC scalaire en fonction d’échappement* :: =  
  
 *ÉCHAP ODBC-initiateur* fn *une fonction scalaire ODBC ÉCHAP-marque de fin*  
  
 *fonction scalaire* :: = *-nom de la fonction* (*-liste d’arguments*)  
  
 (Les définitions pour les éléments non terminaux *-nom de la fonction* et *-nom de la fonction* (*-liste d’arguments*) sont dérivés de la liste des fonctions scalaires dans [annexe e : les fonctions scalaires](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ÉCHAP ODBC-initiateur* :: = {}  
  
 *Terminateur d’ÉCHAP ODBC* :: =}  
  
 Pour déterminer si la source de données prend en charge les procédures et le pilote prend en charge la syntaxe d’appel de procédure ODBC, une application peut appeler **SQLGetInfo**. Pour plus d’informations, consultez [les fonctions scalaires annexe e :](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
