---
title: Close (méthode) (SQLServerPreparedStatement) | Documents Microsoft
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
- SQLServerPreparedStatement.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 36db9ff7-5819-4827-9803-4a81c99069b3
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70fea106095de33b3851ad588688257fd8a5b60c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="close-method-sqlserverpreparedstatement"></a>Close (méthode) (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Libère les ressources JDBC de cet objet d’instruction immédiatement au lieu de patienter jusqu'à leur libération automatique et de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode de fermeture est spécifiée par la méthode de fermeture dans l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
