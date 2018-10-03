---
title: Méthode getSQLStateType (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4a01e2bb8ef76af91c4dede71ae7457351d430b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733197"
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
  
-   Pour Java Runtime Environment version 5.0 : si le **xopenStates** a la valeur de propriété de connexion **true**, cette méthode retourne DatabaseMetaData.sqlStateXOpen. Sinon, DatabaseMetaData.sqlStateSQL99.  
  
-   Pour Java Runtime Environment version 6.0 : si le **xopenStates** a la valeur de propriété de connexion **true**, cette méthode retourne DatabaseMetaData.sqlStateXOpen. Sinon, DatabaseMetaData.sqlStateSQL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getSQLStateType est spécifiée par la méthode getSQLStateType dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
