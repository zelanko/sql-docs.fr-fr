---
title: "setTransactionIsolation (méthode) (SQLServerConnection) | Documents Microsoft"
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
- SQLServerConnection.setTransactionIsolation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6a8fa4d3-5237-40f8-8a02-b40a3d7a1131
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b91e33388706cabe7436259193f9b2c0bb446b25
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="settransactionisolation-method-sqlserverconnection"></a>setTransactionIsolation (méthode) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tente de modifier le niveau d’isolation de transaction pour ce [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) objet à celui indiqué.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setTransactionIsolation(int level)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *niveau*  
  
 Un **int** valeur contenant l’un des niveaux d’isolation suivants :  
  
 TRANSACTION_READ_UNCOMMITTED  
  
 TRANSACTION_READ_COMMITTED  
  
 TRANSACTION_REPEATABLE_READ  
  
 TRANSACTION_SERIALIZABLE  
  
 TRANSACTION_SNAPSHOT = 0x1000  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setTransactionIsolation est spécifiée par la méthode setTransactionIsolation dans l’interface java.sql.Connection.  
  
 Les transactions ne sont pas validées si cette méthode est appelée au milieu d'une transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
