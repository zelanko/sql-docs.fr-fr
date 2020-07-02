---
title: SQLSpecialColumns | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bc1a7b18be85d1b959ba7f18b62b3e5807cc238d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751814"
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Lors de la demande d’identificateurs de ligne (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** retourne un jeu de résultats vide (aucune ligne de données) pour toute étendue demandée autre que SQL_SCOPE_CURROW. Le jeu de résultats généré indique que les colonnes ne sont valides que dans cette étendue.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les pseudo-colonnes pour les identificateurs. Le jeu de résultats **SQLSpecialColumns** identifie toutes les colonnes comme SQL_PC_NOT_PSEUDO.  
  
 **SQLSpecialColumns** peut être exécuté sur un curseur statique. Une tentative d’exécution de **SQLSpecialColumns** sur un qui peut être mis à jour (KEYSET ou Dynamic) retourne SQL_SUCCESS_WITH_INFO indiquant que le type de curseur a été modifié.  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLSpecialColumns des fonctionnalités de date et heure améliorées  
 Pour plus d’informations sur les valeurs retournées pour les colonnes DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH et DECIMAL_DIGTS pour les types date/heure, consultez [métadonnées de catalogue](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations générales, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>Prise en charge par SQLSpecialColumns des grands types CLR définis par l'utilisateur  
 **SQLSpecialColumns** prend en charge les types CLR volumineux définis par l’utilisateur (UDT). Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLSpecialColumns fonction)](https://go.microsoft.com/fwlink/?LinkId=59371)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
