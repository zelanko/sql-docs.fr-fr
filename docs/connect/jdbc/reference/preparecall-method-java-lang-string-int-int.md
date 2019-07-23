---
title: prepareCall, méthode (java.lang.String, int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareCall (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 04d36a25-7f95-4675-9690-4462671b3d67
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7b51cbe470169459469959448208b3aa53b18cce
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976255"
---
# <a name="preparecall-method-javalangstring-int-int"></a>Méthode prepareCall (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un objet [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) qui génère des objets [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) avec le type et la concurrence donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql,  
                                              int resultSetType,  
                                              int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 **String** contenant une instruction SQL.  
  
 *resultSetType*  
  
 **Entier** qui indique le type de jeu de résultats.  
  
 *resultSetConcurrency*  
  
 **Entier** qui indique le type de concurrence du jeu de résultats.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet CallableStatement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode prepareCall est spécifiée par la méthode prepareCall dans l’interface java. Sql. Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [prepareCall, méthode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
