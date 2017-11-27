---
title: "Méthode getGeneratedKeys (SQLServerStatement) | Documents Microsoft"
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
apiname: SQLServerStatement.getGeneratedKeys
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: a3325950-0e81-4ae8-aa0c-e1f6d371adcd
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 582cbc2d2dd5e68240bfa53ba3c15da8e293203a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getgeneratedkeys-method-sqlserverstatement"></a>Méthode getGeneratedKeys (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère toute clé générée automatiquement qui est créés à la suite de l’exécution de ce [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.sql.ResultSet getGeneratedKeys()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de jeu de résultats.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getGeneratedKeys est spécifiée par la méthode getGeneratedKeys dans l’interface java.sql.Statement.  
  
 Pour plus d’informations sur l’utilisation de cette méthode, consultez [utilisant les clés générées automatiquement](../../../connect/jdbc/using-auto-generated-keys.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
