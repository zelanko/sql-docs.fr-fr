---
title: SQLFetchScroll | Documents Microsoft
ms.custom: 
ms.date: 03/17/2017
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
helpviewer_keywords: SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a1f60dc7742e6b0df60390d56a6338b355a621f2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLFetchScroll** retourne un ensemble de lignes de données à l'application. La taille de l’ensemble de lignes est définie à l’aide de [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge toutes les instructions d’extraction définies (par exemple, SQL_FETCH_RELATIVE) avec les limitations suivantes :  
  
-   Si un curseur avant uniquement est défini pour l'instruction, SQL_FETCH_NEXT est requis et toute tentative d'extraction effectuée d'une autre manière retournera une erreur.  
  
-   SQL_FETCH_BOOKMARK est uniquement pris en charge pour les curseurs statiques et les curseurs de jeu de clés.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLFetchScroll des fonctionnalités de date et heure améliorées  
 Valeurs de colonne de résultat de types date/heure sont converties comme décrit dans [Conversions à partir de SQL pour C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Pour plus d’informations, consultez [Date et heure améliorations &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>Prise en charge par SQLFetchScroll des grands types CLR définis par l'utilisateur  
 **SQLFetchScroll** prend en charge les types CLR volumineux définis par l'utilisateur (UDT). Pour plus d’informations, consultez [Large CLR User-Defined Types &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLFetchScroll](http://go.microsoft.com/fwlink/?LinkId=59343)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
