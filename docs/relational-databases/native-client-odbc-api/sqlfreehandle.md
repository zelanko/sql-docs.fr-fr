---
title: SQLFreeHandle | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
caps.latest.revision: "29"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4008f18549faedee2e6ebdc00c2f2531f95dc19f
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2018
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  En mode de validation manuelle, l'appel de **SQLFreeHandle** sur un descripteur d'instruction avec une transaction ouverte provoque une restauration des modifications en attente de la base de données. L'appel de **SQLFreeHandle** sur un descripteur d'instruction ferme toujours tous les curseurs ouverts et ignore les résultats en attente, libérant toutes les ressources associées au descripteur d'instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLFreeHandle, fonction](http://go.microsoft.com/fwlink/?LinkId=59345)   
 [Détails d’implémentation API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
