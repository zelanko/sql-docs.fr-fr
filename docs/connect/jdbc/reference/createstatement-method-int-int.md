---
title: Méthode createStatement (int, int) | Documents Microsoft
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
- SQLServerConnection.createStatement (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 90dbf639-c3d8-4519-9300-5447c79aec17
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7aaf58f311d4b3ebcd59cfd86aa07bc80ca1a2c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="createstatement-method-int-int"></a>Méthode createStatement (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet génère [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objets avec le type donné et la concurrence.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Statement createStatement(int resultSetType,  
                                          int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *resultSetType*  
  
 Le **int** valeur représentant le type de jeu de résultats.  
  
 *resultSetConcurrency*  
  
 Le **int** valeur représentant le type d’accès concurrentiel du jeu de résultats.  
  
## <a name="return-value"></a>Valeur retournée  
 L’objet d’instruction.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode createStatement est spécifiée par la méthode createStatement de l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode createStatement &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
