---
title: Accès concurrentiel au curseur (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c5e18839b74637311edfba3cd75ac3f4dfd7214
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408348"
---
# <a name="cursor-concurrency-odbc"></a>Accès concurrentiel au curseur (ODBC)
  Les opérations de curseur, comme les types de curseurs, sont affectées par les options d'accès concurrentiel définies par l'application. Options d’accès concurrentiel sont définies à l’aide de l’option SQL_ATTR_CONCURRENCY de [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md). Les types d'accès concurrentiel sont :  
  
-   Lecture seule (SQL_CONCUR_READONLY)  
  
-   Valeurs (SQL_CONCUR_VALUES)  
  
-   Version de ligne (SQL_CONCUR_ROWVER)  
  
-   Verrou (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de curseur](cursor-properties.md)  
  
  
