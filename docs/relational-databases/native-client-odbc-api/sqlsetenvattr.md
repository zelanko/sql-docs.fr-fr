---
title: SQLSetEnvAttr | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 315a34127e5ff7d9a23f24fd37de23eb7dffef8a
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012392"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [Guide de référence du programmeur OLE DB](https://go.microsoft.com/fwlink/?LinkId=45250) définit comment les pilotes ODBC doivent interpréter les spécifications d'attribut **SQLSetEnvAttr** à partir des applications écrites dans l'API ODBC 2.*x* ou ODBC 3.*x* . Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est conforme à ces règles.  
  
 L'un des attributs contrôlé par **SQLSetEnvAttr** indique si le regroupement de connexions sera utilisé. Si le regroupement de connexions est utilisé avec le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, il faut affecter au paramètre *DriverCompletion* la valeur SQL_DRIVER_NOPROMPT lors de la connexion à [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) ou **SQLConnect**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLSetEnvAttr fonction)](https://go.microsoft.com/fwlink/?LinkId=59369)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
