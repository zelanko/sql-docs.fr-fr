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
ms.topic: conceptual
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
ms.openlocfilehash: 5cc11a28ca0b63f87b42b20b00a297eb217830c7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
  
  
