---
title: getdiscardedserverpreparedstatementcount, méthode (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getDiscardedServerPreparedStatementCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2910453562cf78c4b88140de15885d4ddca5fe3a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66776864"
---
# <a name="getdiscardedserverpreparedstatementcount-method-sqlserverconnection"></a>getDiscardedServerPreparedStatementCount, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Retourne le nombre d’actuellement en attente préparée instruction ces actions.

## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getDiscardedServerPreparedStatementCount()  
```  

## <a name="return-value"></a>Valeur retournée
 Un **int** qui contient le nombre d’instruction préparée en suspens ces actions.

## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible à partir de la version du pilote JDBC 6.4 et ultérieur.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
