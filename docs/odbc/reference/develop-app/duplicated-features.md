---
title: Caractéristiques dupliquées (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 00f5529cfbfacebcad78a0a4433e84f34034694a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300479"
---
# <a name="duplicated-features"></a>Fonctionnalités en doublon
Les fonctions ODBC *2.x* suivantes ont été dupliquées par les fonctions ODBC *3.x.* En conséquence, les fonctions ODBC *2.x* sont dépréciées dans ODBC *3.x*. Les fonctions ODBC *3.x* sont appelées fonctions de remplacement.  
  
 Lorsqu’une application utilise une fonction ODBC *2.x* dépréciée et que le pilote sous-jacent est un pilote ODBC *3.x,* le Driver Manager cartographie l’appel de fonction à la fonction de remplacement correspondante. La seule exception à cette règle est **SQLExtendedFetch**. (Voir la note de bas de page à la fin de la table suivante.) Pour plus d’informations sur ces cartographies, voir [Mapping Deprecated Functions](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) in Annexe G: Driver Guidelines for Backward Compatibility.  
  
 Lorsqu’une application utilise une fonction de remplacement et que le conducteur sous-jacent est un pilote ODBC *2.x,* le Driver Manager cartographie l’appel de fonction à la fonction amortie correspondante.  
  
|Fonction ODBC *2.x*|Fonction ODBC *3.x*|  
|-------------------------|-------------------------|  
|**SQLAllocConnect (SQLAllocConnect)**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**Sqlerror**|**SQLGetDiagRec**|  
|**SQLExtendedFetch**[1]|**SQLFetchScroll**|  
|**SQLFreeConnect (en anglais)**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLGetConnectOption (SQLGetConnectOption)**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**, **SQLGetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam (SQLSetParam)**|**SQLBindParameter**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransacte**|**SQLEndTran**|  
  
 [1] La fonction **SQLExtendedFetch** est une fonctionnalité dupliquée; **SQLFetchScroll** offre la même fonctionnalité dans ODBC *3.x*. Toutefois, le gestionnaire de conducteur ne cartographie pas **SQLExtendedFetch** à **SQLFetchScroll** lorsqu’il va à l’encontre d’un conducteur ODBC *3.x.* Pour plus d’informations, voir [Ce que le gestionnaire de conducteur fait](../../../odbc/reference/appendixes/what-the-driver-manager-does.md) à l’annexe G: Lignes directrices du conducteur pour la compatibilité vers l’arrière. Le gestionnaire de conducteur cartographie **SQLFetchScroll** à **SQLExtendedFetch** lorsqu’il va à l’encontre d’un conducteur ODBC *2.x.*  
  
> [!NOTE]
>  La fonction **SQLBindParam** est un cas particulier. **SQLBindParam** est une fonctionnalité dupliquée. Il ne s’agit pas d’une fonction ODBC *2.x,* mais d’une fonction qui est présente dans les normes Open Group et ISO. La fonctionnalité fournie par cette fonction est complètement subsumée par celle de **SQLBindParameter**. Par conséquent, le gestionnaire de conducteur passe en photo un appel à **SQLBindParam** à **SQLBindParameter** lorsque le conducteur sous-jacent est un conducteur ODBC *3.x.* Toutefois, lorsque le conducteur sous-jacent est un pilote ODBC *2.x,* le gestionnaire de conducteur n’effectue pas cette cartographie.
