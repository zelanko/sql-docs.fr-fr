---
title: SQLGetCursorName | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 998baf06bb24de7bb3b76f55045ebe16573a72c5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Si l'application ne spécifie pas de nom de curseur, le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client en génère un pour l'application lors de la génération du curseur. L'application peut utiliser **SQLGetCursorName** pour récupérer le nom du curseur défini par le pilote pour les instructions UPDATE et DELETE positionnées. L'application n'a pas besoin d'appeler **SQLSetCursorName** pour tirer parti des instructions de manipulation de données positionnées.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLGetCursorName, fonction](http://go.microsoft.com/fwlink/?LinkId=59349)   
 [Détails d’implémentation API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
