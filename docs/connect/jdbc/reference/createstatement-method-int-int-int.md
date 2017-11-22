---
title: "Méthode (int, int, int) createStatement | Documents Microsoft"
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
apiname: SQLServerConnection.createStatement (int, int, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 2e4fa385-8f61-4394-8f75-3e839930a57d
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 430174a3400ab3d1138efdaa84c25cba78d90d14
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="createstatement-method-int-int-int"></a>Méthode createStatement (int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet génère [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objets avec le type donné, la concurrence et la mise en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Statement createStatement(int nType,  
                                          int nConcur,  
                                          int nHold)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *resultSetType*  
  
 Le **int** qui représente le résultat de la valeur type.  
  
 *nConcur*  
  
 Le **int** qui représente le résultat de la valeur type d’accès concurrentiel.  
  
 *nHold*  
  
 Le **int** valeur qui représente la fonctionnalité.  
  
## <a name="return-value"></a>Valeur retournée  
 L’objet d’instruction.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode createStatement est spécifiée par la méthode createStatement de l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode createStatement &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
