---
title: Accès concurrentiel au curseur (ODBC) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: da4b99f4ea20ce7c8540f45a4324321413b18183
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141573"
---
# <a name="cursor-concurrency-odbc"></a>Accès concurrentiel au curseur (ODBC)
  Les opérations de curseur, comme les types de curseurs, sont affectées par les options d'accès concurrentiel définies par l'application. Options d’accès concurrentiel sont définies à l’aide de l’option SQL_ATTR_CONCURRENCY de [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md). Les types d'accès concurrentiel sont :  
  
-   Lecture seule (SQL_CONCUR_READONLY)  
  
-   Valeurs (SQL_CONCUR_VALUES)  
  
-   Version de ligne (SQL_CONCUR_ROWVER)  
  
-   Verrou (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de curseur](cursor-properties.md)  
  
  