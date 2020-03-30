---
title: Méthode setTransactionIsolation (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setTransactionIsolation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6a8fa4d3-5237-40f8-8a02-b40a3d7a1131
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e7e803e60568030eb105fa52a15bc2c2bc4b3e8d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67972291"
---
# <a name="settransactionisolation-method-sqlserverconnection"></a>setTransactionIsolation, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tente de remplacer le niveau d’isolation de la transaction de cet objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) par le niveau donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setTransactionIsolation(int level)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *level*  
  
 Valeur **int** contenant l’un des niveaux d’isolation suivants :  
  
 TRANSACTION_READ_UNCOMMITTED  
  
 TRANSACTION_READ_COMMITTED  
  
 TRANSACTION_REPEATABLE_READ  
  
 TRANSACTION_SERIALIZABLE  
  
 TRANSACTION_SNAPSHOT = 0x1000  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setTransactionIsolation est spécifiée par la méthode setTransactionIsolation de l’interface java.sql.Connection.  
  
 Les transactions ne sont pas validées si cette méthode est appelée au milieu d'une transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
