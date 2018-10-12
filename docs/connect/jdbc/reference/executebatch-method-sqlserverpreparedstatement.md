---
title: executeBatch, méthode (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8418167e-cbd2-464d-b118-73cdd76080ed
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a6fac19260ccb09e22e311743ac753937e265dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647607"
---
# <a name="executebatch-method-sqlserverpreparedstatement"></a>Méthode executeBatch (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Envoie un lot de commandes à exécuter à la base de données. En cas d'exécution correcte de toutes les commandes, un tableau des nombres de mises à jour est retourné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int[] executeBatch()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Tableau d'entiers qui contient les nombres de mises à jour.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
 java.sql.BatchUpdateException  
  
## <a name="remarks"></a>Notes   
 Cette méthode executeBatch est spécifiée par la méthode executeBatch dans l’interface java.sql.Statement.  
    
 Cette méthode remplace [SQLServerStatement.executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md).  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
