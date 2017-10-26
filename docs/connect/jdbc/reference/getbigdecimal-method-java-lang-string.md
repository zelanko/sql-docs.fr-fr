---
title: "Méthode getBigDecimal (java.lang.String) | Documents Microsoft"
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
- SQLServerCallableStatement.getBigDecimal (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d0b29b48-9663-4de4-9fc2-82bc30e44aed
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 815ed2b2460a4b492868074f5e11e607f0effe70
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getbigdecimal-method-javalangstring"></a>Méthode getBigDecimal (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant que java.math.BigDecimal avec une précision totale en fonction du nom du paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.math.BigDecimal getBigDecimal(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 A **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet BigDecimal.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getBigDecimal est spécifiée par la méthode getBigDecimal dans l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getBigDecimal &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

