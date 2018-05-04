---
title: Séquence d’échappement de jointure externe | Documents Microsoft
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
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31d7ea1f4a349e2a0207481cb85ab898548bd98d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="outer-join-escape-sequence"></a>Séquence d’échappement de jointure externe
ODBC utilise les séquences d’échappement pour les jointures externes. La syntaxe de cette séquence d’échappement est comme suit :  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *ODBC outer-join-échappement* :: =  
  
 *ÉCHAP ODBC-initiateur* JO *jointure externe ODBC ÉCHAP-marque de fin*  
  
 *jointure externe* :: = *-nom de la table* [*nom de corrélation*] {gauche &#124; droite &#124; complète}  
  
 JOINTURE externe {*-nom de la table* [*nom de corrélation*] &#124; *jointure externe*} ON  
  
 *recherche-*  
  
 *condition*  
  
 *nom de corrélation* :: = *nom défini par l’utilisateur*  
  
 *ÉCHAP ODBC-initiateur* :: = {}  
  
 *Terminateur d’ÉCHAP ODBC* :: =}  
  
 Pour déterminer quelles parties de cette instruction sont pris en charge, une application appelle **SQLGetInfo** avec le type d’informations SQL_OJ_CAPABILITIES. Pour les jointures externes, *condition de recherche* doit contenir uniquement la condition de jointure entre spécifié *noms de table*.
