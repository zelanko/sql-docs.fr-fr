---
title: Méthode addConnectionEventListener (SQLServerPooledConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPooledConnection.addConnectionEventListener
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 142830a8-8d4e-48ca-911d-85bf195ca4fe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fbd278bfa95d0697d7435ccac132a60112b32d2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799607"
---
# <a name="addconnectioneventlistener-method-sqlserverpooledconnection"></a>Méthode addConnectionEventListener (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inscrit le détecteur d’événements donné afin qu’il soit informé lorsqu’un événement se produit sur cet objet [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void addConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *listener*  
  
 Un objet ConnectionEventListener.  
  
## <a name="remarks"></a>Notes   
 Cette méthode addConnectionEventListener est spécifiée par la méthode addConnectionEventListener dans l’interface javax.sql.PooledConnection.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerPooledConnection, méthodes](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection, membres](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection, classe](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
