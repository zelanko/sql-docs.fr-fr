---
title: "Méthode getXAResource (SQLServerXAConnection) | Documents Microsoft"
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
- SQLServerXAConnection.getXAResource
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1d2828f-fd20-44b0-b796-dc70f77c5b03
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 78999ece74ad80f7d4ce107484d225cc1ab6f4f6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getxaresource-method-sqlserverxaconnection"></a>Méthode getXAResource (SQLServerXAConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère un [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) de l’objet que le Gestionnaire de transactions utilisera pour gérer cela [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) la participation de l’objet dans une transaction distribuée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public javax.transaction.xa.XAResource getXAResource()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet XAResource.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode getXAResource est spécifiée par la méthode getXAResource dans l’interface javax.sql.XAConnection.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-methods.md)   
 [Membres de SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [SQLServerXAConnection, classe](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
