---
title: SQLSpecialColumns | Documents Microsoft
ms.custom: ''
ms.date: 03/17/2017
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
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 41c7f599cc85d40ffffda1ee6a92791cf1be7638
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Demande lorsque les identificateurs de ligne (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** renvoie un jeu de résultats vide (aucune ligne de données) pour toute étendue autre que SQL_SCOPE_CURROW demandée. Le jeu de résultats généré indique que les colonnes ne sont valides que dans cette étendue.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les pseudo-colonnes pour les identificateurs. Le **SQLSpecialColumns** jeu de résultats identifie toutes les colonnes sous la forme SQL_PC_NOT_PSEUDO.  
  
 **SQLSpecialColumns** peut être exécutée sur un curseur statique. Toute tentative d’exécution **SQLSpecialColumns** sur un être mise à jour (commandé par keyset ou dynamic) retourne SQL_SUCCESS_WITH_INFO, indiquant le type de curseur a été modifié.  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLSpecialColumns des fonctionnalités de date et heure améliorées  
 Pour plus d’informations sur les valeurs retournées pour les colonnes DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH et DECIMAL_DIGTS pour les types date/heure, consultez [métadonnées de catalogue](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations, consultez [Date et heure améliorations &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>Prise en charge par SQLSpecialColumns des grands types CLR définis par l'utilisateur  
 **SQLSpecialColumns** prend en charge les types CLR volumineux définis par l’utilisateur (UDT). Pour plus d’informations, consultez [Large CLR User-Defined Types & #40 ; ODBC & #41 ;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLSpecialColumns, fonction](http://go.microsoft.com/fwlink/?LinkId=59371)   
 [Détails d’implémentation API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
