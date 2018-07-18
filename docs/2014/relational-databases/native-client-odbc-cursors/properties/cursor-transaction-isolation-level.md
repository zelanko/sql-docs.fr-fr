---
title: Niveau d’Isolation de transactions de curseur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 045ad6a09adc3ff4127c04c4dae4281dd413c5b8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430888"
---
# <a name="cursor-transaction-isolation-level"></a>Niveau d'isolation des transactions de curseur
  Le comportement de verrouillage complet des curseurs est basé sur une interaction entre les attributs de concurrence et le niveau d'isolation de la transaction défini par le client. Clients ODBC définissent la transaction d’isolation au niveau en utilisant le [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) attributs SQL_ATTR_TXN_ISOLATION ou SQL_COPT_SS_TXN_ISOLATION. Vous pouvez déterminer le comportement de verrouillage d'un environnement de curseur particulier en associant les comportements de verrouillage des options de concurrence et de niveaux d'isolation des transactions.  
  
 Les niveaux d’isolation de transaction curseur suivants sont pris en charge par le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client :  
  
-   Lecture validée (SQL_TXN_READ_COMMITTED)  
  
-   Lecture non validée (SQL_TXN_READ_UNCOMMITTED)  
  
-   Lecture renouvelée (SQL_TXN_REPEATABLE_READ)  
  
-   Sérialisable (SQL_TXN_SERIALIZABLE)  
  
-   Instantané (SQL_TXN_SS_SNAPSHOT)  
  
 Notez que l’API ODBC spécifie des niveaux d’isolation de transaction supplémentaires, mais ils ne sont pas pris en charge par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de curseur](cursor-properties.md)  
  
  
