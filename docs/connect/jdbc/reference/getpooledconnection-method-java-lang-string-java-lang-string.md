---
title: getPooledConnection, méthode (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnectionPoolDataSource.getPooledConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f2e6391d-9aaf-4b09-ae1c-a27c1ada6301
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d6c21fa5df3545b641ccb935c53f6d7a689f580
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702947"
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
 *user*  
  
 **Chaîne** qui contient le nom de l’utilisateur.  
  
 *passwword*  
  
 **Chaîne** qui contient le mot de passe.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes   
 Cette méthode getPooledConnection est spécifiée par la méthode getPooledConnection dans l’interface javax.sql.ConnectionPoolDataSource.  
  
## <a name="see-also"></a> Voir aussi  
 [getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)   
 [SQLServerConnectionPoolDataSource, méthodes](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-methods.md)   
 [SQLServerConnectionPoolDataSource, membres](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [SQLServerConnectionPoolDataSource, classe](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  
