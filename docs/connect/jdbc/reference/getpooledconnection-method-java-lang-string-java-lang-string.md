---
title: "getPooledConnection (méthode) (java.lang.String, java.lang.String) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnectionPoolDataSource.getPooledConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f2e6391d-9aaf-4b09-ae1c-a27c1ada6301
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c62f975b9d9176941906f3ab8b5e5d7d241d14ff
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getpooledconnection-method-javalangstring-javalangstring"></a>Méthode getPooledConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Essaie d'établir une connexion de base de données physique qui peut être utilisée en tant que connexion regroupée en fonction du nom et du mot de passe d'utilisateur donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public javax.sql.PooledConnection getPooledConnection(java.lang.String user,  
                                                      java.lang.String password)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *utilisateur*  
  
 A **chaîne** qui contient le nom d’utilisateur.  
  
 *passwword*  
  
 A **chaîne** qui contient le mot de passe.  
  
## <a name="return-value"></a>Valeur retournée  
 A [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md) objet.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode getPooledConnection est spécifiée par la méthode getPooledConnection dans l’interface javax.sql.ConnectionPoolDataSource.  
  
## <a name="see-also"></a>Voir aussi  
 [getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)   
 [Méthodes SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-methods.md)   
 [Membres de SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [SQLServerConnectionPoolDataSource, classe](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  

