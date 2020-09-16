---
description: Méthode getXAResource (SQLServerXAConnection)
title: Méthode getXAResource (SQLServerXAConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAConnection.getXAResource
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1d2828f-fd20-44b0-b796-dc70f77c5b03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5a523a1a1b731288632c969baee1170408734a81
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433701"
---
# <a name="getxaresource-method-sqlserverxaconnection"></a>Méthode getXAResource (SQLServerXAConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère un objet [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) qui sera utilisé par le gestionnaire de transactions pour gérer la participation de cet objet [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) dans une transaction distribuée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public javax.transaction.xa.XAResource getXAResource()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet XAResource.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode getXAResource est spécifiée par la méthode getXAResource de l'interface javax.sql.XAConnection.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAConnection, méthodes](../../../connect/jdbc/reference/sqlserverxaconnection-methods.md)   
 [SQLServerXAConnection, membres](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [SQLServerXAConnection, classe](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
