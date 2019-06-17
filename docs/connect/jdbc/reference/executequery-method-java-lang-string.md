---
title: executeQuery, méthode (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3f881493288c385cb490f9d04b22acce03e19f29
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802310"
---
# <a name="executequery-method-javalangstring"></a>Méthode executeQuery (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Exécute l’instruction SQL donnée et retourne un seul objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 Un **chaîne** qui contient une instruction SQL.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet SQLServerResultSet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode executeQuery est spécifiée par la méthode executeQuery dans l’interface java.sql.Statement.  
  
 Cette méthode remplace la méthode [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) qui se trouve dans la classe [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
 L’appel de cette méthode entraîne une exception, car l’instruction SQL de l’objet SQLServerPreparedStatement est spécifiée lors de la création de l’objet.  
  
 Une exception [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) est levée si l’instruction SQL donnée produit autre chose qu’un objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) unique.  
  
## <a name="see-also"></a>Voir aussi  
 [executeQuery, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
