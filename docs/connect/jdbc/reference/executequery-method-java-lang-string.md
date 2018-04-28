---
title: Méthode executeQuery (java.lang.String) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 492cda13e6481a31915b85940d78847e3782205f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="executequery-method-javalangstring"></a>Méthode executeQuery (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Exécute l’instruction SQL fournie et retourne un seul [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 A **chaîne** qui contient une instruction SQL.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet SQLServerResultSet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode executeQuery est spécifiée par la méthode executeQuery dans l’interface java.sql.Statement.  
  
 Cette méthode remplace la [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) méthode qui se trouve dans le [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) classe.  
  
 Appel de cette méthode entraîne une exception, car l’instruction SQL pour l’objet SQLServerPreparedStatement est spécifiée lorsque l’objet est créé.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) est levée si l’instruction SQL donnée produit autre chose qu’un seul [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode executeQuery &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [Membres de SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
