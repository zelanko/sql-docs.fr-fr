---
title: Niveau d’isolement des transactions cursives (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 49ad51f271e80017420db978f9cac2d867712d8c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302864"
---
# <a name="cursor-transaction-isolation-level"></a>Niveau d'isolation des transactions de curseur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le comportement de verrouillage complet des curseurs est basé sur une interaction entre les attributs de concurrence et le niveau d'isolation de la transaction défini par le client. Les clients d’ODBC établissent le niveau d’isolement des transactions à l’aide des attributs [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION ou SQL_COPT_SS_TXN_ISOLATION. Vous pouvez déterminer le comportement de verrouillage d'un environnement de curseur particulier en associant les comportements de verrouillage des options de concurrence et de niveaux d'isolation des transactions.  
  
 Les niveaux d’isolement des transactions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de curseur suivants sont pris en charge par le conducteur de Native Client ODBC :  
  
-   Lecture validée (SQL_TXN_READ_COMMITTED)  
  
-   Lecture non validée (SQL_TXN_READ_UNCOMMITTED)  
  
-   Lecture renouvelée (SQL_TXN_REPEATABLE_READ)  
  
-   Sérialisable (SQL_TXN_SERIALIZABLE)  
  
-   Instantané (SQL_TXN_SS_SNAPSHOT)  
  
 Notez que l’API ODBC spécifie des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] niveaux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supplémentaires d’isolement des transactions, mais ceux-ci ne sont pas pris en charge par ou le conducteur de l’ODBC du client autochtone.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de curseur](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
