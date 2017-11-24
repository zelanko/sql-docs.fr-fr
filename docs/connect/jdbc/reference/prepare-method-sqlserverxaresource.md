---
title: "Méthode Prepare (SQLServerXAResource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerXAResource.prepare
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: f800c966-3fae-41b3-963a-464988f80da3
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3abe6f5f7b415e0fbae0950929acd7ff3318bdbb
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="prepare-method-sqlserverxaresource"></a>Méthode prepare (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Demande que le Gestionnaire de ressources se préparer à une validation de la transaction spécifiée par l’objet Xid donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int prepare(javax.transaction.xa.Xid xid)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *XID*  
  
 Un objet Xid.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Notes  
 Cette méthode de préparation est spécifiée par la méthode de préparation de l’interface javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Membres de SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
