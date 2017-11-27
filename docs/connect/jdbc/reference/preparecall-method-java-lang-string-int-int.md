---
title: "Méthode prepareCall (java.lang.String, int, int) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerConnection.prepareCall (java.lang.String, int, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 04d36a25-7f95-4675-9690-4462671b3d67
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3549eb02cdef8284ebc0c2df949d85dc97c054e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="preparecall-method-javalangstring-int-int"></a>Méthode prepareCall (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) objet génère [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objets avec le type donné et la concurrence.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql,  
                                              int resultSetType,  
                                              int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *SQL*  
  
 A **chaîne** contenant une instruction SQL.  
  
 *resultSetType*  
  
 Un **int** qui indique le type de jeu de résultats.  
  
 *resultSetConcurrency*  
  
 Un **int** qui indique le jeu de résultats type d’accès concurrentiel.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet CallableStatement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode prepareCall est spécifiée par la méthode prepareCall de l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode prepareCall &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
