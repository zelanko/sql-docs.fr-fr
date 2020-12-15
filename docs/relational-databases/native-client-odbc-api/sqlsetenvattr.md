---
description: SQLSetEnvAttr
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ba2b49fa3e5fbc8be5ed21a42604993ce0be6755
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438692"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [Guide de référence du programmeur OLE DB](../../odbc/reference/odbc-programmer-s-reference.md) définit comment les pilotes ODBC doivent interpréter les spécifications d'attribut **SQLSetEnvAttr** à partir des applications écrites dans l'API ODBC 2.*x* ou ODBC 3.*x* . Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est conforme à ces règles.  
  
 L'un des attributs contrôlé par **SQLSetEnvAttr** indique si le regroupement de connexions sera utilisé. Si le regroupement de connexions est utilisé avec le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, il faut affecter au paramètre *DriverCompletion* la valeur SQL_DRIVER_NOPROMPT lors de la connexion à [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) ou **SQLConnect**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLSetEnvAttr fonction)](../../odbc/reference/syntax/sqlsetenvattr-function.md)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
