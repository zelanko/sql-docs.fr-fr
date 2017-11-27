---
title: "Méthode prepareCall (java.lang.String, int, int, int) | Documents Microsoft"
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
apiname: SQLServerConnection.prepareCall (java.lang.String, int, int, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 81104fd5-75b0-4540-9f48-c3dbf59a8564
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67154127b6428a0b41960b6b822c3e727d6224f5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="preparecall-method-javalangstring-int-int-int"></a>Méthode prepareCall (java.lang.String, int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) objet génère [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objets avec le type donné, la concurrence et la mise en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql,  
                                              int nType,  
                                              int nConcur,  
                                              int nHold)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *SQL*  
  
 A **chaîne** contenant une instruction SQL.  
  
 *%nLes*  
  
 Un **int** qui indique le type de jeu de résultats.  
  
 *nConcur*  
  
 Un **int** qui indique le jeu de résultats type d’accès concurrentiel.  
  
 *nHold*  
  
 Un **int** qui indique le jeu de résultats mise en attente.  
  
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
  
  
