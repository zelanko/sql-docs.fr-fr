---
title: "Méthode getColumnClassName (SQLServerResultSetMetaData) | Documents Microsoft"
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
- SQLServerResultSetMetaData.getColumnClassName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2c118790-5dd2-4b10-93b6-7f065ee324ce
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 77e6a0fb3081376d34bdbc863b623b7ceb32c6b6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getcolumnclassname-method-sqlserverresultsetmetadata"></a>Méthode getColumnClassName (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nom qualifié complet de la classe Java dont les instances sont créées si la [getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md) méthode de la [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) classe est appelé pour extraire une valeur de la colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getColumnClassName(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *colonne*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui contient le nom qualifié complet de la classe.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumnClassName est spécifiée par la méthode getColumnClassName dans l’interface java.sql.ResultSetMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Membres de SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  

