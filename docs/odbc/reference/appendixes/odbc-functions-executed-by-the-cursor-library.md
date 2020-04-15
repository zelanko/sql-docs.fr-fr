---
title: Fonctions ODBC exécutées par la Bibliothèque cursor (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], functions
- functions [ODBC], cursor library
- ODBC functions [ODBC], cursor library
- ODBC cursor library [ODBC], functions
ms.assetid: 2f1d3386-7e59-4d55-a5b4-3440b61343a3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70fb48a8764a913ea4c2376c1a44bcd8712e7d29
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298229"
---
# <a name="odbc-functions-executed-by-the-cursor-library"></a>Fonctions ODBC exécutées par la bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 La bibliothèque de curseurs exécute les fonctions suivantes. Lorsqu’une application appelle une fonction dans cette liste, le gestionnaire de conducteur invoque la bibliothèque de curseurs, et non le conducteur. Notez que la bibliothèque de curseur peut appeler le conducteur lors de l’exécution de la fonction.  
  
|||  
|-|-|  
|**SQLBindCol**|**SQLGetStmtOption**|  
|**SQLBindParam (SQLBindParam)**|**SQLNativeSql**|  
|**SQLBindParameter**|**SQLNumParams**|  
|**SQLCloseCursor**|**SQLParamOptions**|  
|**SQLEndTran**|**SQLRowCount**|  
|**SQLExtendedFetch**|**SQLSetConnectAttr**|  
|**SQLFetchScroll**|**SQLSetConnectOption**|  
|**SQLFreeHandle**|**SQLSetDescField**|  
|**SQLFreeStmt**|**SQLSetDescRec**|  
|**SQLGetData**|**SQLSetPos**|  
|**SQLGetDescField**|**SQLSetScrollOptions**|  
|**SQLGetDescRec**|**SQLSetStmtAttr**|  
|**SQLGetFunctions**|**SQLSetStmtOption**|  
|**SQLGetInfo**|**SQLTransacte**|  
|**SQLGetStmtAttr**||
