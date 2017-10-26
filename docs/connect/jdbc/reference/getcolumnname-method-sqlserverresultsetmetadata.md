---
title: "Méthode getColumnName (SQLServerResultSetMetaData) | Documents Microsoft"
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
- SQLServerResultSetMetaData.getColumnName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0330ca1d-5e24-4ce3-9d2a-b931f20a0fcf
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a27af3fe868fbbe62d6587d8b3f2183e39845fd6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getcolumnname-method-sqlserverresultsetmetadata"></a>Méthode getColumnName (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtient le nom de la colonne désignée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getColumnName(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *colonne*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui contient le nom de colonne.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumnName est spécifiée par la méthode getColumnName dans l’interface java.sql.ResultSetMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Membres de SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  

