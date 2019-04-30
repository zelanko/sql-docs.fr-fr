---
title: SQLFreeStmt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4aa7e597bcfa80d7d45064c844986018d64617d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63190307"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
  **SQLFreeStmt** n'est pas recommandé dans ODBC 3.0 et les versions ultérieures. Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge toutes les valeurs *Option* définies pour **SQLFreeStmt**. Toutefois, [SQLCloseCursor](sqlclosecursor.md), [SQLBindParameter](sqlbindparameter.md), [SQLBindCol](sqlbindcol.md), **SQLSetDescField**et [SQLFreeHandle](sqlfreehandle.md) remplacent ou dupliquent la fonction de **SQLFreeStmt** et doivent être utilisés à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLFreeStmt, fonction](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
