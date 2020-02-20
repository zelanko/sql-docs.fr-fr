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
ms.openlocfilehash: e1377e29329f43b9ea982f168e394537295ec889
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955960"
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
  
 Objet ConnectionEventListener.  
  
## <a name="remarks"></a>Notes   
 Cette méthode addConnectionEventListener est spécifiée par la méthode addConnectionEventListener de l’interface javax.sql.PooledConnection.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerPooledConnection, méthodes](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection, membres](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection, classe](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
