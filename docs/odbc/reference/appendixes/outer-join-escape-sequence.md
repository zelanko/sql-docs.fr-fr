---
title: Séquence d’échappement de jointure externe | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 576fe7268ccf71a8c926f6b1124ebbf8a8c711b0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100643"
---
# <a name="outer-join-escape-sequence"></a>Séquence d’échappement pour les jointures externes
ODBC utilise les séquences d’échappement pour les jointures externes. La syntaxe de cette séquence d’échappement est comme suit :  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *ODBC outer-join-séquence d’échappement* :: =  
  
 *ODBC-ÉCHAP-initiateur* JO *jointure externe ODBC ÉCHAP-marque de fin*  
  
 *jointure externe* :: = *nom de la table* [*nom de corrélation*] {gauche &#124; droite &#124; complète}  
  
 JOINTURE externe {*nom de la table* [*nom de corrélation*] &#124; *jointure externe*} ON  
  
 *search-*  
  
 *condition*  
  
 *nom de corrélation* :: = *nom défini par l’utilisateur*  
  
 *ODBC-ÉCHAP-initiateur* :: = {}  
  
 *ODBC ÉCHAP-marque de fin* :: =}  
  
 Pour déterminer quelles parties de cette instruction sont pris en charge, une application appelle **SQLGetInfo** avec le type d’information SQL_OJ_CAPABILITIES. Pour les jointures externes, *condition de recherche* doit contenir uniquement la condition de jointure entre spécifié *noms de table*.
