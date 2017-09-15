---
title: "getResultSetConcurrency (méthode) (SQLServerStatement) | Documents Microsoft"
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
- SQLServerStatement.getResultSetConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 47ef6547-5ec7-4cf5-a4d4-e34cbeec72eb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 461001d8c584503b428414355eed14fc65e58791
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getresultsetconcurrency-method-sqlserverstatement"></a>getResultSetConcurrency (méthode) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le jeu de résultats d’accès concurrentiel pour [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objets générés par ce [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getResultSetConcurrency()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique le jeu de résultats type d’accès concurrentiel.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getResultSetConcurrency est spécifiée par la méthode getResultSetConcurrency dans l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
