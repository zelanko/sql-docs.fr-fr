---
title: Niveau d’isolation des transactions de curseur | Microsoft Docs
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 92d9eb8bb09065290c99f3cb9894208a7613b984
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73784100"
---
# <a name="cursor-transaction-isolation-level"></a>Niveau d'isolation des transactions de curseur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le comportement de verrouillage complet des curseurs est basé sur une interaction entre les attributs de concurrence et le niveau d'isolation de la transaction défini par le client. Les clients ODBC définissent le niveau d’isolation des transactions à l’aide des attributs [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION ou SQL_COPT_SS_TXN_ISOLATION. Vous pouvez déterminer le comportement de verrouillage d'un environnement de curseur particulier en associant les comportements de verrouillage des options de concurrence et de niveaux d'isolation des transactions.  
  
 Les niveaux d’isolation des transactions de curseurs suivants sont pris en charge par le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client :  
  
-   Lecture validée (SQL_TXN_READ_COMMITTED)  
  
-   Lecture non validée (SQL_TXN_READ_UNCOMMITTED)  
  
-   Lecture renouvelée (SQL_TXN_REPEATABLE_READ)  
  
-   Sérialisable (SQL_TXN_SERIALIZABLE)  
  
-   Instantané (SQL_TXN_SS_SNAPSHOT)  
  
 Notez que l’API ODBC spécifie des niveaux d’isolation des transactions supplémentaires, mais ceux-ci ne sont pas pris en charge par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de curseur](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
