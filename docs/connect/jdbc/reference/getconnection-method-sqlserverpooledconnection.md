---
title: Méthode getConnection (SQLServerPooledConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPooledConnection.getConnection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 05bdb61f-26e8-480f-a1c1-1e46a8ed4b70
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aad1cac0f8d627350ad3a4eab5730509148e8ffb
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923365"
---
# <a name="getconnection-method-sqlserverpooledconnection"></a>Méthode getConnection (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un descripteur d’objet pour la connexion physique représentée par cet objet [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Connection getConnection()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet Connection.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode getConnection est spécifiée par la méthode getConnection de l’interface javax.sql.PooledConnection.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPooledConnection, méthodes](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection, membres](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection, classe](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
