---
title: "getResultSetHoldability (méthode) (SQLServerStatement) | Documents Microsoft"
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
apiname: SQLServerStatement.getResultSetHoldability
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 053549ee-2018-47ab-9538-789dac2b150a
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b9f9051512f95da78c15a4f36aa3427e247789c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getresultsetholdability-method-sqlserverstatement"></a>getResultSetHoldability (méthode) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le jeu de résultats mise en attente pour [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objets générés par ce [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getResultSetHoldability()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique le jeu de résultats mise en attente.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getResultSetHoldability est spécifiée par la méthode getResultSetHoldability dans l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
