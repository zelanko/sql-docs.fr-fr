---
title: SQLFreeStmt | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8aa28af9291b06607021209fd673869b34157f53
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144230"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
  **SQLFreeStmt** n'est pas recommandé dans ODBC 3.0 et les versions ultérieures. Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge toutes les valeurs *Option* définies pour **SQLFreeStmt**. Toutefois, [SQLCloseCursor](sqlclosecursor.md), [SQLBindParameter](sqlbindparameter.md), [SQLBindCol](sqlbindcol.md), **SQLSetDescField**et [SQLFreeHandle](sqlfreehandle.md) remplacent ou dupliquent la fonction de **SQLFreeStmt** et doivent être utilisés à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLFreeStmt, fonction](http://go.microsoft.com/fwlink/?LinkId=59346)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  