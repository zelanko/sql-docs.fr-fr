---
title: prepareStatement (méthode) (java.lang.String, int, int, int) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b78d2192-f315-4c45-9051-c77059e2c3f4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b5bb32a78809ae6abac9af2decfff9002c9c3f1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="preparestatement-method-javalangstring-int-int-int"></a>Méthode prepareStatement (java.lang.String, int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) objet génère [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objets avec le type donné, la concurrence et la mise en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sql,  
                                                   int nType,  
                                                   int nConcur,  
                                                   int nHold)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 A **chaîne** contenant une instruction SQL.  
  
 *%nLes*  
  
 Un **int** qui indique le type de jeu de résultats.  
  
 *nConcur*  
  
 Un **int** qui indique le jeu de résultats type d’accès concurrentiel.  
  
 *nHold*  
  
 Un **int** qui indique le jeu de résultats mise en attente.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet PreparedStatement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode prepareStatement est spécifiée par la méthode prepareStatement dans l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode prepareStatement &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
