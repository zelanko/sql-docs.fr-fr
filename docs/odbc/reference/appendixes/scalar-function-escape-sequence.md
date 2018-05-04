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
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 513df8ccd679ec2236822f780400c3cc39e37609
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
