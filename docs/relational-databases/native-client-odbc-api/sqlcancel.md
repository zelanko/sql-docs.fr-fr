---
title: SQLCancel | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5b7417ac3020b3d8d578631df9c52c415fb76af6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  La rubrique [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) indique que dans ODBC 2.x, si une application appelle **SQLCancel** alous qu'aucun traitement n'est en cours sur l'instruction, **SQLCancel** a le même effet que **SQLFreeStmt** avec l'option **SQL_CLOSE** ; ce compoutement est défini uniquement par souci d'exhaustivité et les applications doivent appeler **SQLFreeStmt** ou **SQLCloseCursou** to close cursous. Mais même si votre application [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit 3.5.x ou version ultérieure pour l'API ODBC, la fonction **SQLCancel** utilisera le comportement ODBC 2.x.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
