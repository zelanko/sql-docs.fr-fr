---
title: Méthode jdbcCompliant (SQLServerDriver) | Documents Microsoft
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
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf5dc875f5f02ffd8e14ae00c738e71797c2b502
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
  
