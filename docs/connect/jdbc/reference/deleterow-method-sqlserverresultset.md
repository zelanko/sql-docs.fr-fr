---
title: "deleteRow (méthode) (SQLServerResultSet) | Documents Microsoft"
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
- SQLServerResultSet.deleteRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3759d1d938d45bd952fa589ba47ac7c2d97dcefe
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="deleterow-method-sqlserverresultset"></a>deleteRow (méthode) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Supprime la ligne actuelle à partir de ce[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet et à partir de la base de données sous-jacente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void deleteRow()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode deleteRow est spécifiée par la méthode deleteRow dans l’interface java.sql.ResultSet.  
  
 Cette méthode ne peut pas être appelée lorsque le curseur se trouve sur la ligne d'insertion.  
  
 Si vous utilisez des curseurs de jeu de clés, cette méthode fait apparaître un vide dans le jeu de résultats. Vous pouvez tester ce vide à l’aide de la [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md) (méthode). Les numéros des lignes dans le jeu de résultats ne changent pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
