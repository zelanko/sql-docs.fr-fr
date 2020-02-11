---
title: Niveau d’isolation des transactions de curseur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: fef68bfdb62527f7b631b8d7433e095eba4d1c88
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63207144"
---
# <a name="cursor-transaction-isolation-level"></a>Niveau d'isolation des transactions de curseur
  Le comportement de verrouillage complet des curseurs est basé sur une interaction entre les attributs de concurrence et le niveau d'isolation de la transaction défini par le client. Les clients ODBC définissent le niveau d’isolation des transactions à l’aide des attributs [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION ou SQL_COPT_SS_TXN_ISOLATION. Vous pouvez déterminer le comportement de verrouillage d'un environnement de curseur particulier en associant les comportements de verrouillage des options de concurrence et de niveaux d'isolation des transactions.  
  
 Les niveaux d’isolation des transactions de curseurs suivants [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont pris en charge par le pilote ODBC Native Client :  
  
-   Lecture validée (SQL_TXN_READ_COMMITTED)  
  
-   Lecture non validée (SQL_TXN_READ_UNCOMMITTED)  
  
-   Lecture renouvelée (SQL_TXN_REPEATABLE_READ)  
  
-   Sérialisable (SQL_TXN_SERIALIZABLE)  
  
-   Instantané (SQL_TXN_SS_SNAPSHOT)  
  
 Notez que l’API ODBC spécifie des niveaux d’isolation des transactions supplémentaires, mais ceux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -ci [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne sont pas pris en charge par ou par le pilote ODBC Native Client.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de curseur](cursor-properties.md)  
  
  
