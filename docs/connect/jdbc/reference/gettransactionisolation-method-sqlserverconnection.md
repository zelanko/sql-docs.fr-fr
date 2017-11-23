---
title: "getTransactionIsolation (méthode) (SQLServerConnection) | Documents Microsoft"
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
apiname: SQLServerConnection.getTransactionIsolation
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 179772e9-6572-4ce5-83c5-ab2b196cee67
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3734e06218c1ff7fab9edf486a60b82a44330586
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="gettransactionisolation-method-sqlserverconnection"></a>getTransactionIsolation (méthode) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le niveau d’isolation de transaction actuel de ce [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getTransactionIsolation()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** valeur contenant l’un des niveaux d’isolation suivants :  
  
 TRANSACTION_NONE  
  
 TRANSACTION_READ_UNCOMMITTED  
  
 TRANSACTION_READ_COMMITTED  
  
 TRANSACTION_REPEATABLE_READ  
  
 TRANSACTION_SERIALIZABLE  
  
 TRANSACTION_SNAPSHOT = 0x1000  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTransactionIsolation est spécifiée par la méthode getTransactionIsolation dans l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
