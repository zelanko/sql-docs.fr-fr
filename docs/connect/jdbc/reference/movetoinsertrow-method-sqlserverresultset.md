---
title: "moveToInsertRow (méthode) (SQLServerResultSet) | Documents Microsoft"
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
- SQLServerResultSet.moveToInsertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3c54bfe-d5b7-4f6e-ae6c-3e8954e5b1c9
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 396367249ad1b786064d6fc5685e505590bbc4af
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="movetoinsertrow-method-sqlserverresultset"></a>moveToInsertRow (méthode) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Déplace le curseur vers la ligne d'insertion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void moveToInsertRow()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode moveToInsertRow est spécifiée par la méthode moveToInsertRow dans l’interface java.sql.ResultSet.  
  
 La position actuelle du curseur est mémorisée lorsque le curseur est placé sur la ligne d'insertion. La ligne d'insertion est une ligne spéciale associée à un jeu de résultats pouvant être mis à jour. Elle constitue essentiellement un tampon dans lequel une nouvelle ligne peut être construite en appelant les méthodes updater avant d'ajouter la ligne au jeu de résultats.  
  
 Seuls les updater, getter et [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) méthodes peuvent être appelées lorsque le curseur se trouve sur la ligne d’insertion. Toutes les colonnes dans un jeu de résultats doivent être une valeur chaque fois que cette méthode est appelée et avant d’appeler insertRow. Une méthode updater doit être appelée pour qu'une méthode getter puisse être elle-même appelée sur une valeur de colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

