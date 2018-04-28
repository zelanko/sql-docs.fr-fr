---
title: Méthode getSQLStateType (SQLServerDatabaseMetaData) | Documents Microsoft
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
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e9090d0632c82a811d0c03fdc98dae44c0a732db
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getsqlstatetype-method-sqlserverdatabasemetadata"></a>Méthode getSQLStateType (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si le SQLSTATE retourné par la méthode SQLException.getSQLState est X/Open (maintenant appelé Open Group), SQL CLI, SQL99 (JDBC 3.0) ou SQL:2003 (JDBC 4.0).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getSQLStateType()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique le type de SQLSTATE, qui peut être une des valeurs suivantes :  
  
-   Pour Java Runtime Environment version 5.0 : si le **xopenStates** a la valeur de propriété de connexion **true**, cette méthode retourne DatabaseMetaData.sqlStateXOpen. Dans le cas contraire, DatabaseMetaData.sqlStateSQL99.  
  
-   Pour Java Runtime Environment version 6.0 : si le **xopenStates** a la valeur de propriété de connexion **true**, cette méthode retourne DatabaseMetaData.sqlStateXOpen. Dans le cas contraire, DatabaseMetaData.sqlStateSQL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSQLStateType est spécifiée par la méthode getSQLStateType dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
