---
title: Dupliqué fonctionnalités | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- duplicated functions [ODBC]
- compatibility [ODBC], duplicated functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], duplicated functions
- backward compatibility [ODBC], duplicated functions
ms.assetid: 641b16bc-f791-46d8-b093-31736473fe3d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c88175f314290c06c4239a9ca855ce41512be2b9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707227"
---
# <a name="duplicated-features"></a>Fonctionnalités en doublon
ODBC 2 suivant. *x* fonctions ont été dupliquées par ODBC 3. *x* fonctions. Par conséquent, l’API ODBC 2. *x* fonctions sont déconseillées dans ODBC 3. *x*. ODBC 3. *x* fonctions sont appelées fonctions de remplacement.  
  
 Lorsqu’une application utilise un déconseillées ODBC 2. *x* (fonction) et le pilote sous-jacent est un ODBC 3. *x* pilote, le Gestionnaire de pilotes mappe l’appel de fonction à la fonction de remplacement correspondante. La seule exception à cette règle est **SQLExtendedFetch**. (Voir la note suivante à la fin du tableau suivant.) Pour plus d’informations sur ces mappages, consultez [mappage de fonctions déconseillées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) dans la section annexe g : pilote instructions pour la compatibilité descendante.  
  
 Lorsqu’une application utilise une fonction de remplacement et le pilote sous-jacent est un ODBC 2. *x* pilote, le Gestionnaire de pilotes mappe l’appel de fonction à la fonction déconseillée correspondante.  
  
|ODBC 2. *x* (fonction)|ODBC 3. *x* (fonction)|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLExtendedFetch**[1]|**SQLFetchScroll**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**, **SQLGetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**|**SQLBindParameter**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] la fonction **SQLExtendedFetch** est une fonctionnalité en double ; **SQLFetchScroll** fournit les mêmes fonctionnalités dans ODBC 3. *x*. Toutefois, le Gestionnaire de pilotes ne mappe pas **SQLExtendedFetch** à **SQLFetchScroll** lorsque vous passez par rapport à un ODBC 3. *x* pilote. Pour plus d’informations, consultez [ce que le Gestionnaire de pilotes fait](../../../odbc/reference/appendixes/what-the-driver-manager-does.md) dans la section annexe g : pilote instructions pour la compatibilité descendante. Le Gestionnaire de pilotes mappe **SQLFetchScroll** à **SQLExtendedFetch** lorsque vous passez par rapport à une API ODBC 2. *x* pilote.  
  
> [!NOTE]  
>  La fonction **SQLBindParam** est un cas spécial. **SQLBindParam** est une fonctionnalité en double. Ce n’est pas un ODBC 2 *.x* (fonction), mais une fonction qui n’est présente dans les normes Open Group et ISO. La fonctionnalité fournie par cette fonction est entièrement remplacée par celle de **SQLBindParameter**. Par conséquent, le Gestionnaire de pilotes est mappé à un appel à **SQLBindParam** à **SQLBindParameter** lorsque le pilote sous-jacent est un ODBC 3. *x* pilote. Toutefois, lorsque le pilote sous-jacent est un ODBC 2 *.x* pilote, le Gestionnaire de pilotes n’effectue pas de ce mappage.
