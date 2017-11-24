---
title: "Next, méthode (SQLServerResultSet) | Documents Microsoft"
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
apiname: SQLServerResultSet.next
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 162902318cbc078ce214568b18e752fdd99559b1
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="next-method-sqlserverresultset"></a>Next, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Déplace le curseur d'une ligne vers le bas depuis sa position actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean next()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si la nouvelle ligne actuelle est valide. **false** s’il n’existe plus aucune ligne à traiter.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode suivante est spécifiée par la méthode suivante dans l’interface java.sql.ResultSet.  
  
 Un curseur du jeu de résultats est positionné initialement avant la première ligne. Le premier appel à la méthode suivante rend la première ligne de la ligne actuelle, le deuxième appel fait de la deuxième ligne de la ligne actuelle et ainsi de suite.  
  
 Si un flux d’entrée est ouvert pour la ligne actuelle, un appel à la méthode suivante ferme implicitement. Une chaîne d’avertissement pour le [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet est supprimé lorsqu’une nouvelle ligne est lue.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
