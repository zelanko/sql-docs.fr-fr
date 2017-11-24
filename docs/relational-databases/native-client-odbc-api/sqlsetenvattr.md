---
title: SQLSetEnvAttr | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 868c4131a4f221f8ac567decb9833a91f5705f70
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [Guide de référence du programmeur OLE DB](http://go.microsoft.com/fwlink/?LinkId=45250) définit comment les pilotes ODBC doivent interpréter les spécifications d'attribut **SQLSetEnvAttr** à partir des applications écrites dans l'API ODBC 2.*x* ou ODBC 3.*x* . Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est conforme à ces règles.  
  
 L'un des attributs contrôlé par **SQLSetEnvAttr** indique si le regroupement de connexions sera utilisé. Si le regroupement de connexions est utilisé avec le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, il faut affecter au paramètre *DriverCompletion* la valeur SQL_DRIVER_NOPROMPT lors de la connexion à [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) ou **SQLConnect**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLSetEnvAttr, fonction](http://go.microsoft.com/fwlink/?LinkId=59369)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
