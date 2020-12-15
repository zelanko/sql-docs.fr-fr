---
description: SQLFetchScroll
title: SQLFetchScroll | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c87e00b8aab4879a9fa406cc5d2d60f1573f9fc7
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97465220"
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **SQLFetchScroll** retourne un ensemble de lignes de données à l'application. La taille de l'ensemble de lignes est définie à l'aide de [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge toutes les instructions d'extraction définies (par exemple, SQL_FETCH_RELATIVE) avec les limitations suivantes :  
  
-   Si un curseur avant uniquement est défini pour l'instruction, SQL_FETCH_NEXT est requis et toute tentative d'extraction effectuée d'une autre manière retournera une erreur.  
  
-   SQL_FETCH_BOOKMARK est uniquement pris en charge pour les curseurs statiques et les curseurs de jeu de clés.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLFetchScroll des fonctionnalités de date et heure améliorées  
 Les valeurs de colonne de résultats de types date/heure sont converties comme décrit dans [conversions de SQL en C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>Prise en charge par SQLFetchScroll des grands types CLR définis par l'utilisateur  
 **SQLFetchScroll** prend en charge les types CLR volumineux définis par l'utilisateur (UDT). Pour plus d’informations, consultez [types de User-Defined CLR volumineux &#40;&#41;ODBC ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLFetchScroll, fonction](../../odbc/reference/syntax/sqlfetchscroll-function.md)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
