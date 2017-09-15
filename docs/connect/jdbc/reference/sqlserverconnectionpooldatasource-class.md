---
title: Classe SQLServerConnectionPoolDataSource | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b00e5a90-2af7-4d04-8ef8-256183777dcf
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 82712fa541d958527c409d5a347b69f37d5e642f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverconnectionpooldatasource-class"></a>Classe SQLServerConnectionPoolDataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente des connexions de bases de données physiques pour les gestionnaires de regroupement de connexions.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
 **Implémente :** javax.sql.ConnectionPoolDataSource  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerConnectionPoolDataSource  
```  
  
## <a name="remarks"></a>Notes  
 SQLServerConnectionPoolDataSource est généralement utilisée dans les environnements de serveur d’applications Java qui prennent en charge le regroupement de connexions intégrée et requièrent un ConnectionPoolDataSource fournir des connexions physiques tels que Java Platform, Enterprise Edition (Java Serveurs d’applications Java EE) qui fournissent les API JDBC 3.0 spécification de regroupement de connexions.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [Référence d’API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
