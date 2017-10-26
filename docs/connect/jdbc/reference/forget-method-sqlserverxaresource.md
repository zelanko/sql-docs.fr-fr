---
title: "Méthode forget (SQLServerXAResource) | Documents Microsoft"
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
- SQLServerXAResource.forget
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6d83138d-aa45-4d94-9da6-fdfe7ed28edc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a2ca200e555b23d6d8674783f5742f9f02bd1883
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="forget-method-sqlserverxaresource"></a>Méthode forget (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique au gestionnaire de ressources de ne pas tenir compte d'une branche de transaction terminée de manière heuristique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void forget(javax.transaction.xa.Xid xid)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *XID*  
  
 Un objet Xid.  
  
## <a name="exceptions"></a>Exceptions  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Notes  
 Cette méthode oublier est spécifiée par la méthode oublier dans l’interface javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Membres de SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  

