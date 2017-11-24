---
title: "getMaxRows (méthode) (SQLServerStatement) | Documents Microsoft"
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
apiname: SQLServerStatement.getMaxRows
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 6aece4e5-027d-434e-a8cf-a67c0484f189
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8211894887356f993067bc214e101f171f1d490e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getmaxrows-method-sqlserverstatement"></a>getMaxRows (méthode) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal de lignes qui une [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet qui est généré par ce [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet peut contenir.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getMaxRows()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique le nombre maximal de lignes, ou 0 s’il n’existe aucune limite.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMaxRows est spécifiée par la méthode getMaxRows dans l’interface java.sql.Statement.  
  
 Cette méthode getMaxRows retourne toujours 0 pour les curseurs dynamiques permettant les défilements.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
