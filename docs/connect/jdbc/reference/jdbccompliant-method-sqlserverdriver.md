---
title: "Méthode jdbcCompliant (SQLServerDriver) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b56890ad7b3c88388eae12de798e633108aca76a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="jdbccompliant-method-sqlserverdriver"></a>Méthode jdbcCompliant (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Vérifie que le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] est conforme à la spécification JDBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean jdbcCompliant()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si le pilote JDBC répond à la configuration minimale requise. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Cette méthode jdbcCompliant est spécifiée par la méthode jdbcCompliant dans l’interface java.sql.Driver.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [Membres de SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver, classe](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  

