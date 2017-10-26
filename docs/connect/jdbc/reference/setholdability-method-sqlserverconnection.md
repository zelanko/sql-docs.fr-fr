---
title: "setHoldability (méthode) (SQLServerConnection) | Documents Microsoft"
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
- SQLServerConnection.setHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 552eebd0-4c38-43f0-961f-35244f99109b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cfc1f5eb9b3c6368cfe0dd659146bcfa7353bf89
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setholdability-method-sqlserverconnection"></a>setHoldability (méthode) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Modifie la fonctionnalité des [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objets qui sont créés à l’aide de ce [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) objet à la fonctionnalité donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setHoldability(int nNewHold)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nNewHold*  
  
 Un **int** valeur contenant l’un des niveaux de fonctionnalité suivants :  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setHoldability est spécifiée par la méthode setHoldability dans l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

