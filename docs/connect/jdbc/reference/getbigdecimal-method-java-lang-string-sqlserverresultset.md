---
title: "Méthode getBigDecimal (java.lang.String) (SQLServerResultSet) | Documents Microsoft"
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
- SQLServerResultSet.getBigDecimal (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b0ded929-d5f5-4573-bf75-ce5bd32328a5
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 33ea6d61fd5abc2a85a6b430b7c28dc0117cfbb2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getbigdecimal-method-javalangstring-sqlserverresultset"></a>Méthode getBigDecimal (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du nom de colonne désigné dans la ligne actuelle de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet en tant que Java .Math.BigDecimal avec une précision totale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.math.BigDecimal getBigDecimal(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnName*  
  
 A **chaîne** qui contient le nom de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet BigDecimal.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getBigDecimal est spécifiée par la méthode getBigDecimal dans l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getBigDecimal &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

