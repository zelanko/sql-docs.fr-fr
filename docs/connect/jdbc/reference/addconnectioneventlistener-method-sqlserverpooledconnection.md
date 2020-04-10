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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3481ae6f7a6c257c3fd438b4166339cf9507f136
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922974"
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
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPooledConnection, méthodes](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection, membres](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection, classe](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
